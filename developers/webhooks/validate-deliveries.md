# Validate Deliveries

This guide explains how to validate Clearout **webhook deliveries using HMAC signature** verification. Validating webhook requests properly guarantees their authenticity and prevents your application from receiving malicious requests.

### Why Validate Webhooks&#x20;

Webhook validation is crucial for security and includes protection against:

* **Replay Attacks** - Timestamps prevent old requests from being replayed
* **Request Tampering** - HMAC signatures ensure data integrity
* **Unauthorized Requests** - Only requests with valid signatures are processed
* **Data Spoofing** - Verification confirms requests originate from Clearout

> **Important**
>
> Always validate webhook signatures in production. Never process webhook data without proper verification, as this could lead to security vulnerabilities and data corruption.

### Signature Format&#x20;

Clearout sends webhook signatures in the `x-co-webhook-signature` header with the following format:

```
t=,v1=
```

#### Signature Components <a href="#signature-components" id="signature-components"></a>

* **t** - Unix timestamp (UTC) when the webhook was created
* **v1** - HMAC-SHA256 signature of the payload

#### How Signatures Are Generated <a href="#signature-generation" id="signature-generation"></a>

Clearout generates signatures using the following process:

* Create a string by concatenating the timestamp and raw JSON payload: `timestamp.payload`
* Generate HMAC-SHA256 hash using your webhook secret token
* Encode the hash as a hexadecimal string
* Include both timestamp and signature in the header

### General Instructions for Any Language&#x20;

When implementing webhook verification in any programming language, follow these core steps:

{% stepper %}
{% step %}
**Parse Signature Header**

Extract the timestamp and signature from the `x-co-webhook-signature` header:

```
Header format: t=,v1=
Example: t=1691234567,v1=abc123def456...
```
{% endstep %}

{% step %}
**Construct Data String**

Create the data string for HMAC calculation using this exact format:

```
data = timestamp + "." + raw_webhook_body
```

> **Critical: Use Raw Body**
>
> Always use the raw request body as received, before any parsing or modifications:
>
> * **Before JSON parsing** - Use the raw string before converting to JSON objects
> * **Before any processing** - Don't modify, trim, or reformat the body
> * **Exact match required** - The body must match exactly what was sent by Clearout
> * **Preserve formatting** - Maintain original whitespace, indentation, and field ordering
{% endstep %}

{% step %}
**Calculate HMAC**

Generate HMAC SHA256 signature using your webhook secret:

```
expected_signature = HMAC_SHA256(data_string, webhook_secret)
```
{% endstep %}

{% step %}
**Verify Signature**

Compare signatures using constant-time comparison to prevent timing attacks:

```
if (constant_time_compare(expected_signature, received_signature)) {
    // Signature is valid
}
```
{% endstep %}

{% step %}
**Validate Timestamp (Optional)**

Check that the timestamp is recent to prevent replay attacks (optional but recommended):

```
current_time = get_current_unix_timestamp()
age = current_time - webhook_timestamp

if (age > 120) { // >2 minutes old (recommended)
    // Reject webhook
}
```

> **Recommended Time Window**
>
> We recommend validating timestamps within a 2-minute window, but you can choose any grace period between 2-5 minutes based on your security requirements and system performance needs. This validation is optional but helps prevent replay attacks.
{% endstep %}

{% step %}
**Return Response**

Always return HTTP 200 status for successful webhook processing:

```
HTTP/1.1 200 OK
Content-Type: application/json

{"status": "success"}
```

> **Important: HTTP Status Codes**
>
> Your webhook endpoint must return HTTP 200 for successful processing. Any other status code will cause Clearout to retry the webhook delivery according to the retry schedule.
{% endstep %}
{% endstepper %}

### **JavaScript Example**&#x20;

{% code expandable="true" %}
```javascript
import express, { Request, Response } from "express";
import crypto from "crypto";

const app = express();
const port = 3000;

// Parse JSON body
app.use(express.json());

// Webhook signature verification function
function verifySignature(secret, body, signatureHeader) {
  try {
    const [tPart, v1Part] = signatureHeader.split(",");

    if (!tPart || !v1Part) {
      console.log("Invalid signature header format");
      return false;
    }

    const timestamp = tPart.split("=")[1];
    const receivedSig = v1Part.split("=")[1];

    if (!timestamp || !receivedSig) {
      console.log("Missing timestamp or signature in header");
      return false;
    }

    const data = `${timestamp}.${JSON.stringify(body)}`;
    const expectedSig = crypto
      .createHmac("sha256", secret)
      .update(data, "utf8")
      .digest("hex");

    if (expectedSig !== receivedSig) {
      console.log("Signature verification failed");
      return false;
    }

    console.log("Signature verified");
    return true;
  } catch (error) {
    console.log("Error verifying signature:", error);
    return false;
  }
}

// Timestamp validation function
function verifyTimestamp(signatureHeader, maxAgeSeconds = 120) {
  try {
    const [tPart] = signatureHeader.split(",");

    if (!tPart) {
      console.log("Invalid signature header format");
      return false;
    }

    const timestamp = tPart.split("=")[1];

    if (!timestamp) {
      console.log("Missing timestamp in header");
      return false;
    }

    const age = Math.floor(Date.now() / 1000) - parseInt(timestamp, 10);

    if (age <  0) {
      console.log("Timestamp is in the future");
      return false;
    }

    if (age > maxAgeSeconds) {
      console.log(`Timestamp too old: ${age} seconds (max: ${maxAgeSeconds})`);
      return false;
    }

    console.log("Timestamp verified");
    return true;
  } catch (error) {
    console.log("Error verifying timestamp:", error);
    return false;
  }
}

// Webhook endpoint
app.post("/webhook", (req, res) => {
  const secret = process.env.WEBHOOK_SECRET || "your-webhook-secret";

  // Extract signature header safely
  const signatureHeader = req.headers["x-co-webhook-signature"];

  if (typeof signatureHeader !== "string") {
    return res
      .status(400)
      .json({ status: "error", message: "Missing signature header" });
  }

  // Verify signature and timestamp
  const isValidSignature = verifySignature(secret, req.body, signatureHeader);
  const isValidTimestamp = verifyTimestamp(signatureHeader, 120); // 2 minutes

  if (!isValidSignature) {
    return res
      .status(401)
      .json({ status: "error", message: "Invalid signature" });
  }

  if (!isValidTimestamp) {
    return res
      .status(401)
      .json({ status: "error", message: "Timestamp too old" });
  }

  // Process webhook data here
  console.log("Webhook processed successfully:", req.body);

  // Return 200 OK to confirm successful processing
  res.json({
    status: "OK",
    message: "Webhook received and processed",
    signatureValid: isValidSignature,
    timestampValid: isValidTimestamp,
  });
});

app.listen(port, () => {
  console.log(`Webhook server listening on port ${port}`);
});
```
{% endcode %}

> **Key Features**
>
> * **Signature Verification** - Validates HMAC-SHA256 signature
> * **Timestamp Validation** - Prevents replay attacks (2-minute window)
> * **Error Handling** - Proper error responses for different failure scenarios
> * **Security** - Uses environment variables for secrets
> * **Logging** - Detailed console output for debugging

### Python Example&#x20;

{% code expandable="true" %}
```python
from flask import Flask, request, jsonify
import hmac
import hashlib
import time
import os

app = Flask(__name__)

def verify_signature(secret, body, signature_header):
    """
    Verify HMAC SHA256 signature using raw body (exact string sent in request).
    Header format: "t=,v1="
    """
    try:
        t_part, v1_part = signature_header.split(",")
        timestamp = t_part.split("=")[1]
        received_sig = v1_part.split("=")[1]

        # Must use raw request body (string), not re-dumped JSON
        data = f"{timestamp}.{body}"
        expected_sig = hmac.new(
            secret.encode("utf-8"),
            data.encode("utf-8"),
            hashlib.sha256,
        ).hexdigest()

        print("body:", body)
        print("secret:", secret)
        print("timestamp:", timestamp)
        print("receivedSig:", received_sig)
        print("expectedSig:", expected_sig)

        # Verify signature match
        if not hmac.compare_digest(expected_sig, received_sig):
            return False
        print("Signature verified")

        return True
    except Exception as e:
        print("Error in verify_signature:", e)
        return False

def verify_timestamp(signature_header):
    """
    Verify timestamp freshness (reject older than 2 minutes).
    """
    try:
        t_part, _ = signature_header.split(",")
        timestamp = int(t_part.split("=")[1])
        print("timestamp:", timestamp)

        age = int(time.time()) - timestamp
        print("age:", age)
        if age > 120:  # >2 minutes old (recommended)
            return False
        print("Timestamp verified")

        return True
    except Exception as e:
        print("Error in verify_timestamp:", e)
        return False

@app.route("/")
def hello_world():
    return "Hello, World!"

@app.route("/webhook", methods=["POST"])
def webhook():
    signature_header = request.headers.get("x-co-webhook-signature")
    print("signatureHeader:", signature_header)
    raw_body = request.get_data(as_text=True)
    secret = os.environ.get("WEBHOOK_SECRET", "your-secret-here")

    if not signature_header:
        return jsonify({"status": "error", "message": "Missing signature header"}), 400

    # Verify signature and timestamp
    is_valid_signature = verify_signature(secret, raw_body, signature_header)
    is_valid_timestamp = verify_timestamp(signature_header)

    print("isValidSignature:", is_valid_signature)
    print("isValidTimestamp:", is_valid_timestamp)

    if not (is_valid_signature and is_valid_timestamp):
        return jsonify({
            "status": "error",
            "message": "Invalid signature or timestamp",
            "signatureValid": is_valid_signature,
            "timestampValid": is_valid_timestamp,
        }), 400

    return jsonify({
        "status": "OK",
        "message": "Webhook received",
        "signatureValid": is_valid_signature,
        "timestampValid": is_valid_timestamp,
    })

if __name__ == "__main__":
    app.run()
```
{% endcode %}

> **Important Notes for Python**
>
> * **Raw Body** - Use `request.get_data(as_text=True)` to get the exact raw body string
> * **JSON Stringify** - The raw body must match exactly what was sent, including whitespace and formatting
> * **HMAC Compare** - Use `hmac.compare_digest()` for secure signature comparison
> * **Error Handling** - Always wrap signature verification in try-catch blocks
> * **Environment Variables** - Store your webhook secret in environment variables for security

### PHP Example&#x20;

{% code expandable="true" %}
```php
<?php
function verify_signature($secret, $body, $signature_header) {
    // Parse the signature header
    $parts = explode(',', $signature_header);
    $timestamp = explode('=', $parts[0])[1];
    $received_sig = explode('=', $parts[1])[1];

    // Create the expected signature
    $data = $timestamp . '.' . json_encode($body);
    $expected_sig = hash_hmac('sha256', $data, $secret);

    // Verify signature match
    if (!hash_equals($expected_sig, $received_sig)) {
        return false;
    }

    return true;
}

function verify_timestamp($signature_header) {
    // Parse the signature header
    $parts = explode(',', $signature_header);
    $timestamp = intval(explode('=', $parts[0])[1]);

    // Verify timestamp freshness (reject older than 2 minutes)
    $age = time() - $timestamp;
    if ($age > 120) { // >2 minutes old (recommended)
        return false;
    }

    return true;
}

// Usage example
$signature = $_SERVER['HTTP_X_CO_WEBHOOK_SIGNATURE'] ?? '';
$secret = $_ENV['WEBHOOK_SECRET'] ?? 'your-secret-here';

if (!$signature) {
    http_response_code(400);
    echo json_encode(['error' => 'Missing signature header']);
    exit;
}

$body = json_decode(file_get_contents('php://input'), true);

if (!verify_signature($secret, $body, $signature) || !verify_timestamp($signature)) {
    http_response_code(400);
    echo json_encode(['error' => 'Invalid signature or timestamp']);
    exit;
}

// Process the webhook
echo json_encode(['status' => 'success']);
?>
```
{% endcode %}

> **Important Notes for PHP**
>
> * **Error Handling** - Always validate signature header exists before processing
> * **Timestamp Validation** - Validates timestamps within 2 minutes (recommended range: 2-5 minutes)
> * **Hash Equals** - Use `hash_equals()` for secure signature comparison
> * **Environment Variables** - Store your webhook secret in environment variables for security

### Security Best Practices&#x20;

#### Secret Management <a href="#secret-management" id="secret-management"></a>

* **Store securely** - Never hardcode secrets in your application code
* **Use environment variables** - Store secrets in environment variables or secure key management systems
* **Rotate regularly** - Update your webhook secret periodically for enhanced security
* **Access control** - Limit access to webhook secrets to authorized personnel only

#### Validation Requirements <a href="#validation-requirements" id="validation-requirements"></a>

* **Always validate** - Never skip signature validation, even in development
* **Check timestamps** - Reject requests older than 5 minutes to prevent replay attacks
* **Use constant-time comparison** - Use secure comparison functions to prevent timing attacks
* **Return appropriate status codes** - Return HTTP 200 for successful processing

#### Timestamp Validation (Optional) <a href="#timestamp-validation" id="timestamp-validation"></a>

Verify that the webhook timestamp is recent to prevent replay attacks:

* **Extract timestamp** from the signature header
* **Calculate age** by comparing with current time
* **Reject old requests** beyond your chosen time window
* **UTC timezone** - All timestamps are in UTC

> **Recommended Time Window**
>
> We recommend validating timestamps within a 2-minute window, but you can choose any grace period between 2-5 minutes based on your security requirements and system performance needs.

### HTTP Status Codes&#x20;

Your webhook endpoint must return appropriate HTTP status codes to indicate successful processing

#### Successful Response <a href="#successful-response" id="successful-response"></a>

* **200 OK** - Webhook processed successfully
* **Response Time** - Must respond within 30 seconds

> **Important**
>
> You **must** return a 200 status code for the webhook delivery to be considered successful. Any other status code (4xx or 5xx) will cause the webhook to be retried after a certain time interval. Only a 200 response will mark the webhook as delivered and stop the retry process.

#### What Triggers Retries <a href="#retry-triggers" id="retry-triggers"></a>

* **4xx Client Errors** - Bad request, unauthorized, forbidden, not found, etc.
* **5xx Server Errors** - Internal server error, service unavailable, etc.
* **Timeout** - No response within 30 seconds
* **Connection Errors** - Network issues, DNS failures, etc.

> **Retry Behavior**
>
> When your endpoint returns a non-200 status code, Clearout will automatically retry the webhook delivery using exponential backoff. The retry schedule depends on your account type. See our [Redelivering Webhooks](https://docs.clearout.io/webhooks/redelivering-webhooks.html) guide for detailed retry timing information.

**Next Steps**

Now that you can validate webhook deliveries, learn how to [test your webhook integration](https://docs.clearout.io/webhooks/test-webhooks.html) and understand [webhook retry behavior](https://docs.clearout.io/webhooks/redelivering-webhooks.html).

---
description: >-
  Endpoints to validate, verify, and discover emails in real time with Clearout
  APIs.
---

# Overview

Clearout provides a set of **RESTful APIs for email validation, advanced verification, and discovery** at scale. You can verify or discover millions of email addresses in real time, with endpoints covering [email verification](/broken/pages/30b386ddb6cfa13c4acec0d77478f79d5f845734), [email finding](/broken/pages/7b22d5e21f842be901bf681c46a3ffd0b7aa734c), reverse lookup, remaining credits, company-to-domain [auto-completion](/broken/pages/3f041f454272f7651c78acba5d3584dc8fc9d9d1), and additional [domain](/broken/pages/05a189a53e42c0160ee82641a1ebec4aea2ab02a) utilities.

## How to Get Started

Getting started with Clearout APIs is quick and straightforward:

{% stepper %}
{% step %}
**Create a free Clearout account**

[Sign up](https://app.clearout.io/register) to receive **100 free credits** and instant access to the API.
{% endstep %}

{% step %}
**Generate your API token**

Find your API token in the Clearout [developer](https://app.clearout.io/developer/api/list) dashboard and use it to authenticate all API requests.
{% endstep %}

{% step %}
**Set service-level settings**

Configure your preferred [settings](https://app.clearout.io/settings/email_verifier), then call the service API endpoint to get the response.
{% endstep %}

{% step %}
**Integrate with your application**

Call APIs from your backend or automation workflows to verify or discover email addresses.
{% endstep %}

{% step %}
**Go live and scale**

Monitor your usage, manage credits, and upgrade your plan as it grows.
{% endstep %}
{% endstepper %}

## API Base URL&#x20;

Clearout APIs use a **base URL** to which all endpoint paths are appended. Since the base URL may vary based on your account host region, API users should check it by logging into the [Clearout app](https://app.clearout.io/developer/reference) and navigating to the **Developer** **→ Reference** tab.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/api-base-url.png" alt="Overview of Developer section showcasing API Base URL "><figcaption></figcaption></figure></div>

## Generating an API Token&#x20;

After signing up and logging in, select the **Developer** tab located at the top-right, and then click on the **API → Create API Token** button. All created tokens are listed under this tab. Use this token as the **Bearer** value in all API requests. Tokens can be reset at any time by clicking the **Reset Token** icon.

* Log in to your Clearout dashboard.
* Navigate to **Developer → API**.
* Click [**Create API Token**](https://app.clearout.io/developer/api/list).
* Use the token as the `Authorization: Bearer <TOKEN>` header in all API requests.<br>

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/api-token-generation.png" alt="Generating an API Token "><figcaption></figcaption></figure></div>

### Example - Using a CURL Request

{% code fullWidth="false" %}
```bash
curl -X GET 'https://api.clearout.io/v2/email_verify/getcredits' \
-H 'Authorization: 3ec7egp34f992762fb5cf6a3479e7e34:d43d2e605e94a8c4s9b72be13b37c19c74b41610c3560484e5c422ccb4fb4074'
```
{% endcode %}

## API Response Objects and Status Codes

### HTTP response codes

These are the HTTP response codes set by Clearout to indicate the success or failure of a request:

<table data-header-hidden><thead><tr><th width="308.6640625"></th><th></th></tr></thead><tbody><tr><td><strong>HTTP Status Code</strong></td><td><strong>Meaning / Description</strong></td></tr><tr><td>200</td><td>Success</td></tr><tr><td>400</td><td>Bad Request</td></tr><tr><td>401</td><td>Unauthorized</td></tr><tr><td>402</td><td>Payment Required</td></tr><tr><td>403</td><td>Forbidden</td></tr><tr><td>415</td><td>Invalid Content Type (must be <code>application/json</code>)</td></tr><tr><td>429</td><td>Rate Limit Exceeded</td></tr><tr><td>500</td><td>Internal Server Error</td></tr><tr><td>503</td><td>Service Unavailable</td></tr><tr><td>524</td><td>Request Timeout</td></tr></tbody></table>

### Clearout error codes

The following Clearout error codes will be included in the error response object:

<table data-header-hidden><thead><tr><th width="163.10546875" align="center"></th><th></th></tr></thead><tbody><tr><td align="center"><strong>Error Code</strong></td><td><strong>Description</strong></td></tr><tr><td align="center">1001</td><td>You’ve reached the maximum number of bulk verify requests. Please wait for the existing request to complete or contact <a href="mailto:us@clearout.io"><strong>us@clearout.io</strong></a></td></tr><tr><td align="center">1002</td><td>You’ve exhausted your credits. Please add additional credits to continue</td></tr><tr><td align="center">1004</td><td>Unable to determine email addresses in the list. Ensure emails are present or explicitly specified in a header row using <strong>Email</strong>, <strong>Emails</strong>, <strong>Email address</strong>, or <strong>Emailaddress</strong></td></tr><tr><td align="center">1007</td><td>List has expired. Contact <a href="mailto:us@clearout.io"><strong>us@clearout.io</strong></a></td></tr><tr><td align="center">1008</td><td>You are not authorized to access this resource</td></tr><tr><td align="center">1017</td><td>You’ve reached the daily verify limit. Try again the next day or contact <a href="mailto:us@clearout.io"><strong>us@clearout.io</strong></a></td></tr><tr><td align="center">1027</td><td>Email address not found</td></tr><tr><td align="center">1028</td><td>Available credits (<strong>AVAILABLE_CREDITS</strong>) are insufficient to verify <strong>NUMBER_OF_EMAILS</strong> emails</td></tr><tr><td align="center">1029</td><td>List is not available</td></tr><tr><td align="center">1030</td><td>API rate limit reached. Retry after <strong>[CURRENT TIMESTAMP + 60 seconds] UTC</strong>, or upgrade your plan / contact <a href="mailto:us@clearout.io"><strong>us@clearout.io</strong></a></td></tr><tr><td align="center">1031</td><td>You have exhausted your credits. </td></tr><tr><td align="center">1032</td><td>You have reached your daily verify limit; please try next day</td></tr><tr><td align="center">1074</td><td>Invalid origin</td></tr></tbody></table>

### Flatten Response Object

By adding <mark style="color:$primary;">response=flat</mark> as a query parameter to any API request, the nested object will be converted into a flat object. This is helpful when your system does not support nested JSON objects.

## Cross-Origin Resource Sharing (CORS)&#x20;

Clearout does not support API requests directly from web browsers or client apps. This means Clearout APIs can be used only from your **server-side application**

## Limits and Quotas

### API Rate Limit

Clearout APIs apply rate limits to ensure platform reliability and fair usage across all plans. Rate-limit details are included in the response headers for every API request.

#### Rate Limit Headers

<table data-header-hidden><thead><tr><th width="227.21484375"></th><th></th></tr></thead><tbody><tr><td>Header</td><td>Description</td></tr><tr><td><code>x-ratelimit-limit</code></td><td>Total number of requests allowed within a 60-second window</td></tr><tr><td><code>x-ratelimit-remaining</code></td><td>Number of requests remaining in the current 60-second window</td></tr><tr><td><code>x-ratelimit-reset</code></td><td>Time remaining (in seconds) before the rate-limit window resets</td></tr></tbody></table>

#### Example Response

```
x-ratelimit-limit: 100
x-ratelimit-remaining: 42
x-ratelimit-reset: 18
```

#### How It Works

* A maximum of **100 requests** can be made per minute
* **42 requests** are still available in the current window
* The quota resets in **18 seconds**

#### When the Limit Is Exceeded

If you exceed the allowed request limit:

* **HTTP Status Code:** `429 Too Many Requests`
* **Clearout Error Code:** `1030`

You should wait until the duration specified `x-ratelimit-reset` elapses before retrying.\
To increase your rate limit, upgrade your plan or contact [support](/broken/pages/0jlzgf9SAHol1YbrmY32).

### Plan-Specific Limits

Clearout offers flexible pay-as-you-go and subscription plans, each with different API limits. Compared to pay-as-you-go plans, subscription plans offer higher limits, which you can increase by selecting an add-on option.&#x20;

Please find below the breakup of plans and API **Request Per Limits (RPM).**&#x20;

<h4 align="center">Monthly/Annual Subscription</h4>

| Credits             | Instant Email Verify (RPM) | Instant Email Finder (RPM) |
| ------------------- | :------------------------: | :------------------------: |
| 3,000               |             25             |             14             |
| 10,000              |             55             |             40             |
| 50,000              |             90             |             55             |
| 100,000             |             135            |             85             |
| 250,000             |             185            |             110            |
| 500,000             |             240            |             140            |
| 1,000,000           |             300            |             190            |
| More than 5,000,000 |             400            |             240            |

<h4 align="center">Pay-As-You-Go </h4>

| Credits              | Instant Email Verify (RPM) | Instant Email Finder (RPM) |
| -------------------- | :------------------------: | :------------------------: |
| 5,000                |             20             |             10             |
| 10,000               |             45             |             30             |
| 100,000              |             70             |             45             |
| 250,000              |             110            |             70             |
| 500,000              |             150            |             90             |
| 1,000,000            |             190            |             110            |
| 5,000,000            |             240            |             150            |
| More than 10,000,000 |             320            |             190            |

For more details on limits and pricing, please refer to the [pricing page](https://clearout.io/pricing/) here.

## Testing&#x20;

To confirm that your integration works as intended without incurring credits, use the test email addresses listed below for all possible email verification results.

<table><thead><tr><th width="340.41015625">Test Email Address</th><th>Description</th></tr></thead><tbody><tr><td>invalid@example.com</td><td>An invalid email address</td></tr><tr><td>valid@example.com</td><td>A valid email address</td></tr><tr><td>catch_all@example.com</td><td>Accept-all or catch-all email address</td></tr><tr><td>unknown@example.com</td><td>An unknown email address</td></tr><tr><td>safe_to_send_yes@example.com</td><td>Safe to send email address</td></tr><tr><td>safe_to_send_no@example.com</td><td>Not a safe to send email address</td></tr><tr><td>safe_to_send_risky@example.com</td><td>Risky email address</td></tr><tr><td>disposable@example.com</td><td>Disposable email address</td></tr><tr><td>role@example.com</td><td>Role- or group-based email address</td></tr><tr><td>free@example.com</td><td>Free email provider address</td></tr><tr><td>gibberish@example.com</td><td>Gibberish email address</td></tr><tr><td>hard_bounce@example.com</td><td>Hard bounce email address</td></tr><tr><td>soft_bounce@example.com</td><td>Soft bounce email address</td></tr><tr><td>suggested_email_address@example.com</td><td>An auto-suggested email address</td></tr><tr><td>syntax_error@example.com</td><td>Syntax error email address</td></tr><tr><td>greylisted@example.com</td><td>Greylisted email address</td></tr><tr><td>spamtrap@example.com</td><td>Spamtrap email address</td></tr><tr><td>blocklist_email_address@example.com</td><td>Found part of blocklist email address</td></tr><tr><td>allowlist_email_address@example.com</td><td>Found part of allowlist email address</td></tr><tr><td>blocklist_domain@example.com</td><td>Found part of blocklist domain</td></tr><tr><td>allowlist_domain@example.com</td><td>Found part of allowlist domain</td></tr><tr><td>domain_not_found@example.com</td><td>The domain does not exist for the email address</td></tr><tr><td>not_a_mailserver@example.com</td><td>Not a mail server email address</td></tr><tr><td>mailbox_not_found@example.com</td><td>Mailbox not found email address</td></tr><tr><td>mailbox_quota_exceeded@example.com</td><td>Mail quota exceeded email address</td></tr><tr><td>dns_query_timeout@example.com</td><td>DNS query timeout email address</td></tr><tr><td>unroutable_mailserver@example.com</td><td>Unroutable mail exchange server email address</td></tr><tr><td>overquota_and_inactive@example.com</td><td>Dormant email address</td></tr><tr><td>receiving_limit_reached@example.com</td><td>Receiving limit exceeded email address</td></tr></tbody></table>

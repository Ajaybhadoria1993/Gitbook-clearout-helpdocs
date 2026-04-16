# Webhook Events & Payloads

This page provides a complete reference for all Clearout webhook events and their payload structures. Each webhook event contains detailed information about the completed operation, allowing you to process the results in real time.

> **Event Timing**
>
> All webhook events are triggered immediately after the service completes.

## Webhook Events Overview&#x20;

<table><thead><tr><th width="333">Event Type</th><th>When Triggered</th></tr></thead><tbody><tr><td><code>email_verifier.instant.completed</code> *</td><td>After instant email verification completes</td></tr><tr><td><code>email_verifier.bulk.completed</code></td><td>After bulk email verification completes</td></tr><tr><td><code>email_finder.instant.completed</code> *</td><td>After email finder operation completes</td></tr><tr><td><code>email_finder.bulk.completed</code></td><td>After bulk email finding completes</td></tr><tr><td><code>form_guard.email_validation.completed</code> *</td><td>After email validation in forms is completed</td></tr></tbody></table>

> Events that may be chargeable on a conditional basis; see our [Pricing Guide ](https://clearout.io/pricing-guide/#billable-service-action) for more details

## Webhook Structure&#x20;

All webhook payloads follow a consistent structure with common fields and service-specific data:

#### Common Fields <a href="#common-fields" id="common-fields"></a>

* **event\_id** - Unique identifier for this webhook delivery
* **event\_type** - The type of event that occurred
* **event\_mode** - Environment mode (live/test)
* **event\_created\_on** - ISO 8601 timestamp when the event was created
* **payload** - Contains the actual event data and results

#### Payload Structure <a href="#payload-structure" id="payload-structure"></a>

The payload object contains:

* **status** - Overall operation status (success/error)
* **data** - Service-specific data and results

## Email Verifier Events&#x20;

#### email\_verifier.instant.completed&#x20;

Triggered when instant email verification is completed.

**Payload Example**

{% code overflow="wrap" expandable="true" %}
```json
{
  "event_id": "68b52198f204df746f72c3ec",
  "event_type": "email_verifier.instant.completed",
  "event_mode": "live",
  "event_created_on": "2025-09-01T04:31:20.445Z",
  "payload": {
    "status": "success",
    "data": {
      "email_address": "sanjay@socialfrontier.com",
      "status": "valid",
      "sub_status": {
        "code": 200,
        "desc": "Success"
      },
      "safe_to_send": "yes",
      "ai_verdict": "Given email address is from Gsuite provider, sending message will be delivered without a bounce",
      "suggested_email_address": "",
      "verified_on": "2025-09-01T04:31:20.042Z",
      "time_taken": 380,
      "disposable": "no",
      "free": "no",
      "role": "no",
      "gibberish": "no",
      "bounce_type": "",
      "detail_info": {
        "account": "sanjay",
        "domain": "socialfrontier.com",
        "mx_record": "aspmx.l.google.com",
        "smtp_provider": "gsuite"
      },
      "profile": null
    }
  }
}
```
{% endcode %}

> **Data Structure**
>
> The payload data structure is identical to the Email Verification API response. Refer to the [Email Verification API documentation](https://docs.clearout.io/email-verifier-api.html) for detailed field descriptions.

#### email\_verifier.bulk.completed&#x20;

Triggered when bulk email verification is completed.

**Payload Example**

```json
{
  "event_id": "68b18464a73994ef5ae36608",
  "event_type": "email_verifier.bulk.completed",
  "event_mode": "live",
  "event_created_on": "2025-08-29T10:43:48.077Z",
  "payload": {
    "status": "success",
    "data": {
      "list_id": "68b1821500b0b980de170e2d",
      "list_name": "clearout_email_verifier_sample_list.csv"
    }
  }
}
```

## Email Finder Events&#x20;

#### email\_finder.instant.completed&#x20;

Triggered when instant email finding is completed.

**Payload Example**

{% code expandable="true" %}
```json
{
  "event_id": "68994705edd8dab364becfe6",
  "event_type": "email_finder.instant.completed",
  "event_mode": "live",
  "event_on": "2025-08-11T01:27:33.597Z",
  "payload": {
    "status": "success",
    "data": {
      "emails": [
        {
          "email_address": "sinha@clearout.io",
          "role": "no",
          "business": "yes"
        }
      ],
      "first_name": "sinha",
      "last_name": "",
      "full_name": "sinha",
      "domain": "clearout.io",
      "confidence_score": 99,
      "_depreciated": {
        "confidence_score": 92
      },
      "total": 1,
      "company": {
        "name": "clearout"
      },
      "found_on": "2025-08-11T01:27:33.564Z",
      "credits_charged": 4
    }
  }
}
```
{% endcode %}

> **Data Structure**
>
> The payload data structure is identical to the Email Finder API response. Refer to the [Email Finder API documentation](https://docs.clearout.io/email-finder-api.html) for detailed field descriptions.

#### email\_finder.bulk.completed&#x20;

Triggered when bulk email finding is completed.

**Payload Example**

```json
{
  "event_id": "68b18464a73994ef5ae36608",
  "event_type": "email_finder.bulk.completed",
  "event_mode": "live",
  "event_created_on": "2025-08-29T10:43:48.077Z",
  "payload": {
    "status": "success",
    "data": {
      "list_id": "68b1821500b0b980de170e2d",
      "list_name": "clearout_email_verifier_sample_list.csv"
    }
  }
}
```

## Form Guard Events&#x20;

#### form\_guard.email\_validation.completed&#x20;

Triggered when email validation in forms is completed.

**Payload Example**

{% code expandable="true" %}
```json
{
  "event_id": "689c16f8759521043ae297e2",
  "event_type": "form_guard.email_validation.completed",
  "event_mode": "live",
  "event_created_on": "2025-08-13T04:39:20.774Z",
  "payload": {
    "status": "success",
    "data": {
      "email_address": "sanjaytest@kintra.com",
      "status": "valid",
      "sub_status": {
        "code": 200,
        "desc": "Success"
      },
      "safe_to_send": "yes",
      "ai_verdict": "Given email address is from Servicehoster provider, sending message will be delivered without a bounce",
      "suggested_email_address": "",
      "verified_on": "2025-08-13T04:39:18.955Z",
      "time_taken": 1795,
      "disposable": "no",
      "free": "no",
      "role": "no",
      "gibberish": "no",
      "bounce_type": "",
      "detail_info": {
        "account": "sanjaytest",
        "domain": "kintra.com",
        "mx_record": "mx02.servicehoster.ch",
        "smtp_provider": "servicehoster"
      },
      "profile": null
    }
  }
}
```
{% endcode %}

> **Data Structure**
>
> The payload data structure is identical to the Email Verification API response. Refer to the [Email Verification API documentation](https://docs.clearout.io/email-verifier-api.html) for detailed field descriptions.

**Next Steps**

Now that you understand the webhook events and payloads, learn how to [validate webhook deliveries](https://docs.clearout.io/webhooks/validate-deliveries.html) for security and [test your webhook integration](https://docs.clearout.io/webhooks/test-webhooks.html).

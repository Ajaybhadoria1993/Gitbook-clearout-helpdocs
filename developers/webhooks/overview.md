---
description: Real-time webhooks for validation results
---

# Webhooks Overview

Clearout Webhooks send **real-time notifications for email validation, email finder, and form guard operations**. Webhooks deliver data to your application immediately instead of polling our APIs. You can build real-time integrations with webhooks to process verification results, update databases, trigger follow-up actions, or notify users without manual intervention.&#x20;

Clearout provides [webhook authentication](validate-deliveries.md) to ensure secure delivery, allowing your application to verify the authenticity of each webhook request before processing the payload. This helps protect your endpoint from spoofed or tampered requests

## Webhook vs API&#x20;

APIs send you data when you request it. With Webhooks, you don't need to make requests - you receive data automatically when it's available.

{% hint style="info" %}
**Example**

If you need to know whether an email finder is complete, using APIs requires you to keep polling every few seconds until the process finishes. However, with webhooks, you can configure a webhook event like `email_finder.instant.completed` to receive notifications automatically when email finder completes.
{% endhint %}

## Use Cases&#x20;

Webhooks can be used for multiple purposes. Here are some common use cases:

<table data-header-hidden><thead><tr><th width="205.541015625"></th><th></th><th></th></tr></thead><tbody><tr><td>Use Case </td><td>Description</td><td>Primary Benefit</td></tr><tr><td><strong>Real-time Notifications</strong></td><td>Receive instant alerts when email validation, discovery, or Form Guard operations are completed.</td><td>Allows you to immediately inform users of results or trigger prompt follow-up actions.</td></tr><tr><td><strong>Automated Workflows</strong></td><td>Automatically sync validation data with your CRM, database, or internal workflow tools.</td><td>Eliminates the need for manual data entry and ensures systems are updated without human intervention.</td></tr><tr><td><strong>Integration Automation</strong></td><td>Connect Clearout services with existing platforms to create seamless automated pipelines.</td><td>Replaces the need for constant API polling, saving server resources and improving efficiency.</td></tr></tbody></table>

## How Webhooks Work&#x20;

When you configure a webhook in Clearout:

* You specify a URL endpoint where you want to receive notifications
* You choose which events to subscribe to (e.g., email validation complete, bulk verification finished)
* When an event occurs, Clearout sends an HTTP POST request with JSON payload to your configured URL
* To validate deliveries via webhooks, your application verifies the webhook authentication details to confirm the request came from Clearout.​
* After verification succeeds, your application processes the webhook data and takes the appropriate action.

{% hint style="info" %}
**Important**

Despite network issues, webhooks ensure you receive results even if your initial API request fails or returned with unknown status

Webhook URLs must be publicly accessible and support HTTPS.
{% endhint %}

{% hint style="info" %}
**Good to know**

Webhook events themselves are not charged. In the event of a request timeout or an unknown status response, you are charged for the service request action that was previously unsuccessful or returned unknown. Refer to [Webhook Events & Payloads](webhook-events-and-payloads.md) for details on specific events, and check our [Pricing Guide ](https://clearout.io/pricing-guide/#billable-service-action) to understand how much is charged for each service action.
{% endhint %}

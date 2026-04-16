# Set up & Edit Webhooks

This guide explains how to set up, configure, and manage webhooks in your Clearout App so you can automatically receive real-time notifications when important events occur, such as email validation completions, email finder results, or form guard triggers. You'll also learn how to select events, secure your webhooks, and test your integration for reliability.

## Accessing Webhooks&#x20;

To access webhook settings in Clearout:

{% stepper %}
{% step %}
Log in to your [Clearout App](https://app.clearout.io/)


{% endstep %}

{% step %}
Navigate to the **Developers** section in the main menu


{% endstep %}

{% step %}
Click on **Webhook** to access webhook management


{% endstep %}
{% endstepper %}

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/webhook-dashboard-main.png" alt="Set up &#x26; Edit Webhooks" width="563"><figcaption></figcaption></figure></div>

## Creating a Webhook&#x20;

To create a new webhook:

{% stepper %}
{% step %}
Click the **Create Webhook** button


{% endstep %}

{% step %}
Fill in the webhook configuration form


{% endstep %}

{% step %}
Select the events you want to subscribe to


{% endstep %}

{% step %}
Save your webhook configuration
{% endstep %}
{% endstepper %}

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/webhook-create-form.png" alt="Creating a Webhook" width="525"><figcaption></figcaption></figure></div>

## Webhook Configuration  <a href="#webhook-configuration" id="webhook-configuration"></a>

When creating or editing a webhook, you'll need to configure the following fields:

#### Basic Fields <a href="#basic-fields" id="basic-fields"></a>

* **Name** - A descriptive name for your webhook
* **Description** - Description of the webhook's purpose (150 character limit)
* **URL** - The HTTPS endpoint where webhook notifications will be sent

#### Custom Headers <a href="#custom-headers" id="custom-headers"></a>

You can add custom headers to your webhook requests:

* Click **Add Header** to add a new header
* Specify the **Key** and **Value** for each header
* Common use cases include authentication headers or custom identifiers

> <mark style="color:$info;">**Header Examples**</mark>
>
> <mark style="color:$info;">You might add headers like</mark> <mark style="color:$info;"></mark><mark style="color:$info;">`Authorization: Bearer your-token`</mark> <mark style="color:$info;"></mark><mark style="color:$info;">or</mark> <mark style="color:$info;"></mark><mark style="color:$info;">`X-Custom-ID: your-identifier`</mark> <mark style="color:$info;"></mark><mark style="color:$info;">for authentication or tracking purposes.</mark>

#### Event Selection <a href="#event-selection" id="event-selection"></a>

Events are organized by service and displayed in a grouped checkbox format. You can view all events or only selected ones using the tabs.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/webhook-event-selection.png" alt="Selecting Webhook Events for Email verification, Email Finding and Form Guard"><figcaption></figcaption></figure></div>

> **Event Selection Tips**
>
> Use the "Select all" checkbox to quickly select all available events, or expand each service section to choose specific events. For detailed information about each event and their payloads, see our [Webhook Events & Payloads](https://docs.clearout.io/webhooks/webhooks-events-payloads.html) page.

## Secret Token  <a href="#secret-token" id="secret-token"></a>

The secret token is used to verify that webhook requests come from Clearout. It's generated at the account level and shared across all webhooks.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/webhook-secret-token.jpg" alt="Generating Secret Token"><figcaption></figcaption></figure></div>

#### Generating Your Secret Token<br>

* In the webhook dashboard, scroll down to the **Secret Token** section
* If this is your first time, click the **Generate Token** button to create your secret token
* **Important:** Copy the generated token immediately, as it will only be visible during generation

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/webhook-secret-token-generated.png" alt="Copying Generated Secret Token" width="563"><figcaption></figcaption></figure></div>

#### Rotating Your Secret Token <a href="#rotating-secret-token" id="rotating-secret-token"></a>

* Click the rotate button (circular arrow icon) next to your current token
* A new token will be generated and displayed
* Copy the new token immediately, as it will only be visible during generation
* Update your webhook endpoint to use the new token
* The dashboard will show when the token was last updated

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/webhook-secret-token-rotate.png" alt="Rotating/Regenerating Secret Token"><figcaption></figcaption></figure></div>

> **Important**
>
> The secret token is only visible during generation or rotation. Make sure to copy it immediately and store it securely. Use it to verify webhook signatures as described in our [Validate Deliveries](https://docs.clearout.io/webhooks/validate-deliveries.html) guide.

## Managing Webhooks <a href="#managing-webhooks" id="managing-webhooks"></a>

Once you've created webhooks, they appear in the "My Webhooks" table, where you can manage them using the action buttons:

<table data-view="cards"><thead><tr><th></th></tr></thead><tbody><tr><td><h4><strong>View Event Logs</strong></h4><p>View detailed delivery history, response codes, and JSON payloads for all webhook events. Shows success/failure status and timestamps.</p></td></tr><tr><td><h4><strong>Test Events</strong></h4><p>Send test payloads to verify your webhook endpoint is working correctly. Select from available event types to simulate real webhook deliveries.</p></td></tr><tr><td><h4><strong>Edit Webhook</strong></h4><p>Modify webhook configuration including name, description, URL, custom headers, and event subscriptions.</p></td></tr><tr><td><h4><strong>Delete Webhook</strong></h4><p>Remove the webhook configuration permanently. You'll be asked to confirm the deletion before it's removed.</p></td></tr></tbody></table>

#### Webhook Table View <a href="#webhook-table-view" id="webhook-table-view"></a>

The webhook dashboard displays your configured webhooks in a table format with the following columns:

* **Name** - Your webhook name with description below
* **URL** - The endpoint URL where webhooks are sent
* **Status** - Toggle switch to enable/disable the webhook
* **Listening To** - Number of events the webhook is subscribed to
* **Actions** - The four action buttons described above

## Testing Webhooks&#x20;

You can test your webhook configuration directly from the dashboard:

* Click the **Test Events** button (paper plane icon) for any webhook
* Select the event type you want to test
* A sample payload will be sent to your webhook URL
* Check your endpoint to verify the payload was received correctly

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/webhook-test-interface.png" alt="Testing Webhook" width="563"><figcaption></figcaption></figure></div>



> **Local Testing**
>
> For local development, use tools like [ngrok](https://ngrok.com/) to expose your local server with HTTPS. This allows you to test webhooks on your development environment.

**Next Steps**

Once your webhook is configured, learn about the [event payloads](https://docs.clearout.io/webhooks/webhooks-events-payloads.html) you'll receive and how to [validate webhook deliveries](https://docs.clearout.io/webhooks/validate-deliveries.html) for security.

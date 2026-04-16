---
description: Automate email verification in workflows
---

# HubSpot Workflows

Use **HubSpot Workflows + Clearout** to automatically verify emails whenever a new contact is created in HubSpot or an existing contact’s email is updated. This keeps your CRM continuously clean without manual checks.​

You can also see this process in action in the video:

{% embed url="https://www.youtube.com/watch?embeds_referring_euri=https://clearout.io/&time_continue=1&v=N5wIux7yJB0" %}

### Why use Clearout in workflows? <a href="#why-use-clearout-in-workflows" id="why-use-clearout-in-workflows"></a>

When contacts come from multiple sources (imports, integrations, forms, manual entry), not all of them pass through form or chat validation. By adding Clearout to your workflows, you can:​

* Enrich contacts with Clearout custom properties such as verification status, safe‑to‑send, role/disposable/gibberish flags, verified time, and more.​
* Improve data quality by filtering out invalid, disposable, role, or gibberish emails.​
* Create precise segments and targeting rules (for example, only send campaigns to contacts marked safe‑to‑send).​
* Personalize outreach based on role accounts vs. individual mailboxes.​
* Reduce manual cleanup and automatically remove bad contacts, saving credits and campaign costs.​

To achieve this, you’ll complete **three main steps**, then test and review field mappings.

{% stepper %}
{% step %}
### Syncing Clearout Standard Fields to Hubspot CRM&#x20;

To begin, please ensure that Clearout's standard properties are present in your HubSpot account.

* Link your HubSpot account with Clearout [here](https://app.clearout.io/integrations/connect-account).​
* Upon successful linking, Clearout creates a **Clearout Information** property group in HubSpot with all Standard Clearout fields as **custom properties**.​
* If you already linked HubSpot earlier and don’t see this group, simply **unlink and re‑link** the HubSpot account from Clearout; the fields will then be synced.​

These properties will later be populated by the workflow’s custom code step.
{% endstep %}

{% step %}
### Creating HubSpot Workflow

Next, create a workflow that will host the Clearout validation logic.

* In HubSpot, go to **Automations → Workflows**.

<p align="center"><img src="../../.gitbook/assets/unknown (6).png" alt="Go to HubSpot Automations to Setup Workflows" data-size="original"></p>

* Click **Create workflow → From scratch**.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/from scratch.png" alt="Create New HubSpot Workflow" width="563"><figcaption></figcaption></figure></div>

* Choose **Contact‑based** and **Trigger manually** to start configuring the workflow.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/trigger manually.png" alt="Select Contact‑based and Trigger manually to start configuring the workflow." width="563"><figcaption></figcaption></figure></div>

* You will adjust the triggers in the next step so the workflow runs whenever a new contact is created, or a contact’s email is updated, Clearout’s Verification when any contact gets added or updated into the CRM

<div align="center" data-with-frame="true"><figure><img src="../../.gitbook/assets/crm.png" alt="Adjust the triggers when a new contact is created" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Set up the workflow <a href="#id-3-set-up-the-workflow" id="id-3-set-up-the-workflow"></a>

#### 3.1 Configure triggers

Make the workflow run on:

* **New contact created**, and
* **Email property changed**.

Steps:

1. Click **Set enrollment triggers** (Start triggers).

<p align="center"><img src="../../.gitbook/assets/image (11).png" alt="Set a Enrollment Triggers"></p>

2. Add the first trigger under **Date events → Record created** (this covers new contacts).​

<figure><img src="../../.gitbook/assets/image (12).png" alt="Add the first trigger under Date events for Record Created" width="563"><figcaption></figcaption></figure>

3.  Add a second trigger under the **OR** section: choose **Date events → Property value changed**.​

    <figure><img src="../../.gitbook/assets/image (13).png" alt="Add the first trigger under Date events for Property Value Changed"><figcaption></figcaption></figure>
4. For this second trigger, select the **Email** property and set **New value → is known**, then click **Save**.​

<figure><img src="../../.gitbook/assets/image (14).png" alt="Set Email as new value &#x22;Unknown&#x22;" width="563"><figcaption></figcaption></figure>

Now the workflow will trigger whenever a contact is created or its email address is updated.

#### 3.2 Add Clearout validation via Custom Code

Add a step that calls Clearout and returns verification output fields

1. Click the **+** icon below the trigger to add an action.
2. Choose **Data Ops → Custom code.**

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/ev nodejs.png" alt="Add custom code under &#x22;Data Ops&#x22;" width="563"><figcaption></figcaption></figure></div>

3. Under **Property to include in code**, select the **Email** property (under Text properties). This makes the contact’s email available inside the Node.js code.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/custom nodejs.png" alt="Select Email property" width="563"><figcaption></figcaption></figure></div>

4. In the code editor, replace the default code with the following (update the token before saving):

{% code lineNumbers="true" fullWidth="false" expandable="true" %}
```javascript
var request = require("request");
exports.main = async (event, callback) => {

  // Get the Email from the Event object
  const email = event.inputFields['email'];

  // Generate the Clearout Email Verifier options Object
  var options = {
    method: 'POST',
    url: 'https://api.clearout.io/v2/email_verify/instant',
    headers: {
      'Content-Type': 'application/json',
      'Authorization': 'REPLACE_WITH_YOUR_SERVER_APP_TOKEN', // Server API Key to be generated
    },
    body: {
      email: email, // Get the email address from the event object.
      timeout: 30000 // The option to define the maximum time that can be used for verifying the status of the given email address.
    },
    json: true
  };

  request(options, function (err, response, body) {
    if (err) throw new Error(err); // Handle errors.


    // If Api Succeeded, proceed to get the interested Fields
    if (body.status === 'success') {
      let { safe_to_send, status, verified_on } = body.data
      callback({
        outputFields: {
          status,
          safe_to_send,
          verified_on
        }
      });
    }
  });
}

```
{% endcode %}

5. Generate a Clearout [API Token](https://app.clearout.io/developer/api/list). Copy and replace `REPLACE_WITH_YOUR_SERVER_APP_TOKEN` with your API token.​
6. Under **Data output**, define the outputs: `status`, `safe_to_send`, and `verified_on` (names must match the code above).

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/variable name must workflow.png" alt="Define Output Properties " width="563"><figcaption></figcaption></figure></div>

7. Use the **Test action** to run the step against a sample contact; if everything is correct, you should see a successful response with these output fields.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/variable name must.png" alt="Successful response with selected output fields"><figcaption></figcaption></figure></div>

8. Save this action. The test call will also appear in your Clearout [**Activities**](https://app.clearout.io/activities) section.&#x20;

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/clearout account activities.png" alt="Check Clearout Activities to confirm successful implementation"><figcaption></figcaption></figure></div>

#### 3.3 Branch and handle invalid vs valid contacts

Now, create branches to handle contacts differently based on Clearout’s result.

<figure><img src="../../.gitbook/assets/image (15).png" alt="Branch to handle Valid and invalid email addresses" width="563"><figcaption></figcaption></figure>

1. Add a new action below the custom code step and choose **Branch → One property or action output**.​
   1.

       <figure><img src="../../.gitbook/assets/image (16).png" alt="Select &#x22;One property or action output&#x22; in custom code"><figcaption></figcaption></figure>
2. For the **Select property**, choose **Action outputs → status** (from the custom code step).​
   1.

       <figure><img src="../../.gitbook/assets/image (17).png" alt="Select Action outputs as Status "><figcaption></figcaption></figure>
3. Create two branches:
   * Branch A: `status` **equals** `invalid`
     *

         <figure><img src="../../.gitbook/assets/image (18).png" alt="Branch out to capture valid and invalid status"><figcaption></figcaption></figure>
   * Branch B: `status` **is not equal to** `invalid`.​
     *

         <figure><img src="../../.gitbook/assets/image (19).png" alt="Branch out to capture valid and invalid status"><figcaption></figcaption></figure>

### Branch A: Delete invalid contacts (optional)

If you want to automatically remove invalid contacts:

1. Under the **status = invalid** branch, add a new action.​
2.  Select **CRM → Delete contact** and save.​



    <figure><img src="../../.gitbook/assets/image (24).png" alt="Delete Invalid Email address After validation" width="563"><figcaption></figcaption></figure>



    <figure><img src="../../.gitbook/assets/image (21).png" alt="workflow to Delete Invalid Email address After validation" width="563"><figcaption></figcaption></figure>

(You can skip this step if you prefer to keep invalid contacts and just mark them.)

### Branch B: Update Clearout fields for valid/other contacts

1. Under the **status is not equal to invalid** branch, add a new action.
2. Select **CRM → Set property value**.​
3. Under **Property to set**, choose one of the Clearout properties from the **Clearout Information** group (for example, **Clearout Verification Status**).​
   1.

       <figure><img src="../../.gitbook/assets/image (22).png" alt="set &#x22;property to set&#x22; as &#x22;Clearout Verification Status&#x22;"><figcaption></figcaption></figure>
4. In **Insert data**, select **Action outputs → status** as the value.​
5. Save the action.​

Repeat this **Set property value** action for other Clearout standard fields you want to update, such as

* Clearout Safe To Send
* Clearout Verified On
* Clearout Reason, etc.​

When finished, your workflow should show:

* Trigger (record created OR email changed) → Custom code (Clearout call) → Branch (status invalid vs not invalid) →
  * Invalid branch: Delete contact (optional)
  *   Valid/other branch: Set Clearout fields on the contact.​



      <figure><img src="../../.gitbook/assets/image (20).png" alt="Trigger to check the setup" width="563"><figcaption></figcaption></figure>

Finally, click **Review and publish the workflow** to activate it.
{% endstep %}

{% step %}
### Test the workflow <a href="#id-4-test-the-workflow" id="id-4-test-the-workflow"></a>

* In HubSpot, manually create a new contact under **CRM → Contacts** with a test email and check if Clearout verification runs.​
* Confirm in Clearout **Activities** or by viewing the contact’s **Clearout Information** properties (for example, Clearout Verification Status, Safe To Send, Verified On) that the data is populated.​
* Edit the email address of an existing contact and verify that the workflow triggers again and updates the Clearout's fields accordingly

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/testing workflow hs clearout.png" alt="Test the workflow" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Clearout ↔ HubSpot standard field mappings <a href="#id-5-clearout--hubspot-standard-field-mappings" id="id-5-clearout--hubspot-standard-field-mappings"></a>

**Property group in HubSpot:** `Clearout Information`.

<table data-header-hidden><thead><tr><th width="217.8140869140625"></th><th width="161.614501953125"></th><th width="129.6397705078125"></th><th></th></tr></thead><tbody><tr><td><strong>HubSpot Property Label</strong></td><td><strong>HubSpot Internal</strong></td><td><strong>Clearout Standard</strong></td><td><strong>Clearout API Response</strong></td></tr><tr><td>Clearout Safe To Send</td><td>co_safe</td><td>CO_SAFE</td><td>safe_to_send</td></tr><tr><td>Clearout Verification Status</td><td>co_status</td><td>CO_STATUS</td><td>status</td></tr><tr><td>Clearout Reason</td><td>co_reason</td><td>CO_REASON</td><td>substatus.desc</td></tr><tr><td>Clearout Suggested Email</td><td>co_semail</td><td>CO_SEMAIL</td><td>suggested_email_address</td></tr><tr><td>Clearout Disposable Status</td><td>co_dispose</td><td>CO_DISPOSE</td><td>disposable</td></tr><tr><td>Clearout Free Account Status</td><td>co_free</td><td>CO_FREE</td><td>free</td></tr><tr><td>Clearout Role Account Status</td><td>co_role</td><td>CO_ROLE</td><td>role</td></tr><tr><td>Clearout Verified on</td><td>co_vryon</td><td>CO_VRYON</td><td>verified_on</td></tr><tr><td>Clearout MX Record</td><td>co_mxrec</td><td>CO_MXREC</td><td>detail_info.mx_record</td></tr><tr><td>Clearout SMTP Provider</td><td>co_smtppro</td><td>CO_SMTPPRO</td><td>detail_info.smtp_provider</td></tr><tr><td>Clearout Verified Datetime</td><td>co_vrydt</td><td>CO_VRYDT</td><td>verified_on</td></tr><tr><td>Clearout Gibberish Status</td><td>co_gibberish</td><td>CO_GIBBERISH</td><td>gibberish</td></tr></tbody></table>
{% endstep %}
{% endstepper %}

If you have questions or need help fine-tuning this workflow, you can reach out to the [Clearout Support](../../help-and-support/ask-a-question.md)&#x20;

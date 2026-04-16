---
description: Verify & clean email lists in HubSpot CRM
---

# HubSpot CRM

HubSpot CRM integration with Clearout allows you to verify and maintain clean contact email list&#x73;**. Clearout natively integrates with HubSpot**, allowing you to import and export HubSpot lists directly from your Clearout account, and bad contacts can be automatically unsubscribed during the export process.&#x20;

This integration helps identify invalid, non-deliverable, and risky email addresses, **ensuring better data quality across your CRM**.&#x20;

You can also watch this short walkthrough to see the full end‑to‑end flow:

{% embed url="https://www.youtube.com/watch?v=tXFCh58EgRM" %}

## Setup

{% stepper %}
{% step %}
### Connect account

* Log in to your Clearout account.
* Go to the [**Integration**](https://app.clearout.io/integrations/connect-account) tab and choose **HubSpot**.
* Click **Add Account** and sign in with your HubSpot credentials

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/clearout-hubspot (1).png" alt="Connect HubSpot account for CRM list Email validation" width="563"><figcaption></figcaption></figure></div>

* Once connected, click on the connected HubSpot accounts to see your lists

{% hint style="info" %}
You can connect multiple HubSpot accounts to the same Clearout account
{% endhint %}
{% endstep %}

{% step %}
### Add the email lists

* From the linked HubSpot account view in Clearout, select the list(s) you want to validate.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (28).png" alt="Select HubSpot Email List to validate on Clearout App" width="563"><figcaption></figcaption></figure></div>

* Click **Add to My list** to import them into Clearout for verification
{% endstep %}

{% step %}
### Verify the email list

* After the list is added, click **Verify** to start validating the HubSpot list.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (8).png" alt="Start Verification of selected HubSpot List" width="563"><figcaption></figcaption></figure></div>

* Clearout will process the list and mark each email with a verification status (valid, invalid, risky, etc.).
{% endstep %}

{% step %}
### Export the verified results

Once validation is complete, you can:

* **Download** the results as CSV
* **Export directly back to HubSpot.**
*   When exporting to HubSpot, choose one or both of the following:

    * **Unsubscribe:** Automatically unsubscribes invalid/non‑deliverable email addresses in the selected HubSpot static list, removing them from mailings (<mark style="color:$info;">Unsubscribe works only for static lists).</mark>
    * **Append:** Adds Clearout result columns to the existing records in HubSpot so you can see verification status and related fields inside HubSpot.

    <div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (30).png" alt="Export by appending verified email verification results to HubSpot" width="375"><figcaption></figcaption></figure></div>
{% endstep %}
{% endstepper %}

### Display Clearout columns in HubSpot

To show Clearout fields inside your HubSpot list view:

1. Open the verified list in HubSpot.
2. Click **Actions → Edit columns**.
3. Search for **Clearout Information**.
4. Select the Clearout columns you want to display and save the changes.​

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (10).png" alt="Edit Columns on Hubspot to select Clearout Appended columns for visibility" width="431"><figcaption></figcaption></figure></div>

This makes it easy for your team to filter, segment, and act based on Clearout verification results directly inside HubSpot CRM


# GoHighLevel

**Remove invalid and spammy emails from your GoHighLevel** CRM using Clearout's bulk list email validation. Keep your contact list clean and improve GoHighLevel email deliverability.

## How to Verify Emails in GoHighLevel in 4 Steps

{% embed url="https://www.youtube.com/watch?embeds_referring_euri=https://clearout.io/&v=Aa07CKASq0Q" %}

{% stepper %}
{% step %}
#### Connect account

After logging in to your Clearout account, go to the Integration page and select GHL. Fill in with "**Private Integration Key, Location ID, and Account Name**."

\
Here's how you can retrieve these details from your GHL account:

* To integrate Clearout with GHL, you'll need the Private Integration Token and Location ID:
  * Go to **Settings,** then navigate to **Sub-account > Other Settings > Private Integrations > Create New Integration**.
  * Use the **generated key** for Clearout integration and grant the necessary scopes (**view/edit tags, view/edit contacts, and view/edit custom fields**).
* To get the **Location ID**, go to **Settings** **→ Business Profile → Location ID**.

Once you've fed the Key details into Clearout, click on the "**Add Account**" button.<br>
{% endstep %}

{% step %}
#### Add the email lists

Once your GHL account is connected, Clearout will automatically display your tagged contact lists from GHL.\
\
To prepare contacts for verification, start by [creating tags in GHL](https://www.bardeen.ai/answers/how-to-create-tags-in-gohighlevel) to group specific contacts. These tagged contact lists will then appear in Clearout, allowing you to select one or more for verification. This organized tagging system makes it easy to **manage and verify** only the contacts you need, directly from your GoHighLevel account.
{% endstep %}

{% step %}
**Verify the email address list**

After successfully adding the selected tagged list, click on "**Verify**" to initiate the validation process.
{% endstep %}

{% step %}
**Export the verified results**

Once the validation is completed, the user can choose how to export the verified list to the GHL account. The user can export the result by choosing to unsubscribe, append, or else select both.

**Unsubscribe**: On selecting this option, the non-deliverable email addresses will be automatically un-tagged from the Tag list and will not be part of the verified list for the campaigns.

**Append:** By selecting this option, the user can export the result, along with the selected appended fields, back to the GHL accoun&#x74;**.**
{% endstep %}
{% endstepper %}

<h3 align="center">Frequently Asked Questions</h3>

<details>

<summary>What permissions are required to integrate Clearout with GoHighLevel?</summary>

You'll need the <mark style="color:$info;">**Private Integration Token**</mark> and <mark style="color:$info;">**Location ID**</mark> from GoHighLevel. Ensure that you have access to the <mark style="color:$info;">**sub-account settings**</mark> to generate this token.

</details>

<details>

<summary>How can I retrieve the Private Integration Token and Location ID?</summary>

* Go to <mark style="color:$info;">**Settings**</mark> inside the sub-account, navigate to <mark style="color:$info;">**Other Settings**</mark> → <mark style="color:$info;">**Private Integrations**</mark>, and click on <mark style="color:$info;">**Create New Integration**</mark> button to generate the integration token.
* For the <mark style="color:$info;">**Location ID**</mark>, go to <mark style="color:$info;">**Settings**</mark> → <mark style="color:$info;">**Business Profile**</mark>.

</details>

<details>

<summary>What happens if an email is marked non-deliverable?</summary>

Non-deliverable emails will be <mark style="color:$info;">**untagged from the GHL list**</mark>(as part of Unsubscribe), ensuring they do not remain in active campaigns.

</details>

<details>

<summary>Can I verify multiple tagged lists at once?</summary>

Yes, you can select and verify multiple tagged lists simultaneously, making the validation process faster and more efficient.

</details>

<details>

<summary>How long does it take to verify an email list in GHL?</summary>

The verification time depends on the <mark style="color:$info;">**size of the list**</mark> and the <mark style="color:$info;">**domain type**</mark> of the email addresses. Generally, free domains verify faster, while business domains may take longer as it is dependent on the time taken by the recipient server to respond back.

</details>

<details>

<summary>Is there any additional cost for this integration?</summary>

No, the integration itself is free. The cost is based on the number of credits used for email verification.

</details>

<details>

<summary>Can I integrate Clearout with multiple GHL sub-accounts?</summary>

Yes, you can add and manage multiple GHL sub-accounts within Clearout by using separate integration tokens and location IDs for each sub-account.

</details>

<details>

<summary>What happens if the integration token expires?</summary>

If the integration token expires, you'll need to generate a new token from the sub-account settings in GHL and reconfigure it in Clearout.

</details>

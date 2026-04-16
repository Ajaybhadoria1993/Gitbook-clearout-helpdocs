# Kit (formerly ConvertKit)

Improve the quality of your Kit subscribers by verifying email addresses directly with Clearout. Prevent bounce rates, clean up your tags, and enhance your email marketing performance with real-time email verification.

{% embed url="https://youtu.be/sgGF_Lq6no8" fullWidth="false" %}

## How the Kit Integration Works

Clearout integrates seamlessly with Kit to help you validate email addresses associated with your subscribers. In Kit, tags are commonly used to segment subscribers for email campaigns. In Clearout, each tag is treated as a separate list, allowing you to easily clean and maintain segmented audiences.

{% stepper %}
{% step %}
### Connect Your Kit Account

Click “**Add Account**” in Clearout to securely authenticate and sync your Kit account.&#x20;

{% hint style="info" %}
**Note**: Only one Kit account can be connected at a time. To connect a different account, you will need to log out from Kit and reauthenticate.
{% endhint %}

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/kit_add_account_page.webp" alt="Connect Kit account with Clearout for List verification"><figcaption></figcaption></figure></div>


{% endstep %}

{% step %}
### Select a Tag (List) for Validation

Once connected, Clearout displays all your **Kit tags as lists**.\
\
Subscriber counts are not shown until a specific tag is added for validation.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/kit_add_list_page.webp" alt="Select Kit Tag list to start verification" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Validate Your Subscribers

**Select a tag** to run a real-time email verification check. Clearout will identify and categorize invalid, disposable, gibberish, role-based, or risky email addresses.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/kit_list_added.webp" alt="Start verification of your selected Kit list" width="563"><figcaption></figcaption></figure></div>

>
>
> ### Key Integration Details
>
> * **Tags as Lists**\
>   In Kit, tags segment your subscribers. Clearout treats each tag as an individual list.\
>   While Clearout has no tag-based limits, Kit allows up to 1,000 subscribers on the free plan.
> * **Email Counts per List**\
>   The number of emails under a tag is not visible until the tag is selected/added for validation.
> * **Custom Fields Created on Export**\
>   Clearout adds custom fields such as **Clearout Safe To Send**<mark style="color:$info;">**, Clearout Status and Clearout AI Verdict**</mark> to subscriber records only during the export process. These fields enhance subscriber data directly within your Kit dashboard.
> * **Subscriber Unsubscription**\
>   If you choose to unsubscribe invalid addresses during export, subscribers will be unsubscribed **only from the selected tag**. They will remain active under other tags they belong to.
{% endstep %}

{% step %}
### Export the verified results

After the validation is complete, the user can download the results in .CSV or .XLSX format, or export them directly to their Kit account.

The user can export the results by selecting either "**unsubscribe**," "**append**," or **both**.

* **Unsubscribe**: Users can unsubscribe the invalid/non-deliverable email addresses on the Kit Tag automatically, which removes all the non-deliverables from the selected tag.
* **Append**: User can export the result and append the Clearout columns with the selected tag in the Kit account.

This ensures your email list remains accurate, your reputation intact, and your Kit automation workflows clean.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/kit_export.webp" alt="Export verified list results to Kit "><figcaption></figcaption></figure></div>


{% endstep %}
{% endstepper %}

## Using Clearout Fields in Kit Workflows and Campaigns

Clearout’s custom fields provide deep insights into the quality of each subscriber. These fields can be used directly within Kit’s:

* **Email Campaigns**: Filter out low-quality emails before sending broadcasts.
* **Visual Automations (Workflows)**: Apply conditions and paths based on validation status (e.g., only continue for Clearout Safe To Send = Yes).
* **Filters and Segments**: Use Clearout fields to create more refined segments and improve targeting.

For every validated tag or preset, you can use the **Clearout \*** fields in Kit filters and automation rules to optimize your communication and reduce churn.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/kit_custom_field_filter.webp" alt="Edit Kit filters to add Clearout fields in the automation rules"><figcaption></figcaption></figure></div>

<h3 align="center">Frequently Asked Questions</h3>

<details>

<summary>Why do I need the Clearout + Kit integration?</summary>

This integration helps keep your email list clean, reliable, and high-performing by verifying the email addresses of your Kit subscribers in real time. By removing invalid, risky, or fake emails, you can:

* Boost deliverability and inbox placement
* Avoid bounce-related penalties
* Enhance segmentation and automation flows
* Maximize ROI from every email campaign

It’s the easiest way to ensure you’re sending messages to real, engaged subscribers—without leaving your Kit environment.

</details>

<details>

<summary>Is Kit the same as ConvertKit?</summary>

Yes, **Kit is the new name for ConvertKit**. The rebranding reflects the platform’s growth beyond email into a broader creator marketing ecosystem. All existing features, including your account, tags, automations, and integrations like Clearout, remain fully functional under the new name.

</details>

<details>

<summary>How does the Clearout + Kit integration work?</summary>

Once you connect your Kit account with Clearout, your **tags** (used in Kit to segment subscribers) will appear as lists in Clearout. You can select any tag for email validation and export the cleaned data back to Kit with enhanced fields and optional actions like unsubscribing invalid addresses.

</details>

<details>

<summary>What happens to invalid email addresses after validation?</summary>

During export, Clearout offers two options:

* **Unsubscribe**: Remove invalid or non-deliverable subscribers from the selected tag only.
* **Append**: Add custom Clearout fields (e.g., Clearout Status, Clearout Safe To Send etc) to each subscriber in Kit. You may also apply both actions simultaneously.

</details>

<details>

<summary>Are my tags or subscriber data modified during validation?</summary>

No. The validation process does not alter your Kit data unless you choose to export the results and select an action like unsubscribing or appending fields.

</details>

<details>

<summary>Can I use Clearout fields in Kit’s Visual Automations or Broadcasts?</summary>

Yes. The fields Clearout adds during export (e.g., **Clearout Status, Clearout Score, Clearout AI Verdict etc**) can be used in:

* **Email Campaign filters**
* **Visual Automations (Workflows)**
* **Segment creation**

This enables you to send emails only to verified, high-quality subscribers and build automations based on real-time email hygiene data.

</details>

<details>

<summary>Can I connect multiple Kit accounts to Clearout?</summary>

Yes. Clearout allows multiple accounts to be connected. To connect multiple accounts, you need to log out from current Kit account to connect new account. Once accounts are connected, you can switch between the accounts to validate the tags.

</details>

<details>

<summary>Why can’t I see email counts under a tag before validation?</summary>

For clarity and performance, email counts are only visible after a tag is added or selected for validation in Clearout.

</details>

<details>

<summary>How are credits used for validating Kit subscribers?</summary>

Clearout consumes **1 credit per email address validated**. If the same email appears under **multiple tags**, credits will be charged for each instance, as Clearout performs a **real-time validation** every time an email is processed through a new tag.

</details>

<details>

<summary>Do Clearout credits expire?</summary>

* **One-time purchased credits**: Never expire.
* **Subscription-based credits**: Renew monthly and leftover credits rollover to next month.

</details>

<details>

<summary>Where can I view Clearout pricing?</summary>

You can explore our pricing plans and choose what suits your needs here: [Clearout Pricing](https://clearout.io/pricing)

</details>

<details>

<summary>Still have questions?</summary>

We’re happy to help. Reach out to us at [us@clearout.io](mailto:us@clearout.io) for any additional support or inquiries.

</details>

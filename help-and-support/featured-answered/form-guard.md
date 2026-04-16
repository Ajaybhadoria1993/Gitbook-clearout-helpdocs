# FG

<details>

<summary>Does Form Guard work with my existing form builder?</summary>

Yes. Form Guard works with **all major form builders and custom HTML forms**, including platforms like WordPress, HubSpot, Unbounce, Leadpages, Marketo, Webflow, and others.

Integration requires adding a lightweight **JavaScript snippet** to your form page.

</details>

<details>

<summary>Will Form Guard slow down my website or form load time?</summary>

No. Form Guard loads **asynchronously**, which means it runs in the background and does not affect your page load speed or form performance.

</details>

<details>

<summary>Is there a limit to the number of forms I can protect?</summary>

No. You can protect **unlimited forms** under your account. Usage depends only on your **available credit balance and plan**.

</details>

<details>

<summary>How do I remove the “Powered by Clearout” branding?</summary>

The “**Powered by Clearout**” **branding appears on free accounts**.\
Once you upgrade to a **subscription plan**, the branding is automatically removed.

</details>

<details>

<summary>How are credits charged for Form Guard validations?</summary>

Each validated field consumes **2 credits per validation**.

For example:

* Email validation → 2 credits
* Phone validation → 2 credits
* Name validation → 2 credits

If a form validates both **email and phone**, the total cost is **4 credits per validation**.

</details>

<details>

<summary>How can I check if Form Guard is working?</summary>

You can monitor Form Guard activity in the **Clearout Dashboard** under the [**Activities**](https://app.clearout.io/activities) **section**.

The dashboard shows:

* Validation statistics
* Usage logs
* Validation results

Detailed logs for each validation are available under **Activities**, and results can be exported for analysis.

</details>

<details>

<summary>What happens to invalid or fake submissions?</summary>

Form Guard **blocks invalid submissions** before they are accepted.

If a user enters invalid information, they will see an error message and must correct the input before submitting the form.

Invalid attempts are also recorded in the [**Activities**](https://app.clearout.io/activities) **section** for review.

</details>

<details>

<summary>Why does email validation sometimes take longer?</summary>

Form Guard performs **real-time validation by connecting directly to the recipient’s mail server** to confirm the mailbox status.

For some domains, particularly business email servers, this process may take a few extra seconds depending on the server response time.

</details>

<details>

<summary>What is the recommended timeout for email validation?</summary>

For business email verification, a timeout of **10 seconds** is recommended.

This provides a balance between **high accuracy and good user experience**.

</details>

<details>

<summary>How accurate is phone number type classification (Mobile, Landline, VoIP)?</summary>

Phone number type classification is based on carrier allocation data.

If a number has been **ported between networks** (for example, from VoIP to mobile), the classification may still show the original type until telecom databases update.

This limitation applies across the industry.

</details>

<details>

<summary>How accurate is carrier detection?</summary>

Carrier detection is based on **trusted telecom datasets** and is generally accurate at the time of lookup.

However, if a number has recently been ported to another carrier, the updated carrier may not appear immediately due to telecom data update cycles.

Carrier information should be treated as a **best-available snapshot**, not a permanent identifier.

</details>

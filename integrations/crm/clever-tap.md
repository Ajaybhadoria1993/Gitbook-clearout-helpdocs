# CleverTap

Reduce email bounce rates, improve deliverability, and have confidence that your emails are reaching the inbox. **Clearout email verification integration with CleverTap** ensures that the contacts are valid, which improves data quality and database health.

{% embed url="https://youtu.be/u6w1n9IcZgg?si=AoYcVJQqxCRXgucw" %}

## How It works:&#x20;

{% stepper %}
{% step %}
### Connect CleverTap Account <a href="#ufmb1" id="ufmb1"></a>

* After logging into Clearout, go to "**Integrations.**" Select **CleverTap** and click on "**Connect to CleverTap.**"
* Enter the following project details to authorize the connection:
* Project ID
* Passcode
* Region

These details can be obtained by navigating to the **Settings** > **Project page** of the CleverTap dashboard. To identify the **region** of your account, **check the URL** of your CleverTap account.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/CT1-2.png" alt="Copy Region, account ID and Passcode from Clevertap account to connect with Clearout for list verification"><figcaption></figcaption></figure></div>

<table><thead><tr><th width="457.44140625">CleverTap Dashboard URL</th><th>Region</th></tr></thead><tbody><tr><td><a href="https://eu1.dashboard.clevertap.com/login.html#/">https://eu1.dashboard.clevertap.com/login.html#/</a></td><td>EU1</td></tr><tr><td><a href="https://in1.dashboard.clevertap.com/login.html#/">https://in1.dashboard.clevertap.com/login.html#/</a></td><td>IN1</td></tr><tr><td><a href="https://us1.dashboard.clevertap.com/login.html#/">https://us1.dashboard.clevertap.com/login.html#/</a></td><td>US1</td></tr><tr><td><a href="https://sg1.dashboard.clevertap.com/login.html#/">https://sg1.dashboard.clevertap.com/login.html#/</a></td><td>SG1</td></tr></tbody></table>
{% endstep %}

{% step %}
### Add the Email Lists <a href="#xfjsy" id="xfjsy"></a>

After the successful login, select the email list from the existing CleverTap audience list. Then click on "**Add to My List**" to proceed with the audience list validations.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/check-box.webp" alt="Select CleverTap List to verify on Clearout"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Verify the Email Lists <a href="#wcq1p" id="wcq1p"></a>

Once the email list is successfully added, click on "**Verify**" to start validating the added CleverTap list.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/list-verify (2).webp" alt="Start verification of the selected list"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Export the Verified Lists <a href="#v3o3k" id="v3o3k"></a>

Once the email validation is completed, the user can choose how to export the verified list to the CleverTap account. The user can export the result by choosing to unsubscribe or append else by selecting both.\
\
**Unsubscribe:** The user can automatically unsubscribe the invalid/non-deliverable email addresses on the CleverTap list, removing all non-deliverables from the mailing list.\
\
**Append:** The user can export the result and append the Clearout columns with the original file in the CleverTap account.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/export.webp" alt="Export verified list results to CleverTap "><figcaption></figcaption></figure></div>

You will see various Clearout columns to append and can select the ones you need. We recommend selecting "**safe to send**" along with "**Status**" for the highest deliverability rate, or the ones classified as "**Valid.**"
{% endstep %}
{% endstepper %}

## Clearout Verification Status <a href="#id-4xh1u" id="id-4xh1u"></a>

Every email is primarily categorized as either Valid, Invalid, Unknown, or Catch-All.\
\
**Valid:** The email address will be declared a Valid Email Address after a successful SMTP transaction if the recipient's mail server accepts it. Even if the email address is real, sending emails to addresses tagged as "Disposable" is not advised.\
\
**Invalid:** An email address is marked Invalid if it's syntactically wrong or if an email account doesn't exist on the receiving mail server.\
\
**Unknown:** The receiving mail server may reply slowly or be momentarily unable to handle queries at times. Those email addresses have an "unknown" status, which can be revalidated after some time.\
\
**Catch-All:** An email address that accepts all messages sent to that address and never bounces them back.\
\
**Clearout Safe to send:** Clearout identifies high-quality email addresses using an advanced-level screening mechanism, resulting in greater deliverability and open rates for your emails. We highly advise sending emails in bulk within a 24-hour time frame using email addresses with a deliverability score of 1.\
\
**Clearout Disposable:** Certain service providers generate temporary email addresses for a limited duration, such as a few hours to a few days. "Disposable Email Addresses" is the term for such addresses. Sending emails to such addresses increases the bounce rate; sending emails to "**Disposable Email Addresses**" is not recommended.\
\
[Click here](../../email-verifier/overview.md#associated_results) to Learn More about other Clearout statuses.


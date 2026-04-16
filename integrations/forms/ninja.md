# Ninja Forms

Have you been receiving form entries with temporary or invalid email addresses?&#x20;

Avoid such bad and invalid email leads at the time of capture on your Ninja Forms with the help of Clearout Email Validator!

Using the **Clearout WordPress plugin** in Ninja Forms can detect and reject :

* Misspelled and other **invalid email** addresses
* **Temporary**, disposable, or throwaway emails that cause bounces
* **Spam traps**, which can damage your _sender's reputation, can get you blacklisted_
* **Gibberish emails**, which are random email addresses created by spammers, usually
* **Role-based** email addresses that have low value to your sales and marketing

{% embed url="https://www.youtube.com/watch?t=1s&v=Ip_ZNIXUqiM" %}

## Steps to integrate Ninja Forms with Clearout WordPress Plugin

{% stepper %}
{% step %}
**Log in** to your Clearout account, navigate to the ‘**Developer**’ section. Click on '**+Create API Token**,' add a name and description, then click **Create**.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/Clearout-API-Token-creation.png" alt="Clearout API Token Creation for Ninja Form Integration"><figcaption></figcaption></figure></div>

You’ll see the API token. **Copy Clearout API Token**, then go back to your WordPress site.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/Clearout-API-Token-copying.png" alt="Copy Clearout API Token Creation for Ninja Form Integration"><figcaption></figcaption></figure></div>


{% endstep %}

{% step %}
Set up the Clearout Email Validator plugin. Go to your form **Settings** > **Clearout Email Validator** _(make sure you’ve activated the plugin)_, **paste** your Clearout API token.

Note: By default, the plugin will block role-based addresses and disposable addresses. You can allow either or both by choosing the checkboxes in the settings.&#x20;

You can also enable "**Accept only Business Address as valid**", which will override all the other settings.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/clearout-plugin-settings-1-768x345-1.png" alt="WordPress settings of Clearout Email Validator Plugin"><figcaption></figcaption></figure></div>


{% endstep %}

{% step %}
Next, if you scroll down, navigate to find the '**Apply Validation**' as shown below. Select '**Ninja Forms**' for the email validation to perform.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/clearout-plugin-settings-2-768x331-1.png" alt="WordPress settings of Clearout Email Validator Plugin for Ninja Forms"><figcaption></figcaption></figure></div>

That’s it! \
\
Now, when performing a test on your form, it will no longer accept invalid email addresses. \
\
Shown below is **an example** of a Ninja form integrated with Clearout Email Validator. A Gmail address with a typing error has been identified in real-time as invalid, giving the message ‘_This email address is invalid or not allowed – please check.’_

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/after-1024x536-1.png" alt="Email Validation example on Fluent Forms"><figcaption></figcaption></figure></div>


{% endstep %}
{% endstepper %}

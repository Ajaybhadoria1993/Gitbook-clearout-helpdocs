# Ninja

Have you been receiving form entries with temporary or invalid email addresses?

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

You’ll see the API token. **Copy Clearout API Token**, then go back to your WordPress site.
{% endstep %}

{% step %}
Set up the Clearout Email Validator plugin. Go to your form **Settings** > **Clearout Email Validator** _(make sure you’ve activated the plugin)_, **paste** your Clearout API token.

Note: By default, the plugin will block role-based addresses and disposable addresses. You can allow either or both by choosing the checkboxes in the settings.

You can also enable "**Accept only Business Address as valid**", which will override all the other settings.
{% endstep %}

{% step %}
Next, if you scroll down, navigate to find the '**Apply Validation**' as shown below. Select '**Ninja Forms**' for the email validation to perform.

That’s it!\
\
Now, when performing a test on your form, it will no longer accept invalid email addresses.\
\
Shown below is **an example** of a Ninja form integrated with Clearout Email Validator. A Gmail address with a typing error has been identified in real-time as invalid, giving the message ‘_This email address is invalid or not allowed – please check.’_
{% endstep %}
{% endstepper %}

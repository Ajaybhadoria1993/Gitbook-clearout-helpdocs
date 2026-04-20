# WS

Take advantage of Clearout’s integration with WS Form to clean the email contacts in real time basis

Are your online forms collecting temporary, disposable, role-based, gibberish or mistyped leads?\
Identify and remove such invalid leads at the time of capture on WS Forms by integrating them with Clearout Email Validator.\
Now upgrade the quality of leads effortlessly.

## Steps To Integrate WS Forms With Clearout WordPress Plugin <a href="#l65tx" id="l65tx"></a>

{% stepper %}
{% step %}
**Log in** to your Clearout account, navigate to the ‘**Developer**’ section. Click on '**+Create API Token**,' add a name and description, then click **Create**.

You’ll see the API token. **Copy Clearout API Token**, then go back to your WordPress site.
{% endstep %}

{% step %}
Set up the Clearout Email Validator plugin. Go to your form **Settings** > **Clearout Email Validator** _(make sure you’ve activated the plugin)_, **paste** your Clearout API token.

{% hint style="info" %}
<mark style="color:$info;">**NOTE**</mark>:

By default, the plugin will block role-based addresses and disposable addresses. You can allow either or both by choosing the checkboxes in the settings.
{% endhint %}

You can also enable "**Accept only Business Address as valid**", which will override all the other settings.

Navigate down to '**Apply Validation**' > Select **Forminator Form** > Click on **Apply** to activate the validation.
{% endstep %}

{% step %}
We have a **Test** Plugin option at the bottom of the plugin settings page, allowing you to test the settings and see sample error messages.

That's it! Below is **an example** of a WS Form integrated with Clearout, identifying an invalid email address in real-time.
{% endstep %}
{% endstepper %}

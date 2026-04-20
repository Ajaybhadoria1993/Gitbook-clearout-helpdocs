# Forminator

Are your online forms collecting leads that are temporary, disposable, gibberish, role-based, or mistyped? Upgrade the quality of leads by identifying and removing such invalid email addresses at the time of lead capture on your Forminator Forms with the help of the Clearout Email Validator Plugin.

There are two ways to integrate:

* Directly through Clearout WordPress Plugin
* Using Clearout **Form Guard** on the form

{% embed url="https://www.youtube.com/watch?t=1s&v=dW68KlMLrFk" %}

## Option 1: Integrate using Clearout WordPress Plugin <a href="#h0tiy" id="h0tiy"></a>

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
Navigate down to '**Apply Validation**' > Select **Forminator Form** > Click on **Apply** to activate the validation.

That's all! When you test your form now, it will not accept invalid email addresses.
{% endstep %}
{% endstepper %}

## Option 2: Integrate Using Clearout Form Guard <a href="#j2wot" id="j2wot"></a>

Embedding Clearout’s Form Guard in Forminator forms can detect disposable, invalid, and such bad email addresses in real-time, upgrading the quality of leads and turning your email lists into an army of raving, engaged super-fans!

{% embed url="https://www.youtube.com/watch?v=-3JC0ZojnhI" %}

{% stepper %}
{% step %}
Go to the **Clearout account**, click on **Form Guard**. "**Create Guard**" and customise the validation checks. **Save** the Guard to generate the **JavaScript code snippet**.
{% endstep %}

{% step %}
**Copy** the Clearout Form Guard snippet, move to the WordPress site → **All pages** section. **Select the form** where you want to embed the code.
{% endstep %}

{% step %}
**Create** a code block > **Paste** the Clearout Form Guard snippet & Click on **Update**.
{% endstep %}
{% endstepper %}

Shown below is **an example** of a Forminator form integrated with Clearout. An invalid Gmail address has been identified in real-time, giving the message ‘_Please enter a valid email address._’

Try this effortless integration to ensure quality lead submissions!

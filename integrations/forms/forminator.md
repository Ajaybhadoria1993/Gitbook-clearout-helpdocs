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

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/Clearout-API-Token-creation.png" alt="Clearout API Token Creation for Forminator Form Integration"><figcaption></figcaption></figure></div>

You’ll see the API token. **Copy Clearout API Token**, then go back to your WordPress site.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/Clearout-API-Token-Forminator forms-copying.png" alt="Copy Clearout API Token Creation for Forminator Form Integration"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
Set up the Clearout Email Validator plugin. Go to your form **Settings** > **Clearout Email Validator** _(make sure you’ve activated the plugin)_, **paste** your Clearout API token.

Note: By default, the plugin will block role-based addresses and disposable addresses. You can allow either or both by choosing the checkboxes in the settings.&#x20;

You can also enable "**Accept only Business Address as valid**", which will override all the other settings.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image3_forminator.png" alt="WordPress settings of Clearout Email Validator Plugin"><figcaption></figcaption></figure></div>


{% endstep %}

{% step %}
Navigate down to '**Apply Validation**' > Select **Forminator Form** > Click on **Apply** to activate the validation.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/Forminator-forms.png" alt="WordPress settings of Clearout Email Validator Plugin for Forminator Form"><figcaption></figcaption></figure></div>

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

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image6_forminator-1024x537.png" alt="WordPress All pages section to add Clearout Form Guard snippet"><figcaption></figcaption></figure></div>


{% endstep %}

{% step %}
**Create** a code block > **Paste** the Clearout Form Guard snippet & Click on **Update**.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image1_forminator-1024x512.png" alt="Create code block and paste Clearout Form Guard snippet"><figcaption></figcaption></figure></div>


{% endstep %}
{% endstepper %}

Shown below is **an example** of a Forminator form integrated with Clearout. An invalid Gmail address has been identified in real-time, giving the message ‘_Please enter a valid email address._’

Try this effortless integration to ensure quality lead submissions!

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image5_forminator.png" alt=""><figcaption></figcaption></figure></div>


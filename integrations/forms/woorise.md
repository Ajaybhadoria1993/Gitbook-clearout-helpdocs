# Woorise

Woorise is a widely used no-code form builder to create forms and capture leads using a drag-and-drop interface. But even the best-designed forms can still be exposed to spam, fake entries, and low-quality submissions, which can skew analytics, reduce campaign efficiency, and fill your CRM with contacts that never convert.

**Clearout Form Guard** adds a simple **plug-and-play real-time validation layer** to your forms with minimal setup. It **validates key fields like email, phone, and name** in real time, helping block bots, invalid data, and fake entries before they reach your database. The result is cleaner data and a form **system you can trust for accurate marketing and outreach**.

## Integration Steps

{% stepper %}
{% step %}
### Create a Form Guard in Clearout

Log in to your Clearout account and navigate to the **Form Guard** tab.\
Click Create Guard to start configuring your form protection.

Use the following configuration:

* **Form**: For a Standard HTML form, Form Guard will automatically detect it.
* **Email Field**: No customization required, Form Guard will auto-detect the email field.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/unknown (10).png" alt="Customizing Email Validation on Form Guard for Real-time validation" width="563"><figcaption></figcaption></figure></div>

* **Phone Field**: No customization required, Form Guard will auto-detect the phone field.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/unknown (9).png" alt="Customizing Phone Validation on Form Guard for Real-time validation" width="563"><figcaption></figcaption></figure></div>

* **Name Field**: Not a standard field used in Woorise; **custom selectors** will be required for Form Guard to detect it properly.

{% hint style="info" %}
Note: For any assistance, reach out to [us@clearout.io](mailto:us@clearout.io)&#x20;
{% endhint %}

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/unknown (8).png" alt="Customizing Name Validation on Form Guard for Real-time validation" width="563"><figcaption></figcaption></figure></div>

Complete the setup and **copy the code snippet** provided.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/unknown (11).png" alt="" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Open Your Form in Woorise

Go to your Woorise account and select the page where your form is embedded, then click **Edit**.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/unknown (12).png" alt="Integrating Form Guard with Woorise Forms" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Add a Custom HTML Block and Paste the Form Guard Script

Click the “**+**” icon in the top-right corner and search for **Custom HTML**.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/unknown (13).png" alt="Paste Form Guard snippet in custom HTML" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Paste the Form Guard Script

**Paste** the copied Clearout Form Guard script **and publish** the changes to activate Woorise form validation.
{% endstep %}
{% endstepper %}

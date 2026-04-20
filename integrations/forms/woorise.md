# Woorise

Woorise is a widely used no-code form builder to create forms and capture leads using a drag-and-drop interface. But even the best-designed forms can still be exposed to spam, fake entries, and low-quality submissions, which can skew analytics, reduce campaign efficiency, and fill your CRM with contacts that never convert.

**Clearout Form Guard** adds a simple **plug-and-play real-time validation layer** to your forms with minimal setup. It **validates key fields like email, phone, and name** in real time, helping block bots, invalid data, and fake entries before they reach your database. The result is cleaner data and a form **system you can trust for accurate marketing and outreach**.

## Integration Steps

{% stepper %}
{% step %}
#### Create a Form Guard in Clearout

Log in to your Clearout account and navigate to the **Form Guard** tab.\
Click Create Guard to start configuring your form protection.

Use the following configuration:

* **Form**: For a Standard HTML form, Form Guard will automatically detect it.
* **Email Field**: No customization required, Form Guard will auto-detect the email field.
* **Phone Field**: No customization required, Form Guard will auto-detect the phone field.
* **Name Field**: Not a standard field used in Woorise; **custom selectors** will be required for Form Guard to detect it properly.

{% hint style="info" %}
Note: For any assistance, reach out to [us@clearout.io](mailto:us@clearout.io)
{% endhint %}

Complete the setup and **copy the code snippet** provided.
{% endstep %}

{% step %}
#### Open Your Form in Woorise

Go to your Woorise account and select the page where your form is embedded, then click **Edit**.
{% endstep %}

{% step %}
#### Add a Custom HTML Block and Paste the Form Guard Script

Click the “**+**” icon in the top-right corner and search for **Custom HTML**.
{% endstep %}

{% step %}
#### Paste the Form Guard Script

**Paste** the copied Clearout Form Guard script **and publish** the changes to activate Woorise form validation.
{% endstep %}
{% endstepper %}

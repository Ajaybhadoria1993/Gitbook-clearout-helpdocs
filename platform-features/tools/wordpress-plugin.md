---
icon: wordpress-simple
---

# Wordpress Plugin

The Clearout WordPress plugin **integrates with major WordPress form plugins to validate email addresses in real time upon submission.** This helps keep your lists clean, protects sender reputation, and stops bad sign‑ups before they reach your CRM or ESP

**With** **Clearout + WordPress**, you can:

* Allow only valid email addresses during registration, subscription, and lead capture.​
* Block spam traps, disposable and fake email addresses.​
* Enforce business/work email addresses on specific forms (for example, demo or trial requests).​
* Optionally block free email providers (gmail.com, yahoo.com, outlook.com, etc.) when required.​
* Reduce fraudulent and bot sign-ups, improving overall data quality.

{% embed url="https://www.youtube.com/watch?v=YG5BrBn7FHo" %}

## Steps to obtain the Clearout Email Validator Plugin <a href="#keyqj" id="keyqj"></a>

{% stepper %}
{% step %}
#### Connect account <a href="#epnt6" id="epnt6"></a>

If you are not an existing Clearout user, firstly [create an account](https://app.clearout.io/register). Existing Clearout users can begin from Step 2

If you are new to Clearout, [create an account](https://app.clearout.io/register). Existing Clearout users can sign in and generate an API token from **Developer → API Tokens** to use with the plugin
{% endstep %}

{% step %}
#### Install and Activate the Plugin <a href="#qip10" id="qip10"></a>

* Log in to your WordPress admin dashboard.
* Go to **Plugins → Add New**.
* In the search bar, type **“Clearout email validator."**
* Locate the [**Clearout Email Validator**](https://wordpress.com/plugins/clearout-email-validator) plugin and click **Install Now**.
* After installation, click **Activate** to start using the plugin
{% endstep %}

{% step %}
#### Plugin Setup <a href="#h8w70" id="h8w70"></a>

Finally, please configure the plugin to suit your preferences. Once installed and active, follow these steps. In your WordPress account

* Go to Settings → Clearout email validator
* Enter the [API token](https://app.clearout.io/developer/api/list) (Create one if it does not exist)
* Provide the timeout you wish (the time allowed to validate the email ID once it is submitted by the registrant or subscriber).
* Select the types of email addresses you want to be shown as valid.
* Click on Apply
{% endstep %}
{% endstepper %}

{% hint style="info" %}
<mark style="color:$info;">**Important note**</mark>

Complete a test form immediately after setup to ensure the plugin and validation rules work as intended. For plugin setup testing, use the [test email address](../../developers/api/overview.md#testing).
{% endhint %}

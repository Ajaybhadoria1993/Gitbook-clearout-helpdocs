---
description: Configure form guard validation rules.
icon: folder-gear
---

# Advanced Settings

This section covers all advanced configuration options for the Guard.

{% hint style="info" %}
**Note:** If you're a first-time user, it's recommended to proceed with the default settings by clicking Continue. This will create a Guard with the standard configuration, allowing you to see how the Form Guard functions on your forms.

If you are updating the Form Guard settings, make sure to reload any pages where the Form Guard is integrated. This ensures the Guard loads with the updated settings and reflects the latest changes correctly.
{% endhint %}

## Timeout&#x20;

This setting defines the maximum time (in seconds) before validation times out. By default, if validation exceeds the timeout limit, the input value is considered acceptable, and form submission is not blocked. _(Default: **10 seconds**)_

It is recommended to keep this setting at its default value, as increasing the timeout may negatively impact the user experience.

## Mode&#x20;

This setting controls how and when the Form Guard triggers validation for form fields.

* **AJAX (Default)**: Validation is triggered when a user finishes interacting with a form field and moves focus away from it. This provides real-time feedback and is generally recommended for a smoother user experience.
* **FormSubmit**: Validation is triggered only when the user clicks the submit button. This mode validates all relevant fields at once, just before form submission.

Unless you have a specific reason to validate only on submission, it's recommended to keep this setting on AJAX for immediate validation feedback.

## Submit Button Selector&#x20;

The Clearout Form Guard is designed to detect the submit button automatically within your form. In most cases, no manual configuration is required.

However, if the Guard is unable to locate the submit button due to non-standard markup or dynamic form rendering, you can manually specify it by providing a valid jQuery selector in this field.

Use this option only when the automatic detection fails, ensuring that the Guard can correctly bind validation behavior to the form submission process.

## On Ready Hook (Optional)&#x20;

This option allows you to define a custom JavaScript function that runs once Clearout's Form Guard has fully loaded on your page.

You can use this to execute custom JavaScript or CSS as soon as the Form Guard is initialized, enabling additional customization or functionality tailored to your needs.

```javascript
on_ready: function() {
  // Your custom initialization code here
  console.log('Clearout widget is ready!');

  // Add custom styling or functionality
  window.clearout.$('.my-form-field').addClass('some-custom-class');
}
```

## Trigger Form Discovery on Event&#x20;

This option accepts an event name and the Form Guard listens to the event and attaches it to the form on the page.

This is particularly useful where forms are dynamically loaded and an event is emitted once they are ready

## Limit Usage (Optional)&#x20;

This option allows you to set usage limits for your Form Guard, ensuring that validations do not exceed a specified threshold per IP or globally. This helps prevent excessive usage and protects your validation credits from being misused on pages where validations are enabled.

> **Default Behavior:** If the usage limit is exceeded, validations will no longer be performed for the respective inputs. However, form submissions will not be blocked. This behaviour can be changed by enabling the <mark style="color:$info;">**Block Form Submission on Limit Crossed**</mark> Setting on your **Acceptable Values** options in the previous step.

* **Per IP**: Defines the maximum number of validations allowed per individual IP address.
* **Globally**: Sets a usage limit for validations across the entire Form Guard.

## Add Form URLs (Optional)&#x20;

This option lets you restrict validations to specific URLs, ensuring that your Guard runs validations only on approved pages.

You can also use wildcard characters (<mark style="color:blue;">\*</mark>) to define patterns instead of listing individual URLs. Pattern Examples & Interpretation:

* **https://\*.clearout.io/\*** → Allows access to any URLs and subdomains within Clearout.io.
* **https://clearout.io/forms/\***  → Restricts access to URLs under /forms/ only.
* **https://clearout.io/\*/forms**  → Grants access to any URL ending with /forms, regardless of its position in the path.

## Bot Detection (Optional)&#x20;

It is highly recommended to implement bot detection on forms to capture genuine human intent submission, thereby preventing the automated process of filling the forms, which may skew data and result in inaccurate analytics. Form Guard helps in automatic identification of bot filling through its unique methodology or by external providers such as Google

By choosing the **Default** option, your form is protected using Form Guard’s automatic detection system with no additional setup required.

Alternatively, if you prefer to use **Google reCAPTCHA v3 (invisible),** you can generate **a site key** and **secret key** from [here](https://developers.google.com/recaptcha/docs/v3) and configure it with a precise score value. The default score is 0.5, but you can change it to a value between 0.0 and 1.0. The higher the score, the more it helps reCAPTCHA check to determine very likely positive human interactions.

> **Recommendation**: If your form provider already supports reCAPTCHA, you do not need to enable this option here.


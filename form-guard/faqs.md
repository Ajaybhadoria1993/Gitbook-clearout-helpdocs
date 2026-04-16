---
description: Find answers to common questions about the Form Guard.
icon: circle-question
---

# FAQs

## General Questions  <a href="#general-questions" id="general-questions"></a>

<details>

<summary>What is form validation and why is it important?</summary>

Form validation is the process of checking whether the information submitted in a form is valid/accurate, complete, and properly formatted before it is accepted.

It helps prevent invalid or fraudulent submissions, improves the quality of collected data, and ensures that systems like CRMs and marketing platforms receive reliable information.

</details>

<details>

<summary>Can Form Guard prevent bots and spam submissions in real-time?</summary>

Yes. Form Guard validates form inputs in real time and detects suspicious or invalid submissions before they enter your system.

It can identify issues such as disposable email addresses, invalid domains, and bot-generated inputs, helping prevent spam leads from reaching your CRM or marketing tools.

</details>

<details>

<summary>What types of forms can be protected by Form Guard?</summary>

Form Guard can be used to protect most web forms that collect user information, including:

* Signup and registration forms
* Contact forms
* Lead generation forms
* Newsletter subscription forms
* Demo request or trial forms

It helps ensure that only valid and genuine submissions are accepted.

</details>

<details>

<summary>Do I need a developer to set up Form Guard?</summary>

You do not need a developer; Form Guard is a no-code form validation solution. The generated JavaScript snippet can be placed on your website's header HTML, and all settings can be customised through the Form Guard dashboard

</details>

<details>

<summary>Does form validation affect legitimate users?</summary>

No. Form Guard is designed to validate form inputs without disrupting the experience for legitimate users.

If an issue is detected, users typically receive a prompt to correct the input before submitting the form.

</details>

<details>

<summary>How fast does Form Guard validate form submissions?</summary>

Form Guard performs validation in real time during the form submission process. Most validations complete within seconds, depending on the type of checks being performed and the responsiveness of external mail servers.

</details>

<details>

<summary>How often should form validation rules be reviewed or updated?</summary>

Form validation rules should be reviewed periodically to ensure they continue to detect new spam patterns, disposable email domains, and evolving bot behavior.

Regular updates help maintain strong protection against fraudulent or low-quality submissions.

</details>

<details>

<summary>Can Form Guard improve data quality?</summary>

Yes. By filtering invalid or suspicious submissions before they reach your CRM or database, Form Guard helps ensure that collected data is accurate, reliable, and usable for sales or marketing activities.

</details>

<details>

<summary>What are common errors detected during form validation?</summary>

Form validation typically detects issues such as:

* Invalid email formats
* Disposable or temporary email addresses
* Non-existent domains
* Suspicious submissions
* Incomplete or improperly formatted fields

These checks help prevent low-quality data from entering your system.

</details>

<details>

<summary>How do bots submit forms on websites?</summary>

Bots can automatically fill and submit web forms using scripts that mimic user behavior. These bots often submit fake or disposable email addresses, random names, or incomplete data to exploit signup forms, contact forms, or lead generation forms.

Without proper validation, these automated submissions can quickly fill databases with low-quality or fraudulent entries.

</details>

<details>

<summary>How can I stop fake form submissions on my website?</summary>

Fake form submissions can be reduced by implementing real-time form validation and verification mechanisms.

Solutions like Form Guard help detect and block suspicious inputs such as disposable emails, invalid domains, or automated bot activity before the form is successfully submitted. This prevents fake data from reaching your CRM or marketing systems.

</details>

<details>

<summary>What is real-time form validation?</summary>

Real-time form validation checks the information entered in a form while the user is filling it out or at the moment of submission.

This allows errors or suspicious inputs to be detected immediately, giving users a chance to correct the information and preventing invalid or fraudulent submissions from being processed.

</details>

## Technical Questions&#x20;

<details>

<summary>The widget is working but consuming too many credits. How can I optimize usage?</summary>

**Usage Limits**

Enable usage limits in the Form Guard settings to control validation frequency.

**Custom Validation**

Implement custom validation logic using hooks to prevent unnecessary API calls.

**FormSubmit Mode**

Use FormSubmit mode instead of AJAX for less frequent validations.

**Timeout Settings**

Set appropriate timeout values to prevent excessive validation attempts.

</details>

<details>

<summary>Can I use the widget with multiple forms on the same page?</summary>

Yes, the widget supports multiple forms on the same page. Here's what you need to know:

Each form should have unique field IDs or names to prevent conflicts.

**Multiple Fields Option**

Use the Multiple Fields option if your forms require different validation rules.

**Credit Usage**

Be mindful of API credit usage when validating multiple forms simultaneously.

</details>

## Billing Questions&#x20;

<details>

<summary>How are credits calculated for the Form Guard?</summary>

Credits are calculated based on the following:

* Two credits per successful email validation
* Two credits per successful phone validation
* Two credits per successful name validation
* Credits are only consumed for successful validations

For more information, visit our [pricing guide](https://clearout.io/pricing-guide/).

</details>

<details>

<summary>What happens when I run out of credits?</summary>

When you run out of credits:

* The widget will continue to function but will not perform validations
* You'll receive a notification to purchase more credits
* Your existing forms will continue to work without validation

</details>

> Visit [Form Guard FAQs](../help-and-support/featured-answered/form-guard.md) to explore detailed answers and guidance.

---
description: Form guard API & developer implementation
icon: display-code
---

# Developer

While the Form Guard is designed for easy use requiring only a simple copy-paste and no coding there are several advanced features available through the **Form Guard SDK** that can be utilized on the client side. These capabilities are intended for **advanced users** who are comfortable writing and customizing JavaScript code.

> **Note:** Writing incomplete or syntactically incorrect code can break Clearout's Form Guard functionality on your forms. Always test custom scripts thoroughly in a **sandbox environment** before deploying them to production.

## Getting Started with the Basics&#x20;

**How to ensure the Clearout's JS has loaded correctly on the page?**&#x20;

Once you've added Clearout's JS code to your page, **refresh the page** and **open the browser** console.

You should see the below-mentioned log message indicating that **Clearout's SDK has been successfully initialized along with the version.**

<div data-with-frame="true"><figure><img src="../.gitbook/assets/formguard developer-cropped.png" alt="Console log showing Clearout SDK initialization" width="563"><figcaption></figcaption></figure></div>

This log ensures that the Form Guard is active and ready to perform validations on your page.

### Enabling debug mode & inspect options&#x20;

Enabling **Debug Mode** provides detailed and descriptive logs in the browser console. These logs include insights such as

* Field detection and validation processes
* API request and response details
* Error messages and warnings
* Performance metrics

To enable debug mode, you can override the options in your JavaScript code:

```html
<script>
    function onCoJSScriptLoaded() {
      console.log('Clearout JS Loaded - Overriding Options!!');
      window.clearout.options.debug = true
      window.clearout.options.inspect = true
    }
</script>
<script id="clearout-js-widget" src="https://clearout.io/jswidget/{your_app_id}" async onload="onCoJSScriptLoaded()"></script>
```

> **Note:** Debug mode should only be enabled in development environments as it may impact performance and expose sensitive information.

## Basic Configuration&#x20;

### Overriding Options&#x20;

In Clearout's Form Guard, settings are managed through the Clearout Dashboard. However, you can override these settings on the client side if needed. For example:

```html
<script>
  function onCoJSScriptLoaded() {
    console.log('Clearout JS Loaded - Overriding Options!!');
    window.clearout.options.mode = 'formSubmit'
    window.clearout.options.email.block_free_account = true
    window.clearout.options.email.feedback_free_account_message = 'Free email accounts are not allowed :('
  }
</script>
<script id="clearout-js-widget" src="https://clearout.io/jswidget/{your_app_id}" async onload="onCoJSScriptLoaded()"></script>
```

This will force the Form Guard to use FormSubmit mode and block free email accounts, regardless of the dashboard settings.

### **Custom Form Selection**&#x20;

The **window.clearout.options.form\_elements** option allows you to specify which form elements on the page require validation. This is particularly useful for div-based or non-standard forms or custom form implementations.

```javascript
window.clearout.options.form_elements = [
  {selector:'#custom-form-container'}, // treats this id selector as a form with default widget options
  {selector: '.dynamic-form-wrapper', options: {mode: 'formSubmit'}}, // treats this class selector as a form with formSubmit mode
  {selector: '[data-form-type="custom"]', options: {mode: 'ajax', email: {block_free_account: true}}} // treats this data-form-type attribute selector as a form with ajax mode and blocks free email accounts
];
```

### **Pre-filled Value Validation**&#x20;

The **window.clearout.options.prefill\_validation** option enables validation of pre-filled values in form fields. This is useful when forms are pre-populated with data and you want to validate these values immediately.

```javascript
window.clearout.options.prefill_validation = true;
```

### **Built-in Error Message Suppression**&#x20;

The **window.clearout.options.suppress\_form\_builtin\_error\_message\_selector** option allows you to specify selectors for form elements whose built-in error messages should be suppressed. This helps prevent duplicate error messages when using Clearout's validation.

```javascript
window.clearout.options.suppress_form_builtin_error_message_selector = '.form-error-message, .validation-message';
```

### **Phone Field Overlay**&#x20;

The **window.clearout.options.phone.overlay** option enables Clearout to create an enriched phone UI component over your form's existing phone field. This provides enhanced validation and formatting capabilities.

```javascript
window.clearout.options.phone.overlay = true;
```

### **Form Discovery**&#x20;

The form discovery options allow you to configure the duration and interval for form discovery. This is useful when you have forms that are dynamically loaded on the page.

```javascript
window.clearout.options.form_discovery_duration = 15000; // Max allowed time in millseconds to discover forms on page, set to -1 for infinite
window.clearout.options.form_discovery_interval = 500; // Interval time in milliseconds between form discovery attempts
```

## Disabling Validation on Particular Fields&#x20;

In some cases, you may want to exclude certain fields from Clearout's validation. This is particularly useful when you have duplicate fields (like email and confirm email) where validating both fields would be redundant.

To disable validation on a specific field, simply add the **data-clearout-validation-disable** attribute to the field element. The Form Guard will automatically ignore any fields with this attribute.

```html
<form id="signup-form">
  <input type="email" name="email" placeholder="Enter your email">
  <input type="email" name="confirm_email" placeholder="Confirm your email" data-clearout-validation-disable>
  <button type="submit">Sign Up</button>
</form>
```

**Note**: This attribute is particularly useful for

* Confirm email fields
* Hidden fields that don't require validation
* Fields that are handled by other validation systems
* Fields that are temporarily disabled or read-only

## Disabling Validation on Particular Form&#x20;

In some cases, you may want to exclude validation for a specific form on the page.&#x20;

To disable validation on a specific form, simply add the **data-clearout-form-identifier=false** attribute to the \<FORM/> element. The Form Guard will automatically ignore the form with this attribute.

## Available Options&#x20;

Here are all the configurable options available in the Clearout FormGuard:

```javascript
window.clearout.options = {
  api_url: config.API_URL,
  timeout: 10,
  mode: 'ajax',

  on_ready: null,
  form_elements: [], // changed
  suppress_form_builtin_error_message_selector: null,

  submit_button_cursor_style: 'pointer',
  submit_button_selector: null,

  auto_validation: true,
  prefill_validation: false,

  bot_detection: {
     enabled: false, // Boolean type - whether bot detection need to be performed during validation
     provider:null,  // String type - provider can be either Google reCaptcha or Cloudflare Turnstile
     data: null      // Object type - object to hold provider specific keys
   },

  feedback_google_recaptcha: 'Google Recaptcha Verification Failed',
  feedback_cloudflare_turnstile: 'Bot Validation Failed, Please refresh the page',

  inspect: false,
  debug: false,

  email: {
    elements: [],
    enabled: true,

    allow_safe_to_send_yes: false, // changed

    block_role_account: false,
    block_free_account: false,
    block_disposable_account: true,
    block_unknown_status: false,
    block_catchall_status: false,
    block_gibberish_account: false,
    block_form_submission_on_timeout: false,
    block_form_submission_on_limit_crossed: false,

    feedback: true,
    optional: false,
    selector: null,

    on_before_verify: null,
    on_after_verify: null,

    suggest_email: false,
    suggest_email_message_template: 'Did you mean __SUGGESTED_EMAIL_ADDRESS__?',

    feedback_invalid_classname: 'co-error-msg',
    feedback_invalid_message: 'Invalid email address',
    feedback_role_account_message: 'Invalid - Role account not allowed',
    feedback_free_account_message: 'Invalid - Free account not allowed',
    feedback_disposable_account_message: 'Invalid - Disposable account not allowed',
    feedback_unknown_message: 'Unable to verify the email address, try after sometime',
    feedback_catchall_message: 'Catch All email not acceptable, please enter a different email address',
    feedback_gibberish_message: 'Invalid - Gibberish email address not allowed',
    feedback_safe_to_send_only_message: 'Please enter different email, entered email is not safe',
    feedback_on_timeout_message: 'Email could not be verified - timeout occurred',
    feedback_on_usage_limit_crossed_message: 'Unable to verify the email address, usage limit crossed',
  },

  phone: {
    elements: [],
    enabled: false,

    block_mobile_numbers: false,
    block_landline_numbers: false,
    block_toll_free_numbers: false,
    block_voip_numbers: false,
    block_unknown_type: false,
    block_form_submission_on_timeout: false,
    block_form_submission_on_limit_crossed: false,
    allowed_countries: [],
    prefill_dial_code: false,

    selector: null,
    optional: false,

    on_before_verify: null,
    on_after_verify: null,

    feedback: true,
    feedback_invalid_message: 'Invalid phone number',
    feedback_invalid_classname: 'co-phone-error-msg',
    feedback_mobile_message: 'Invalid - Mobile numbers not allowed',
    feedback_landline_message: 'Invalid - Landline numbers Not allowed',
    feedback_toll_free_message: 'Invalid - Toll Free numbers not allowed',
    feedback_voip_message: 'Invalid - VOIP numbers not allowed',
    feedback_unknown_message: 'Invalid - Unknown numbers not allowed',
    feedback_on_timeout_message: 'Phone Number could not be verified - timeout occurred',
    feedback_on_usage_limit_crossed_message: 'Unable to verify the phone number, usage limit crossed',
  },

  name: {
    elements: [],
    enabled: false,
    gibberish_threshold: 'high',

    block_gibberish_name: true,
    block_profanity_words: true,
    block_form_submission_on_timeout: false,
    block_form_submission_on_limit_crossed: false,

    selector: null,
    optional: false,
    on_before_verify: null,
    on_after_verify: null,

    feedback: true,
    feedback_invalid_message: 'Invalid name',
    feedback_invalid_classname: 'co-name-error-msg',
    feedback_gibberish_message: 'Invalid - Gibberish name not allowed',
    feedback_profanity_message: 'Invalid - Profanity words are not allowed',
    feedback_on_timeout_message: 'Name could not be verified - timeout occurred',
    feedback_on_usage_limit_crossed_message: 'Unable to verify the Name, usage limit crossed',
  }
}
```

Search:

<table><thead><tr><th width="101.7890625">Field</th><th width="184.03515625">Setting</th><th width="114.046875">Type</th><th width="127.8515625">Default Value</th><th>Description</th></tr></thead><tbody><tr><td>email</td><td>block_catchall_status</td><td>Boolean</td><td>false</td><td>Boolean to block form submission for emails with a catch-all status, where the mailbox accepts all addresses regardless of validity.</td></tr><tr><td>email</td><td>block_disposable_account</td><td>Boolean</td><td>true</td><td>Boolean to block form submission if the email is from a disposable or temporary email provider</td></tr><tr><td>email</td><td>block_form_submission_on_limit_crossed</td><td>Boolean</td><td>false</td><td>Boolean to block form submission when your app’s email validation usage limit has been exceeded.</td></tr><tr><td>email</td><td>block_form_submission_on_timeout</td><td>Boolean</td><td>false</td><td>Boolean to block form submission if the email validation request times out</td></tr><tr><td>email</td><td>block_free_account</td><td>Boolean</td><td>false</td><td>Boolean to block form submission for emails from free providers like Gmail, Yahoo, or Outlook.</td></tr><tr><td>email</td><td>block_gibberish_account</td><td>Boolean</td><td>false</td><td>Boolean to block emails identified as gibberish or invalid, preventing submission of nonsensical or fabricated addresses.</td></tr><tr><td>email</td><td>block_role_account</td><td>Boolean</td><td>false</td><td>Boolean to prevent form submission if the email is a role-based address (e.g., admin@, support@, info@)</td></tr><tr><td>email</td><td>block_unknown_status</td><td>Boolean</td><td>false</td><td>Boolean to block form submission if the email status couldn't be determined by Clearout</td></tr><tr><td>email</td><td>elements</td><td>Array</td><td>null</td><td>Allows you to specify an array of email validation configurations, each with a corresponding jQuery selector. This is particularly useful when you have multiple email fields on a page that require different validation rules. Each item in the array defines the selector for the input field and the specific validation settings to apply.</td></tr><tr><td>email</td><td>enabled</td><td>Boolean</td><td>true</td><td>Boolean to enable or disable email validation for the form</td></tr><tr><td>email</td><td>feedback</td><td>Boolean</td><td>true</td><td></td></tr><tr><td>email</td><td>feedback_catchall_message</td><td>HTML String</td><td>catch all email not acceptable, please enter a different email address</td><td>Option to provide a custom HTML string to be displayed when email status is catchall</td></tr><tr><td>email</td><td>feedback_disposable_account_message</td><td>HTML String</td><td>invalid - disposable account not allowed</td><td>Option to provide a custom HTML string to be displayed when disposable account is detected</td></tr><tr><td>email</td><td>feedback_free_account_message</td><td>HTML String</td><td>invalid - role account not allowed</td><td>Option to provide a custom HTML string to be displayed when free account is detected</td></tr><tr><td>email</td><td>feedback_gibberish_message</td><td>HTML String</td><td>invalid - gibberish email address not allowed</td><td>Option to provide a custom HTML string to be displayed when its a classified as a gibberish email</td></tr><tr><td>email</td><td>feedback_invalid_classname</td><td>String</td><td>co-error-msg</td><td>Option to add a custom CSS class to Clearout’s feedback HTML container for styling purposes.</td></tr><tr><td>email</td><td>feedback_invalid_message</td><td>HTML String</td><td>invalid email address</td><td>Option to provide a custom HTML string displayed when an invalid email is detected.</td></tr><tr><td>email</td><td>feedback_on_timeout_message</td><td>HTML String</td><td>email could not be verified - timeout occurred</td><td>Option to provide a custom HTML string to be displayed when validation timeout occurs</td></tr><tr><td>email</td><td>feedback_on_usage_limit_crossed_message</td><td>HTML String</td><td>unable to verify the email address, usage limit crossed</td><td>Option to provide a custom HTML string to be displayed when usage limit has crossed on your app</td></tr><tr><td>email</td><td>feedback_role_account_message</td><td>HTML String</td><td>invalid - role account not allowed</td><td>Option to provide a custom HTML string to be displayed when role account is detected</td></tr><tr><td>email</td><td>feedback_safe_to_send_only_message</td><td>HTML String</td><td>please enter different email, entered email is not safe</td><td>Option to provide a custom HTML string to be displayed when the email is not Safe to Send</td></tr><tr><td>email</td><td>feedback_unknown_message</td><td>HTML String</td><td>unable to verify the email address, try after sometime</td><td>Option to provide a custom HTML string to be displayed when unknown email is detected</td></tr><tr><td>email</td><td>on_after_verify</td><td>Function</td><td>null</td><td>Callback function executed immediately after Clearout’s validation completes, useful for handling post-validation actions.</td></tr><tr><td>email</td><td>on_before_verify</td><td>Function</td><td>null</td><td>Callback function executed immediately before Clearout’s validation starts, useful for performing pre-validation logic.</td></tr><tr><td>email</td><td>optional</td><td>Boolean</td><td>false</td><td>Boolean indicating if the email field is optional; when true, empty values are accepted and skipped during validation.</td></tr><tr><td>email</td><td>safe_to_send_only</td><td>Boolean</td><td>false</td><td>A super status option that allows only emails classified as “safe to send.” This is the strictest setting and overrides all other block rules.</td></tr><tr><td>email</td><td>selector</td><td>jQuery selector</td><td>null</td><td>Option to specify a jQuery selector to attach Clearout’s validation. Only needed if Clearout is unable to automatically detect the email field. This explicitly sets the target for validation when automatic detection fails.</td></tr><tr><td>email</td><td>suggest_email</td><td>Boolean</td><td>true</td><td>Boolean to enable displaying suggested corrections for common email typos as an error message.</td></tr><tr><td>email</td><td>suggest_email_message_template</td><td>HTML String</td><td>did you mean __suggested_email_address__?</td><td>Option to provide a custom HTML string for displaying suggested email corrections, where a placeholder is replaced with the suggested email address.</td></tr><tr><td>form</td><td>auto_discovery</td><td>Boolean</td><td>true</td><td>Enables or disables automatic detection and attachment of validation widgets to forms present on the page. When set to true, the widget will scan the DOM and initialize validation on all eligible forms automatically.</td></tr><tr><td>form</td><td>bot_detection</td><td>Object</td><td>bot_detection: { enabled: false, provider: null, data: null }</td><td>Enable bot protection for form submissions. Use Form Guard's automatic detection or an external provider such as Google reCaptcha v3.</td></tr><tr><td>form</td><td>debug</td><td>Boolean</td><td>false</td><td>Enables the generation of debug logs in the browser console. Useful for troubleshooting and monitoring validation behavior during development.</td></tr><tr><td>form</td><td>feedback_cloudflare_turnstile</td><td>HTML String</td><td>bot validation failed, please refresh the page</td><td>Specifies the error message displayed when Clearout Bot validation fails</td></tr><tr><td>form</td><td>feedback_google_recaptcha</td><td>HTML String</td><td>google recaptcha verification failed</td><td>Specifies the error message displayed when Google reCAPTCHA validation fails</td></tr><tr><td>form</td><td>form_discovery_duration</td><td>Number</td><td>15000</td><td>Specifies the maximum duration (in milliseconds) allowed for scanning the page to discover and attach validation to forms. Set to -1 to enable unlimited scanning time. -1 for infinite</td></tr><tr><td>form</td><td>form_discovery_interval</td><td>Number</td><td>500</td><td>Defines the time interval (in milliseconds) between consecutive scans of the page for form discovery and attachment.</td></tr><tr><td>form</td><td>form_elements</td><td>Array</td><td>null</td><td>Allows manual specification of one or more form elements to which the validation widget should be attached. This is especially useful for non-standard forms, such as those constructed with &#x3C;div> containers instead of &#x3C;form> tags. Additionally, this option supports applying different validation settings to multiple forms on the same page by associating each form element with its own configuration.</td></tr><tr><td>form</td><td>inspect</td><td>Boolean</td><td>false</td><td>options to allow visual highlighting of input fields that have validation rules attached</td></tr><tr><td>form</td><td>mode</td><td>String</td><td>ajax</td><td>Defines the validation trigger mode. By default, validation is performed when an input field loses focus (onBlur). Setting this to formSubmit will defer validation until the form's submit button is clicked, at which point all eligible fields will be validated. ajax formSubmit</td></tr><tr><td>form</td><td>on_ready</td><td>Function</td><td>null</td><td>Defines a callback function to be executed once the widget has fully loaded and is ready on the page. Use this to perform any initialization or custom logic after the widget becomes available. function() {}</td></tr><tr><td>form</td><td>prefill_validation</td><td>Boolean</td><td>false</td><td>Determines whether validation should be performed on pre-filled form fields when the widget initializes. When enabled, existing input values are validated immediately upon page load.</td></tr><tr><td>form</td><td>submit_button_cursor_style</td><td>String</td><td>pointer</td><td>Specifies the CSS cursor style to apply to the submit button. If not provided, the widget will inherit the cursor style defined by the form's existing styles.</td></tr><tr><td>form</td><td>submit_button_selector</td><td>jQuery selector</td><td>null</td><td>Specifies a jQuery selector for the form’s submit button. This is useful in cases where the widget cannot automatically identify the correct submit button.</td></tr><tr><td>form</td><td>suppress_form_builtin_error_message_selector</td><td>jQuery selector</td><td>null</td><td>option to supress form's built in error msg (used in hs)</td></tr><tr><td>form</td><td>timeout</td><td>Number</td><td>10</td><td>Specifies the maximum duration (in seconds) allowed for validation to complete. If validation exceeds this time limit, the entry will be permitted by default—unless the block_on_timeout setting is enabled. Max 180</td></tr><tr><td>form</td><td>trigger_form_discovery_on_event</td><td>String</td><td>null</td><td>event to listen to before loading the SDKSpecifies the name of an event to listen for before initiating form discovery on the page. Form scanning and validation attachment will start only after this event is triggered.</td></tr><tr><td>name</td><td>block_form_submission_on_limit_crossed</td><td>Boolean</td><td>false</td><td>Boolean to block form submission when your app’s email validation usage limit has been exceeded.</td></tr><tr><td>name</td><td>block_form_submission_on_timeout</td><td>Boolean</td><td>false</td><td>Boolean to block form submission if the email validation request times out</td></tr><tr><td>name</td><td>block_gibberish_name</td><td>Boolean</td><td>true</td><td>Boolean to allow or block names classified as gibberish by Clearout.</td></tr><tr><td>name</td><td>block_profanity_words</td><td>Boolean</td><td>true</td><td>Boolean to allow or block names containing words of profanity</td></tr><tr><td>name</td><td>elements</td><td>Array</td><td>null</td><td>Allows you to specify an array of name validation configurations, each with a corresponding jQuery selector. This is especially useful when multiple name fields on a form require different validation rules. Each item in the array defines the selector for the input field and the specific validation settings to apply.</td></tr><tr><td>name</td><td>enabled</td><td>Boolean</td><td>false</td><td>Boolean to enable or disable name validation for the form</td></tr><tr><td>name</td><td>feedback</td><td>Boolean</td><td>true</td><td></td></tr><tr><td>name</td><td>feedback_gibberish_message</td><td>HTML String</td><td>invalid - gibberish name not allowed</td><td>Option to provide a custom HTML string displayed when an gibberish name is detected.</td></tr><tr><td>name</td><td>feedback_profanity_message</td><td>HTML String</td><td>Invalid - Profanity words are not allowed</td><td>Option to provide a custom HTML string displayed when a profanity word is detected</td></tr><tr><td>name</td><td>feedback_invalid_classname</td><td>HTML String</td><td>co-name-error-msg</td><td>Option to add a custom CSS class to Clearout’s feedback HTML container for styling purposes.</td></tr><tr><td>name</td><td>feedback_invalid_message</td><td>HTML String</td><td>invalid name</td><td>Option to provide a custom HTML string displayed when an invalid name is detected.</td></tr><tr><td>name</td><td>feedback_on_timeout_message</td><td>HTML String</td><td>name could not be verified - timeout occurred</td><td>Option to provide a custom HTML string to be displayed when validation timeout occurs</td></tr><tr><td>name</td><td>feedback_on_usage_limit_crossed_message</td><td>HTML String</td><td>unable to verify the name, usage limit crossed</td><td>Option to provide a custom HTML string to be displayed when usage limit has crossed on your app</td></tr><tr><td>name</td><td>gibberish_threshold</td><td>String</td><td>high</td><td>Defines the strictness level for gibberish detection, allowing adjustment of how aggressively invalid or nonsensical names are filtered.</td></tr><tr><td>name</td><td>on_after_verify</td><td>Function</td><td>null</td><td>Callback function executed immediately after Clearout’s validation completes, useful for handling post-validation actions.</td></tr><tr><td>name</td><td>on_before_verify</td><td>Function</td><td>null</td><td>Callback function executed immediately before Clearout’s validation starts, useful for performing pre-validation logic.</td></tr><tr><td>name</td><td>optional</td><td>Boolean</td><td>false</td><td>Boolean indicating if the email field is optional; when true, empty values are accepted and skipped during validation.</td></tr><tr><td>name</td><td>selector</td><td>jQuery selector</td><td>null</td><td>Option to specify a jQuery selector to attach Clearout’s validation. Only needed if Clearout is unable to automatically detect the name field. This explicitly sets the target for validation when automatic detection fails.</td></tr><tr><td>phone</td><td>allowed_countries</td><td>Array</td><td>[]</td><td>Option to accept phone numbers from certain countries only.</td></tr><tr><td>phone</td><td>block_form_submission_on_limit_crossed</td><td>Boolean</td><td>false</td><td>Boolean to block form submission when your app’s email validation usage limit has been exceeded.</td></tr><tr><td>phone</td><td>block_form_submission_on_timeout</td><td>Boolean</td><td>false</td><td>Boolean to block form submission if the email validation request times out</td></tr><tr><td>phone</td><td>block_landline_numbers</td><td>Boolean</td><td>false</td><td>Boolean to block landline phone numbers from being submitted through the form.</td></tr><tr><td>phone</td><td>block_mobile_numbers</td><td>Boolean</td><td>false</td><td>Boolean to block landline mobilenumbers from being submitted through the form.</td></tr><tr><td>phone</td><td>block_toll_free_numbers</td><td>Boolean</td><td>false</td><td>Boolean to block toll-freephone numbers from being submitted through the form.</td></tr><tr><td>phone</td><td>block_unknown_type</td><td>Boolean</td><td>false</td><td>Boolean to block unknown phone numbers from being submitted through the form.</td></tr><tr><td>phone</td><td>block_voip_numbers</td><td>Boolean</td><td>false</td><td>Boolean to block voip phone numbers from being submitted through the form.</td></tr><tr><td>phone</td><td>elements</td><td>Array</td><td>null</td><td>Allows you to specify an array of phone validation configurations, each with a corresponding jQuery selector. This is especially useful when multiple phone fields on a form require different validation rules. Each item in the array defines the selector for the input field and the specific validation settings to apply.</td></tr><tr><td>phone</td><td>enabled</td><td>Boolean</td><td>false</td><td>Boolean to enable or disable phone validation for the form</td></tr><tr><td>phone</td><td>feedback</td><td>Boolean</td><td>true</td><td></td></tr><tr><td>phone</td><td>feedback_invalid_classname</td><td>String</td><td>co-phone-error-msg</td><td>Option to add a custom CSS class to Clearout’s feedback HTML container for styling purposes.</td></tr><tr><td>phone</td><td>feedback_invalid_message</td><td>HTML String</td><td>invalid phone number</td><td>Option to provide a custom HTML string displayed when an invalid phone is detected.</td></tr><tr><td>phone</td><td>feedback_landline_message</td><td>HTML String</td><td>invalid - landline numbers not allowed</td><td>Option to provide a custom HTML string displayed when a landline phone is detected.</td></tr><tr><td>phone</td><td>feedback_mobile_message</td><td>HTML String</td><td>invalid - mobile numbers not allowed</td><td>Option to provide a custom HTML string displayed when an mobile phone is entered</td></tr><tr><td>phone</td><td>feedback_on_timeout_message</td><td>HTML String</td><td>phone number could not be verified - timeout occurred</td><td>Option to provide a custom HTML string to be displayed when validation timeout occurs</td></tr><tr><td>phone</td><td>feedback_on_usage_limit_crossed_message</td><td>HTML String</td><td>unable to verify the phone number, usage limit crossed</td><td>Option to provide a custom HTML string to be displayed when usage limit has crossed on your app</td></tr><tr><td>phone</td><td>feedback_toll_free_message</td><td>HTML String</td><td>invalid - toll free numbers not allowed</td><td>Option to provide a custom HTML string displayed when an toll-free phone is detected.</td></tr><tr><td>phone</td><td>feedback_unknown_message</td><td>HTML String</td><td>invalid - unknown numbers not allowed</td><td>Option to provide a custom HTML string displayed when phone number's status could not be determined</td></tr><tr><td>phone</td><td>feedback_voip_message</td><td>HTML String</td><td>invalid - voip numbers not allowed</td><td>Option to provide a custom HTML string displayed when an voip phone is detected.</td></tr><tr><td>phone</td><td>on_after_verify</td><td>Function</td><td>null</td><td>Callback function executed immediately after Clearout’s validation completes, useful for handling post-validation actions.</td></tr><tr><td>phone</td><td>on_before_verify</td><td>Function</td><td>null</td><td>Callback function executed immediately before Clearout’s validation starts, useful for performing pre-validation logic.</td></tr><tr><td>phone</td><td>optional</td><td>Boolean</td><td>false</td><td>Boolean indicating if the email field is optional; when true, empty values are accepted and skipped during validation.</td></tr><tr><td>phone</td><td>overlay</td><td>Boolean</td><td>false</td><td>Experimental: Option to enable Clearout’s enriched phone overlay on existing phone input fields with a country code dropdown. Enhances the user experience with formatting and validation support.</td></tr><tr><td>phone</td><td>prefill_dial_code</td><td>Boolean</td><td>false</td><td>Option to automatically add dial code (eg: +1) to phone number based on page visitor's location.</td></tr><tr><td>phone</td><td>selector</td><td>jQuery selector</td><td>null</td><td>Option to specify a jQuery selector to attach Clearout’s validation. Only needed if Clearout is unable to automatically detect the phone field. This explicitly sets the target for validation when automatic detection fails.</td></tr></tbody></table>

## Customizing Styles and CSS&#x20;

All UI components created by the **Clearout Form Guard** come with properly **namespaced CSS classes**, making it easy to target and customize their appearance using your own styles.

Below is a list of all elements and their associated class names:

* **co-input-container**: This is the main wrapper div, which is wrapped around the respective input container.
* **co-loader-container**: This is the loader container, which is placed on top of the container.
* **co-loader-img-container**: This is the loader image's container, which basically contains the tick, cross, or the loader.
* **co-feedback-container**: This is the container that contains the feedback elements and is positioned just below the input container.
* **co-feedback-msg**: This is the container containing the actual feedback message.

## Using the Validators&#x20;

All of Clearout's built-in **validators** are exposed under the global window.clearout object. This allows advanced users to **directly** **access** **and** **invoke** **the** **verify** **method** of each validator, enabling deeper integration or custom validation logic in your application.

For example, you can manually trigger a validation like this:

```javascript
let emailValidationResponse = await window.clearout.emailValidator.verify({ email: 'us@clearout.io' })
console.log('Email Validation Response: ', emailValidationResponse.result)

let phoneValidationResponse = await window.clearout.phoneValidator.verify({ phone: '+918220154838' })
console.log('Phone Validation Response: ', phoneValidationResponse.result)

let nameValidationResponse = await window.clearout.nameValidator.verify({ name: 'Nishanth Babu' })
console.log('Name Validation Response: ', nameValidationResponse.result)
```

Using these exposed validation methods, you can verify the data in runtime alongside your client side logics to determine the status of data points at any point in your workflows.

## Using the Form Component&#x20;

To manually attach the Clearout Form Guard to specific forms using the SDK, you can use the globally available **FormValidator** class. This allows you to create an instance of the widget directly on a jQuery form object, offering precise control over which forms are initialized and how.

You can do this by instantiating **FormValidator** with two parameters: the jQuery form object and a custom options object. These options can either be inherited from the globally available **window.clearout.options** or fully customized as per your requirements.

```javascript
new window.clearout.FormValidator(clearout.$('#testform'), clearout.options)
```

## Form Guard Callback Hooks&#x20;

The Clearout Form Guard currently supports three types of callback hooks that allow you to extend and customize the validation process:

* **on\_ready**\
  Triggered when the Clearout JS SDK is fully loaded and initialized on the page.
* **on\_before\_verify**\
  Triggered just before the input data is sent to Clearout for validation.
* **on\_after\_verify**\
  Triggered immediately after Clearout returns the validation response.

> Note: The <mark style="color:$info;">on\_before\_verify</mark> and <mark style="color:$info;">on\_after\_verify</mark> hooks are field-specific and are individually available for email, phone, and name validations. This allows you to apply fine-grained logic tailored to each input type.

### **on\_ready hook**&#x20;

The on\_ready hook is executed once the Clearout Form Guard SDK has fully loaded and initialized on the page. This hook is particularly useful for running initialization logic that needs to execute once the Form Guard is ready.

**Common use cases include:**

* Applying custom CSS or styling to Form Guard elements
* Adding specific data attributes to input fields
* Running setup scripts that depend on the Form Guard being initialized

This callback guarantees that all globally scoped variables—such as validators and configuration options—are accessible and fully initialized, ensuring a safe point to begin custom interactions with the widget.

### **on\_before\_verify hook**&#x20;

The **on\_before\_verify** hook is triggered just before the field data is sent to Clearout for validation. This hook is ideal for performing custom pre-validation checks on the input data.

**Function Parameters**

The callback receives a destructured object:

* **email, phone, or name**: The actual value being entered in the field
* <mark style="color:$info;">**$form**</mark>: The jQuery-wrapped form element

The Function is expected to return an object with is\_acceptable (true/false) and an error\_msg string. If **is\_acceptable** is set to **false**, the field will not be submitted, and the provided **error\_msg** will be displayed to the user.

This gives you complete control to add pre-checks or filters before Clearout runs its own verification logic.

```javascript
function ({ email, $form }) {
  let is_acceptable = true
  let error_msg = null
  console.log('Debug: OnBeforeVerify hook is called: ', { email, $form })

  // Your Logic goes here
  // a simple account length check
  let acctName = email.split('@')[0]
  if (acctName.length > 25) {
    is_acceptable = false
    error_msg = 'Email is too long! pls try a shorter email.'
  }
  return ({ is_acceptable, error_msg })
}
```

### **on\_after\_verify hook**&#x20;

The **on\_after\_verify** hook is triggered after Clearout returns a response for the field's validation. This hook is particularly useful for performing any post-verification checks, triggering workflows, or making UI changes based on the validation outcome.

**Function Parameters**&#x20;

The callback receives a destructured object:

* **email, phone, or name**: The actual value being entered in the field
* **$form**: The jQuery-wrapped form element
* **result**: The verification response

The Function is expected to return an object with is\_acceptable (true/false) and an error\_msg string. If **is\_acceptable** is set to **false**, the field will **not be submitted**, and the provided **error\_msg** will be displayed to the user.

This gives you complete control to add **post-checks or filters** after Clearout runs its own verification logic.

```javascript
function ({ phone, $form, result }) {
  let is_acceptable = true
  let error_msg = null
  console.log('Debug: OnBeforeVerify hook is called: ', { phone, $form, result })

  // Your Logic goes here
  // A Sample logic to determine the length of phone number
  if (phone.length !== 10) {
    error_msg = 'Invalid Phone number not allowed!'
    is_acceptable = false
  }
  return ({ is_acceptable, error_msg })
}
```

---
description: Real-time Email Validation on Forms (Deprecated; use Form Guard)
---

# JavaScript Widget

The Clearout JavaScript Widget comes in handy for non-developers to easily integrate real-time verification into all kinds of online forms. This will let a user capture all valid prospects right at the time of form filling, avoiding the loss of any opportunity

{% hint style="info" %}
<mark style="color:$info;">**Important note**</mark>

<mark style="color:red;">The JavaScript Widget is no longer supported</mark>. We recommend using [Form Guard](/broken/pages/rXGOw2nHnrFS098BfLhM) for best features and support
{% endhint %}

## JavaScript Widget 2.0 - Live Demos

**Clearout** **JavaScript widget** comes as a simple way to bring real-time email address verification to any online forms that capture the email addresses. The widget can be configured to handle what kind of email address is to be considered valid. Below page link shows how the Clearout JavaScript widget has enhanced the **HubSpot, Unbounce, and LeadPages** forms to capture only the leads with the valid email address

<table><thead><tr><th width="369.69921875">Form Provider + JavaScript Widget 2.0</th><th>Live Demo Page</th><th data-hidden></th></tr></thead><tbody><tr><td>HubSpot</td><td><a href="https://clearout.io/formguard/v2/demos/hubspot.html">Try it</a></td><td>HubSpot</td></tr><tr><td>Unbounce</td><td><a href="https://clearout.io/formguard/v2/demos/unbounce.html">Try it</a></td><td>Unbounce</td></tr><tr><td>Lead Pages</td><td><a href="https://clearout.io/formguard/v2/demos/leadpages.html">Try it</a></td><td>Lead Pages</td></tr></tbody></table>

## Getting Started with JavaScript Widget

Create your JavaScript widget from the Apps page by clicking on 'Create App' and by choosing run type as 'Client.' When creating Clearout Apps, you'll need to choose how and where to validate. This helps prevent the mishandling of credits and abuse by setting access thresholds across domains, URLs, and/or IPs.

{% hint style="info" %}
The app screenshots illustrated on this page may be irrelevant due to the fact that the JavaScript Widget has been deprecated and is no longer supported.
{% endhint %}

## Security Configuration:

{% stepper %}
{% step %}
#### Limit Usage:

You can take full control in avoiding abuse by limiting the usage by applying a rate limit on IP addresses. This will further help in using the credits effectively. It is always advisable to specify a rate limit either at a global level or at a minute interval. Failing to do so might deplete the credit balance sooner. There will be no limits applied by default.
{% endstep %}

{% step %}
#### Add URLs:

You can prevent abuse by adding URLs that restrict where email verification is permitted on the website. By the way, URLs can contain wildcards to specify whether verification should be performed on the entire website or a subset of websites, as shown in the image below.
{% endstep %}
{% endstepper %}

## Get your JavaScript Widget up and working:

Once the client-side app is created, you will be given a code snippet with the corresponding API token that needs to be inserted anywhere before the closing body tag. Upon saving the snippet as a component of the form, the client-side app begins verifying the emails.

```javascript
<script>
  var clearout = window.clearout = window.clearout || [],
  opts = {
    app_token: "REPLACE_WITH_YOUR_CLIENT_APP_TOKEN",
    mode: "ajax",
    block_role_account: true,
    feedback_role_account_message: "Don't use a role-based account, please",
  };
  clearout.push(["initialize", opts]),
      function () {
        var t = document,
          e = t.createElement("script"),
          a = t.getElementsByTagName("script")[0];
        e.type = "text/javascript", e.async = !0,
        e.src = "https://clearout.io/wp-content/co-js-widget/clearout_js_widget.js",
        a.parentNode.insertBefore(e, a)
      }();
</script>
```

With the mentioned snippet's basic settings, you can capture the valid business email addresses. In case you wanted to accept free accounts or other such accounts, you can make use of the advanced settings.

> <mark style="color:$info;">**Things to remember**</mark>
>
> * In case the account used to generate the app token runs out of credits, the form submissions will be allowed without email validation
> * In case of throttle limits are exceeded, the form submissions will be allowed without email validation

## Advanced Settings:

Once the code snippet is generated, you can specify the settings for the widget against the 'opts'. Initially, the code snippet only contains 'app\_token', which is the user identifier, and 'mode', which is configured to ajax by default. These settings are enough to make the widget work. You can configure the additional settings as follows;

{% code fullWidth="false" expandable="true" %}
```javascript
<script type="text/javascript">
    var clearout = window.clearout = window.clearout || [];
    var opts = {

        app_token: YOUR_CLIENT_APP_TOKEN,
        /**
          *Replace 'YOUR_CLIENT_APP_TOKEN' with your public token
          */

        safe_to_send_only: false,
        /**
          *The option to block the emails that Clearout verification returns safe_to_send as false -
          *default is 'false'
          *This option Supersedes every other block settings
          */

        optional_email: false,
        /**
          *Setting this option to 'true' allows form submission with empty email field value,
          *however any non-empty value will undergo validation - default is 'false'
        */

        block_role_account: true,
        /**
          *The option to accept or reject the Role based accounts (true/false) - default is 'false'
          */

        block_free_account: true,
        /**
          *The option to block Free accounts (true/false) - default is 'false'
          */

        block_disposable_account: true,
        /**
          *The option to block Disposable accounts (true/false) - default is 'true'
          */

        block_unknown_status: false,
        /**
          *The option to block the emails that Clearout verification gives Unknown result (true/false) -
          *default is 'false'
          */

        block_catchall_status: false,
        /**
          *The option to block the emails that Clearout verification gives Catchall result (true/false) -
          *default is 'false'
          */

        block_gibberish_account: false,
        /**
          *The option to block the emails that Clearout verification classifies as gibberish -
          *default is 'false'
          */

        block_form_submission_on_timeout: false,
        /**
          *The option to block the emails that timedout during the verification process -
          *default is 'false'
          */

        block_form_submission_on_limit_crossed: false,
        /**
          *The option to block the emails that are not validated by clearout after the usage limit has crossed -
          *default is 'false'
          */

        timeout: 10,
        /**
          *The option to define the maximum time that can be used for verifying the status of the given email address (Number in Seconds)
          */

        feedback: true,
        /**
          *The option to show feedback message for invalid emails (true/false)—the default is 'true'
          */

        feedback_invalid_classname: "error-msg",
        /**
          * The option to specify the class name to refer invalid CSS (String)—the default is 'error-msg'
          */

feedback_invalid_message: "<span style=\"color:red;font-size:15px;\">Invalid email address,"
        /**
          * The option to specify the HTML String to be displayed when invalid email is entered -  default is "Invalid email address."
          */

        feedback_free_account_message: "Invalid - <b>Free account</b> not allowed",
        /**
          *The option to specify the HTML String to be displayed when free account email is entered—the default is "Invalid Free account not allowed."
          */

        feedback_role_account_message: "Invalid - Role account not allowed",
        /**
          *The option to specify the HTML String to be displayed when role based email is entered - default is "Invalid—Role account not allowed."
          */

        feedback_disposable_account_message: "Invalid - Disposable account not allowed",
        /**
          *The option to specify the HTML String to be displayed when Disposable email is entered - default is "Invalid—Disposable account not allowed"
          */

        feedback_unknown_message: "Unable to verify the email address, try after sometime",
        /**
          *The option to specify the HTML String to be displayed when Clearout gives Unknown status post verification default is "Unable to verify the email address, try after sometime"
          */

        feedback_catchall_message: "Catch All email not acceptable, please enter a different email address",
        /**
          * The option to specify the HTML String to be displayed when Clearout gives Catchall status post verification—the default is "Catch All email not acceptable, please enter a different email address"
          */

        feedback_safe_to_send_only_message: "Please enter different email, entered email is not safe",
        /**
          * The option to specify the HTML String to be displayed when a non safe to send email is entered—the default is "Please enter different email, entered email is not safe"
          */

        feedback_gibberish_message: "Invalid—Gibberish email address not allowed,"
        /**
          * The option to specify the HTML String to be displayed when a gibberish email is entered—the default is "Invalid—Gibberish email address not allowed."
          */

        feedback_google_recaptcha: "Google Recaptcha Verification Failed",
        /**
          * The option to specify the HTML String to be displayed when Google Recaptcha verification fails—the default is "Google Recaptcha Verification Failed"
          */

feedback_on_timeout_message: "Email could not be verified - timeout occured",
        /**
* The option to specify the HTML string to be displayed when email verification times out—the default is "Email could not be verified—timeout occurred."
          */

        feedback_on_usage_limit_crossed_message: "Email could not be verified—usage limit crossed,"
        /**
          * The option to specify the HTML String to be displayed when usage limits have crossed—the default is "Email could not be verified - usage limit crossed"
          */

        mode: "ajax",
        /**
          *The option to specify the desired mode of verification (ajax/formSubmit) - default is "ajax"
          */

        selector: "user_email",
        /**
          *The option to specify the email field using specified selector for which verification should happen (classname eg: user_email)—the default is empty
          */

        submit_button_selector: '.submit-btn',
        /**
          * The option to specify any valid jquery selector for a submit button to use with formSubmit mode—default is empty
          */

        debug: true,
        /**
          *The option to specify debug console (true/false)—the default is 'true.'
          */

        elements: [{selector: 'ANY SELECTOR', opts: 'ANY OF THE ABOVE MENTIONED OPTIONS'}],
        /**
          *This block can be used to `configure any element in the form specifying the selector and the equivalent options as an array—the default is empty array
          */

        inspect: true
        /**
          * The option to specify if the field getting verified needs to be highlighted with a border or not defaults to 'false.'
          */

        on_before_verify: <function>,
        /**
* Use this option to pre-hook into the email validation workflow, this callback function will be called with the email and the form object parameters before the control pass to the Clearout validation, so it's the best place to do sanitization or bring your own validation. By returning false to this callback function, you will stop triggering. Clearout validation

* Example:
          * on_before_verify: function({ email, $form }){
          *   // custom code
          *   // return true or false
          * }
          */

        on_after_verify: <function>,
        /**
          *  Use this option to post-hook into email validation workflow, this callback function will be called with the email and the form object parameters after successful execution of Clearout validation along with result, so it's the best place to trigger or filter any further operation based on the validation result such as customizing UI or messages or stopping form submission based on result status by returning false

* Example:
          * on_after_verify: function({ result, $form }){
          *   // custom code
          *   // return true or false
          * }
          */

        recaptcha_site_key: <GOOGLE_RECAPTCHA_V3_SITE_KEY>,
        /**
          * Option to specify whether to use Google reCAPTCHA (v3) in * order to prevent bot or abuser from the signup forms.
          * <SITE_KEY> needs to be generated and replaced in the above option.
          */

        auto_validation: true,
       /**
          * Option to auto detect the email text field in the forms, setting 'false' won't detect email fields automatically provide a way to specify explicitly - default is 'true'
          */

        on_ready: <function>,
        /**
          * Use this option to attach Clearout validation to the custom forms, most probably this will used when 'auto_validation' option set to false
          *Example:
          * on_ready: function(){
          *   // custom code
          * }
          */

        prefill_validation: false,
        /**
          * Option to automatically validate prefilled email fields - default is 'false'
          */

        suggest_email: true,
        /**
          * The option to display a suggested email address if the user's entered email address not valid - default is 'true'
          */

        suggest_email_message_template: 'Did you mean __SUGGESTED_EMAIL_ADDRESS__ ?',
        /**
          * The option to specify the suggested email message template. the placeholder __SUGGESTED_EMAIL_ADDRESS__ will be replaced with the real suggested email - default is 'Did you mean __SUGGESTED_EMAIL_ADDRESS__ ?
          */

        suppress_form_builtin_error_message_selector: '.error-msg',
        /**
          * Use this option to suppress the form's built-in error message by specifying the valid jQuery selector of the form's error message element - default is null
          */

        submit_button_cursor_style: 'pointer',
        /**
          * Use this option to set form's submit button cursor style - default is 'pointer'
          */
      };

      clearout.push(["initialize", opts]),
      function () {
        var t = document,
          e = t.createElement("script"),
          a = t.getElementsByTagName("script")[0];
        e.type = "text/javascript", e.async = !0,
        e.src = "https://clearout.io/wp-content/co-js-widget/clearout_js_widget.js",
        a.parentNode.insertBefore(e, a)
      }();

</script>
```
{% endcode %}

> **Impact of Emails or Domains** [**Allowlist/Blocklist Settings**](https://app.clearout.io/dashboard/settings/email_verifier)
>
> In case of an incoming email address or domain is already part of allowlist or blocklist then the verification outcome will be based on that. Above setting options wont have any impact during the verification.

## reCAPTCHA:

Google reCAPTCHA (v3) helps to prevent hackers from abusing the system, as it blocks bots from submitting fake or nefarious online requests.

### Captchas can be used to

* Protect the integrity of online forms by stopping abusers from sending in repeated false responses
* Prevent abusers from signing up for multiple accounts

So, a captcha with real-time email validation would generate genuine leads. To enable Google reCAPTCHA (v3), you need to generate a site key and a secret key from [Google](https://developers.google.com/recaptcha/docs/v3)

## Adding Email Validation to a Specific Form

In case a page has many forms, and you are looking to enable Clearout email validation to a specific form, then it requires passing the form element as part of the initialization, as mentioned below

{% stepper %}
{% step %}
Find the form element for which the Clearout email validation needs to be added
{% endstep %}

{% step %}
Pass the form element as the third parameter in the **clearout.push()** initialization method

```javascript
<script>
    var clearout = window.clearout = window.clearout || [];
    var opts = {
    app_token: "REPLACE_WITH_YOUR_CLIENT_APP_TOKEN",
    api_url: "https://api.clearout.io",
    }
    var form = document.getElementById('YOUR_FORM_ID');  // Step 1
    clearout.push(["initialize", opts, form]);  // Step 2
    (function () {
      var u = "/";
      var d = document,
        g = d.createElement("script"),
        s = d.getElementsByTagName("script")[0];
      g.type = "text/javascript"; g.async = true;
      g.src = "https://clearout.io/wp-content/co-js-widget/clearout_js_widget.js",
      s.parentNode.insertBefore(g, s);
    })();
</script>
```
{% endstep %}
{% endstepper %}

## Adding Email Validation to Asynchronous or Deferred Form

In case the form on the page is set to be rendered dynamically, then wait for the form element to be available before adding it to the Clearout email validation.

```javascript
<html>
<body>
  <div>
    <!-- page content goes here -->
    <!-- some script to generate form -->

  </div>

  <!-- Initialize Clearout JS Widget -->
  <script>
    var clearout = window.clearout = window.clearout || [];
    var opts = {
      app_token: "REPLACE_WITH_YOUR_CLIENT_APP_TOKEN",
      api_url: "https://api.clearout.io",
      auto_validation: false // STOP ATTACHING VALIDATION AUTOMATICALLY
    };
    clearout.push(["initialize", opts]);
    (function () {
      var u = "/";
      var d = document, g = d.createElement("script"), s = d.getElementsByTagName("script")[0];
      g.type = "text/javascript"; g.async = true;
      g.src = "https://clearout.io/wp-content/co-js-widget/clearout_js_widget.js",
        s.parentNode.insertBefore(g, s);
    })();

    // Wait for form availability and then attach Clearout email validation
    var formSelector = ".myformclassname" // any valid jQuery selector
    var intervalId = setInterval(function () {
      // check jQuery loaded
      if ( typeof window.jQuery === "undefined" ) { return; }

      // jQuery loaded
      if (jQuery(formSelector).length) {
        console.log("Form is available")
        clearInterval(intervalId)
        intervalId = null
        window.clearout.emailValidator.attachToForm({ formSelector })
      }
    }, 500)

  </script>
</body>
</html>
```

## Email Validation on Popup Forms during Form Submission

Most pop-up form providers will render the form dynamically, and even the form submit button would be a custom button created using the \<DIV> tag.

In that case, adding clearout validation to the form requires the mode to be '**formSubmit**' rather than '**ajax**'; also, to handle the custom submit button, it is necessary to take over the button click with a transparent overlay before the actual form submission occurs. The steps below illustrate how to take over the form submit button and then attach validation to the form

{% stepper %}
{% step %}
Switch off the auto-validation mode. Adding Clearout's JS Widget will auto-detect the email fields by default and attach the validation. This can be disabled by setting the 'auto\_validation' option to 'false.'
{% endstep %}

{% step %}
Specify which form & submit button on the page requires validation by setting the form options as mentioned below:

> Please change the option values according to your form setting, since the below values are only for reference.

```javascript
var formOpts = {
    formSelector: ".my-form",
    /** specify form selector - mandatory option */
    submit_button_selector: ".my-form-submit-btn",
    /** specify form submit button - forces formSubmit mode */
    mode: "formSubmit",
    /** either ajax or formSubmit - default ajax */
    submitButtonOverlay: true /** whether to overlay transparent container or not - default true */
}
```
{% endstep %}

{% step %}
Pass the form option (formOpts) to the Cleaout emailValidator service method attachToForm() is part of the widget on\_ready callback, as mentioned below.

```javascript
var coJsWidgetReady = function() {
console.log("Clearout.onReady called...attaching form for validation")
var formOpts = {
    formSelector: ".my-form",
    /** specify form selector - mandatory option */
    submit_button_selector: ".my-form-submit-btn",
    /** specify form submit button - forces formSubmit mode */
    mode: "formSubmit",
    /** either ajax or formSubmit - default ajax */
    submitButtonOverlay: true /** whether to overlay transparent container or not - default true */
  }
  clearout.emailValidator.attachToForm(formOpts)
}
```
{% endstep %}

{% step %}
The final snippet of code would look something like below and needs to be inserted on the page where the form will be rendered.

```javascript
var coJsWidgetReady = function () {
  console.log("Clearout.onReady called...attaching form for validation")
  var formOpts = {
    formSelector: ".my-form",
    /** specify form selector - mandatory option */
    submit_button_selector: ".my-form-submit-btn",
    /** specify form submit button - forces formSubmit mode */
    mode: "formSubmit",
    /** either ajax or formSubmit - default ajax */
    submitButtonOverlay: true/** whether to overlay transparent container or not - default true */
  }
  clearout.emailValidator.attachToForm(formOpts)
}

var clearout = window.clearout = window.clearout || [];
var opts = {
  app_token: 'REPLACE_WITH_YOUR_CLIENT_APP_TOKEN',
  api_url: "https://api.clearout.io",
  auto_validation: false,
  on_ready: coJsWidgetReady
}
clearout.push(["initialize", opts]);
(function () {
  var u = "/";
  var d = document,
    g = d.createElement("script"),
    s = d.getElementsByTagName("script")[0];
  g.type = "text/javascript"; g.async = true;
  g.src = "https://clearout.io/wp-content/co-js-widget/clearout_js_widget.js",
  s.parentNode.insertBefore(g, s);
})();
```
{% endstep %}
{% endstepper %}

> <mark style="color:$info;">**Note**</mark>**:** Please contact us@clearout.io, if none of the above methods help you integrate Clearout email validation on the form

## Integrate custom email validation using the verify() method.

Use the **clearout.emailValidator.verify()** method at your disposal in situations where you need to implement your own form validation with Clearout's real-time email validation for the email field. To find out more about the integration, please take a look at the code example below.

{% code expandable="true" %}
```javascript
<html>
<body>
  <div>
    <!-- page content goes here -->
    <!-- Form goes here -->

  </div>

  <!-- Initialize Clearout JS Widget -->
  <script>
    var clearout = window.clearout = window.clearout || [];
    var opts = {
      app_token: "REPLACE_WITH_YOUR_CLIENT_APP_TOKEN",
      api_url: "https://api.clearout.io",
      auto_validation: false // STOP ATTACHING VALIDATION AUTOMATICALLY
    };
    clearout.push(["initialize", opts]);
    (function () {
      var u = "/";
      var d = document, g = d.createElement("script"), s = d.getElementsByTagName("script")[0];
      g.type = "text/javascript"; g.async = true;
      g.src = "https://clearout.io/wp-content/co-js-widget/clearout_js_widget.js",
        s.parentNode.insertBefore(g, s);
    })();

    // Custom Submit button handler to do validations before submitting form
    $('.submit-btn').on('click', async function(e){
      e.preventDefault()
      <!-- Custom validations and code goes here -->

      // Calling Clearout's Email validation
      let result = await clearout.emailValidator.verify(email, options)
      if (result && result.data && result.data.free === 'yes') {
        <!-- Code to ask user to enter business email -->
      }
    })

  </script>
</body>
</html>
```
{% endcode %}

> **Note:** Please contact us@clearout.io, if none of the above methods help you integrate Clearout email validation on the form

## Customizing Feedback Error Message

If you want to change the error message text or apply the styling, please check all the options that start with feedback, as they are of HTML string type, so feel free to update the text that suits your requirement and use inline HTML style or classname to change the look and feel.

Check out the code snippet and screenshot below to see how the feedback message text and styling have been modified.

```javascript
<script>
  var clearout = window.clearout = window.clearout || [],
  opts = {
    app_token: "REPLACE_WITH_YOUR_CLIENT_APP_TOKEN",
    mode: "ajax",
    block_role_account: true,
    feedback_invalid_message: "<span style=\"color:#f1cb03;font-size:10px;\">Correct your email address ☝</span>",
  };
  clearout.push(["initialize", opts]),
      function () {
        var t = document,
          e = t.createElement("script"),
          a = t.getElementsByTagName("script")[0];
        e.type = "text/javascript", e.async = !0,
        e.src = "https://clearout.io/wp-content/co-js-widget/clearout_js_widget.js",
        a.parentNode.insertBefore(e, a)
      }();
</script>
```

## Activate/Deactivate the apps:

If you want to disable any app temporarily, you can click on the toggle button against the app under the status column. Verification will not be carried out as long as the status of the app remains 'Inactive.' You can resume the verification by turning the toggle to an active state.

## Deleting the unused/old apps:

Any unused app can be deleted by clicking the delete icon against the app. On hovering over the app name, the Delete(Bin Icon) option will be visible.

## Reset/Regenerate the Token:

Whenever an abuse is identified while you are still in control of the usage, you may reset the app token. Resetting any app token provides two options:

* Deactivating the existing token in use. The token will expire immediately (in case of abuse is identified)
* Keep the already active token working for an hour post-resetting (which might be helpful in case of migrating to a newer setup). Once the first hour completes, the old token will not work.

It is always advisable to choose 'Expire Immediately' if any sort of abuse is identified. On successful resetting of the token, make sure to update the form code with the new token.

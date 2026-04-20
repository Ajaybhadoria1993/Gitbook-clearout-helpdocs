---
description: Real-time phone number validation & formatting
icon: phone
---

# Phone Field Validation

The Form Guard provides a **flexible and powerful phone validation component** that allows you to configure how Clearout should validate phone numbers based on your specific requirements. This section covers

## Phone Field Setting Options

The Guard creation or custom code can set the phone field options below.

### Acceptable Values

* **Accept any Valid phone number (default)**: Allows any valid phone number with a valid format
* **Accept only Mobile phone numbers**: Allows only valid mobile phone numbers with a valid format.
* **Accept only Landline phone numbers**: Allows only landline phone numbers with a valid format
* **Custom**: Allows you to set your own custom validation rules for phone numbers
  * **Block Mobile Numbers**: Block mobile phone numbers from being submitted through the form
  * **Block Landline Numbers**: Block landline numbers from being submitted through the form
  * **Block Toll-Free Numbers**: Block toll-free phone numbers from being submitted through the form
  * **Block VOIP Numbers**: Block VOIP phone numbers from being submitted through the form
  * **Block Unknown status**: Block unknown phone numbers from being submitted through the form
  * **Block form submission on timeout**: Block form submission if the phone validation request times out
  * **Block form submission on usage limit crossed**: Block form submission when the phone validation usage limit is exceeded.

### Feedback Messages

This option allows you to customize the feedback (error) messages displayed on forms when an invalid or unacceptable value is entered in the phone field.

* **Default**: A predefined set of feedback messages automatically set by the Form Guard.
* **Custom**: Displays all possible feedback message variations for the phone field (refer to the image below), with their default values shown as placeholder text in the input field.

## Hooks

This option allows you to define custom JavaScript functions that execute either before or after Clearout's form validation.

### **On Before Verify**

This hook is triggered just before Clearout's Phone validation runs. The function receives two destructured parameters as defined below:

* **phone**: The value entered in the respective form field.
* **$form**: The jQuery-wrapped form element.

The function should return an object with is\_acceptable and error\_msg properties. Setting is\_acceptable to false will consider the input value as invalid with the message set on the error\_msg property.

* **is\_acceptable**: The validation status of the On Before Verify hook.
* **error\_msg**: The HTML error message string to be displayed in case of is\_acceptable is false.

```javascript
on_before_verify: function({ phone, $form }) {
  let response = { is_acceptable: true, error_msg: '' };

  // Custom validation logic goes here

  return response;
}
```

### **On After Verify**

This hook is triggered just after Clearout's Phone validation runs and has returned back with Clearout's Validation response. The function receives three destructured params:

* **phone**: The value entered in the respective form field
* **$form**: The jQuery-wrapped form element
* **result**: The Clearout's Validation result object

The function should return an object with is\_acceptable and error\_msg properties. Setting is\_acceptable to false will consider the input value as invalid with the message set on the error\_msg property.

* **is\_acceptable**: The validation status of the On After Verify hook.
* **error\_msg**: The HTML error message string to be displayed in case of is\_acceptable is false.

```javascript
on_after_verify: function({ phone, $form, result }) {
  let response = { is_acceptable: true, error_msg: '' };

  // Custom validation logic goes here
  console.log(result);

  return response;
}
```

## Field Selection

This option lets you choose whether Clearout's Form Guard should automatically detect and attach validation to phone fields or apply validation only to specific fields of your choice.

By default, the **Automatic** mode is enabled, allowing Clearout to identify form fields based on various techniques:

* Element's **type is** of **tel**
* Element's name is equal to any one of **clearout-phone, mobile, phone, telephone, mobilephone**
* Element has attribute **data-clearout-phone-field**

## Allowed Countries

Option to accept phone numbers from certain countries only.

All countries are enabled by default, but you can limit this to specific ones if required.

* **All**: Accept phone numbers from every country.
* **Custom**: Accept phone numbers only from the countries you select. You may choose one or multiple options.

## Prefill Dial Code

This option automatically inserts the appropriate dial code (e.g., +1) into the phone number field based on the visitor’s location.

* **Yes**: Automatically prefill the dial code using the visitor’s location.
* **No**: Do not prefill the dial code.

## Optional Fields

In case the phone input field is set as optional, without requiring the visitor to fill it, then you can set this option to <mark style="color:$info;">**"Yes."**</mark>

**Here's how it works:**

* **If the field is left empty:** The form submission will proceed without validation for that field.
* **If the field is filled**: Even though it's optional, the entered value will be validated. The form will only be allowed to submit if the value passes validation based on your configured criteria.

## Testing

For testing purposes, you can use the [test phone numbers](https://clearoutphone.io/supported-countries/) to verify different validation scenarios without incurring any credit cost. For more details about supported countries and phone number formats, please refer to our [Supported Countries](https://clearoutphone.io/supported-countries/) page.

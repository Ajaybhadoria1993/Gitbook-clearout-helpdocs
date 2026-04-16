---
description: Validate name fields to prevent spam leads
icon: signature
---

# Name Field Validation

The Form Guard provides a **flexible and powerful name validation component** that allows you to configure how Clearout should validate names based on your specific requirements. This section covers the various options available to customize the name validation behavior.

> **Note**: Current Gibberish name detection is based on Markov Chaining detection method and the model has been trained and tested for USA person names. You can control the detection accuracy by [**Gibberish Threshold**](name-field-validation.md#gibberish-threshold) **option**

## Name Field Setting Options&#x20;

Find below the various name field setting options that can be configured as part of the Guard creation or by using the customized code

<div data-with-frame="true"><figure><img src="../.gitbook/assets/name_validation_clearout_formguard.webp" alt="select and customize Name validation settings for Name Field"><figcaption><p>Customize how names are validated on your forms.</p></figcaption></figure></div>

### Acceptable Values&#x20;

* **Accept any Valid name (default)**: Allows any name that is properly formatted, contains no profanity, and does not include special characters or numbers
* **Accept only Non-Gibberish names**: Allows only names with valid format and non-gibberish characters
* **Custom**: Allows you to set your own custom validation rules for names
  * **Block Gibberish Names**: Block names classified as gibberish by Clearout
  * **Block Profanity Words**: Prevent submission of names containing profanity or inappropriate language.
  * **Block form submission on timeout**: Block form submission if the name validation request times out
  * **Block form submission on usage limit crossed**: Block form submission when name validation usage limit exceeds

### Feedback Messages&#x20;

This option allows you to customize the feedback (error) messages displayed on forms when an invalid or unacceptable value is entered in the name field.

* **Default**: A predefined set of feedback messages automatically set by the Form Guard.
* **Custom**: Displays all possible feedback message variations for the name field, with their default values shown as placeholder text in the input field.

## Hooks&#x20;

This option allows you to define custom JavaScript functions that execute either before or after Clearout's form validation.

### **On Before Verify**

This hook is triggered just before Clearout's name validation runs. The function receives two destructured parameters as defined below:

* **name**: The value entered in the respective form field.
* **$form**: The jQuery-wrapped form element.

The function should return an object with is\_acceptable and error\_msg properties. Setting is\_acceptable to false will consider the input value as invalid with the message set on the error\_msg property.

* **is\_acceptable**: The validation status of the On Before Verify hook.
* **error\_msg**: The HTML error message string to be displayed in case is\_acceptable is false.

```javascript
on_before_verify: function({ name, $form }) {
  let response = { is_acceptable: true, error_msg: '' };

  // Custom validation logic goes here
  if (name.includes('test')) {
    response.is_acceptable = false; // Set is acceptable to false to prevent form submission
    response.error_msg = 'Test Names are not allowed !!';
  }

  return response;
}
```

### **On After Verify**

This hook is triggered just after Clearout's Name validation runs and has returned back with the Clearout's Validation response. The function receives three de-structured params:

* **name**: The value entered in the respective form field
* **$form**: The jQuery-wrapped form element
* **result**: The Clearout's Validation result object

The function should return an object with is\_acceptable and error\_msg properties. Setting is\_acceptable to false will consider the input value as invalid with message set on error\_msg property.

* **is\_acceptable**: The validation status of the On After Verify hook.
* **error\_msg**: The HTML error message string to be displayed in case of is\_acceptable is false.

```javascript
on_after_verify: function({ name, $form, result }) {
  let response = { is_acceptable: true, error_msg: '' };

  // Custom validation logic goes here
  console.log(result);

  return response;
}
```

## Field Selection&#x20;

This option lets you choose whether Clearout's Form Guard should automatically detect and attach validation to name fields or apply validation only to specific fields of your choice.

By default, the **Automatic** mode is enabled, allowing Clearout to identify form fields based on various techniques:

* Element's type is of **text** and name attribute is any one of **name**, **first-name**, **last-name**, **first\_name**, **last\_name**, **firstname**, **lastname**, **clearout-name**
* Element has attribute **data-clearout-name-field**

## Gibberish Threshold&#x20;

Defines the sensitivity level for gibberish detection. Possible values: Off, Low, High (default: High). Higher values apply stricter detection criteria.

## Optional Fields&#x20;

In case the name input field is set as optional, without requiring the visitor to fill it, then you can set this option to <mark style="color:$info;">**"Yes."**</mark>

**Here's how it works**:

* **If the field is left empty**: The form submission will proceed without validation for that field.
* **If the field is filled**: Even though it's optional, the entered value will be validated. The form will only be allowed to submit if the value passes validation based on your configured criteria.

## Testing&#x20;

For testing purposes, you can use the following test names to verify different validation scenarios without incurring any credit cost.

<table><thead><tr><th width="185.84375">Test Name</th><th width="127.71484375">Gibberish</th><th width="148.33984375">Clearout Status</th><th>Profanity</th><th>Description</th></tr></thead><tbody><tr><td>Elon Musk</td><td>false</td><td>valid</td><td>false</td><td>Valid name with proper formatting</td></tr><tr><td>Bill Gates</td><td>false</td><td>valid</td><td>false</td><td>Valid name with proper formatting</td></tr><tr><td>John Doe</td><td>false</td><td>valid</td><td>false</td><td>Valid name with proper formatting</td></tr><tr><td>James aaa</td><td>true</td><td>invalid</td><td>false</td><td>Contains gibberish text</td></tr><tr><td>john19890512</td><td>true</td><td>invalid</td><td>false</td><td>Completely gibberish text</td></tr><tr><td>Mr1 Smith</td><td>false</td><td>invalid</td><td>false</td><td>Invalid name with number in title</td></tr><tr><td>M~r. Smith</td><td>false</td><td>invalid</td><td>false</td><td>Contains special character (~)</td></tr><tr><td>asdnaksjfajksfnjaksf</td><td>true</td><td>valid</td><td>false</td><td>Gibberish name, keyboard smash</td></tr><tr><td>qwertyuiop</td><td>true</td><td>valid</td><td>false</td><td>Gibberish name, keyboard smash</td></tr><tr><td>Élon Mùsk</td><td>false</td><td>valid</td><td>false</td><td>Accented valid name with proper formatting</td></tr><tr><td>Ävinfgùelsk</td><td>true</td><td>valid</td><td>false</td><td>Accented Gibberish name</td></tr><tr><td>asshole</td><td>false</td><td>valid</td><td>true</td><td>Profanity word with proper formatting</td></tr><tr><td>shit</td><td>false</td><td>valid</td><td>true</td><td>Profanity word with proper formatting</td></tr></tbody></table>

---
description: Verify chatbot leads in HubSpot real time.
---

# HubSpot Chatflows

**Verify chatbot and live chat leads in real time** by connecting Clearout’s Email Verification API to HubSpot Chatflows. This ensures invalid, disposable, or risky emails are caught during the conversation, before they enter your HubSpot CRM.​

You can also watch:

{% embed url="https://www.youtube.com/watch?embeds_referring_euri=https://clearout.io/&source_ve_path=Mjg2NjY&v=5EnqNy7OjdY" %}

***

### Integrate Clearout in HubSpot Chatflows  <a href="#k5hl0" id="k5hl0"></a>

Follow these steps for a bot such as **Qualify leads bot** (the same pattern works for other bots)

Open your HubSpot chatflow:

* Go to **Conversations → Chatflows**.
* Click **Create chatflow → Website** and choose a bot (for example,  **Qualify leads bot**).
* Click **Next** to go to the **Build** section, where you can edit the action boxes

The steps given below are for the **Qualify leads bot**:

{% stepper %}
{% step %}
Once 'Qualify leads bot' is selected, click Next to reach the Build section to edit the Action Boxes.
{% endstep %}

{% step %}
Scroll down to the Action box named Get Email and click on the + icon below it to create a new action for email verification.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/hs_chatflow.png" alt="Select Action Box to create trigger for Email verification in HubSpot Chatflow"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
A new Action window will open. Scroll down to Run a code snippet, give an Action name and delete the existing code.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/hs_chatflow_step two.png" alt="Run a code snippet, give an Action name and delete the existing code"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
Please copy and paste this code.

{% code lineNumbers="true" %}
```javascript
// Import the "request" module.
var request = require("request");

// Define the main function that will be exported.
exports.main = (event, callback) => {
  var options = {
    method: 'POST',
    url: 'https://api.clearout.io/v2/email_verify/instant',
    headers: {
      'Content-Type': 'application/json',
      'Authorization': 'REPLACE_WITH_YOUR_CLEAROUT_SERVER_APP_TOKEN',   // Add authorization token (API key).
    },
    body: {
      email: event.session.parsedResponses.Get_Email.parsedResponse, // Get the email address from the event object.
      timeout: 30000 //The option to define the maximum time that can be used for verifying the status of the given email address.
    },
    json: true
  };

  request(options, function (err, response, body) {
    if (err) throw new Error(err); // Handle errors.

    // initialize default value 
    let nextModuleNickname = 'send_to_team_member'     // The next module your bot will go to. If nothing is provided,we will select the next module in the bot path for you.
    let botMessage = '' // The message your bot will return.
    let responseExpected = false   // Whether or not this code snippet should be executed again with the next user input.

    // check entered email is safe to send if not then ask user to re-enter the email.
    if (body.data.safe_to_send === 'no') {
      nextModuleNickname = 'Get_Email'
      botMessage = `${body.data.email_address} is not valid email address`
    }
    // set the response.
    const responseJson = {
      botMessage,  
      nextModuleNickname,
      responseExpected
    }
    callback(responseJson);
  });
};
```
{% endcode %}
{% endstep %}

{% step %}
**Edit Row 11** by replacing '**REPLACE\_WITH\_YOUR\_CLEAROUT\_SERVER\_APP\_TOKEN**' with Clearout's API Token and Save.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/hs_chatflow_step6.png" alt="Add Clearout Server API Token in Row 11 on the Clearout Code Snippet"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
How To Generate a Clearout API Token?

* To generate a Clearout API token, log in to Clearout, then navigate to [Developer **→** API](https://app.clearout.io/developer/api/list).
* Give a name and description to the token and click Create
* Copy the API token and paste it in Row 11 of the code

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (31).png" alt="Generate Clearout Server API Token"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
Go to the Get Email action box and edit the action name to Get\_Email.

> Note: The name should be exactly the same.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/hs_chatflow_step7.png" alt="Go to the Get Email action box and edit the action name to Get_Email."><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
In the same Action box, scroll down to Save to HubSpot property. Choose Email from the dropdown. Uncheck the box that says Skip this action if property already exists and Save.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/hs_chatflow_step8.png" alt="Save to HubSpot property. Choose Email from the dropdown. Uncheck the box that says Skip this action if property already exists and Save."><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
**Your** **HubSpot chatbot with real-time email verification is READY**! Give it a test run by hitting Preview.

Wasn't that quick and easy? The addition of a simple code snippet to your Chatflows can effectively block unwanted junk data from infiltrating your system. Let's make a conscious decision to work exclusively with fresh and valid data, ensuring we don't squander our precious time on irrelevant information.


{% endstep %}
{% endstepper %}

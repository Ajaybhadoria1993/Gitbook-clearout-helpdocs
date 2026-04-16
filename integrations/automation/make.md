# Make

**Make** is a visual automation platform that lets you build multi-step workflows between Clearout and almost any online service, without writing code. You can use it to verify emails automatically whenever data moves between your forms, CRMs, sheets, and other tools.

### Verify emails in Make in Just 6 simple steps <a href="#verify-emails-in-make-in-6-simple-steps" id="verify-emails-in-make-in-6-simple-steps"></a>

{% stepper %}
{% step %}
#### Connect with Make <a href="#oh178" id="oh178"></a>

To integrate Clearout with any other app via Make, you need a Make account.​ If you don’t have one, [create a Make account](https://www.make.com/en/register?utm_source=clearout\&utm_medium=partner\&utm_campaign=clearout-partner-program)

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/clearout-integrations-1024x557.webp" alt="Connect Clearout via Make"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Create a new scenario <a href="#hjcie" id="hjcie"></a>

* **Log in** to your Make account.
* Click **Create a new scenario** to start building your workflow

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/Screenshot-2_1024x524-1024x453 (1).png" alt="Create new scenario on make to build workflow"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### &#x20;Set up a trigger connection

Every scenario starts with a module (connector) that triggers the workflow. For example, using **Google Sheets**:​

* Add **Google Sheets** as the first module.
* Connect your Google account to Make.
* Select the spreadsheet file and worksheet that contains the email addresses, then click **OK**.​

You can use any other trigger app (forms, CRM, etc.) in the same way.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/Screenshot-3-1024x705 (1).png" alt="SEt trigger to validate email address of new contacts"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Select a Clearout action

After your trigger is configured, add a Clearout action module:​

* In the next empty module, search for **Clearout** and select it.
* From the list of available actions, choose **Verify Email Address**.
* Click **OK** to proceed.​

This action will take an email from the trigger module and send it to Clearout for validation.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/Screenshot-4-1024x665 (1).png" alt="Select Clearout as Action to trigger the validition"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
#### Connect your Clearout account <a href="#ek9ur" id="ek9ur"></a>

* In the Clearout module, click **Add** to create a new connection.​
* When prompted, paste your **Clearout API Token**

**Generate your Clearout API key:**

* **Log in** to your Clearout Account.
* Go to [**Developer → API**](https://app.clearout.io/developer/api/list).
* Click **Create API Token** to generate a new token.
* Copy the token and paste it into the **Create a connection** popup in Make, then save.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/Screenshot-5-1024x551.png" alt="Paste Clearout API Token to create a connection with Make"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
#### Execute the scenario <a href="#rdppx" id="rdppx"></a>

After all modules are configured:

1. Click **Run once** (or **Run**) in Make to execute the scenario.
2. Check the Clearout module’s output to see verification results for each processed email.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/Screenshot-6-1024x667 (1).png" alt="Configure and run the module to test the email validation"><figcaption></figcaption></figure></div>

From here, you can add more modules (filters, routers, CRM updates, notifications) to route valid and invalid emails differently, fully **automating your verification flow with Make and Clearout.**
{% endstep %}
{% endstepper %}

# Make

**Make** is a visual automation platform that lets you build multi-step workflows between Clearout and almost any online service, without writing code. You can use it to verify emails automatically whenever data moves between your forms, CRMs, sheets, and other tools.

### Verify emails in Make in Just 6 simple steps <a href="#verify-emails-in-make-in-6-simple-steps" id="verify-emails-in-make-in-6-simple-steps"></a>

{% stepper %}
{% step %}
### **Connect with Make**

To integrate Clearout with any other app via Make, you need a Make account.​ If you don’t have one, [create a Make account](https://www.make.com/en/register?utm_source=clearout\&utm_medium=partner\&utm_campaign=clearout-partner-program)

<div data-with-frame="true"><figure><img src="https://docs.clearout.io/~gitbook/image?url=https%3A%2F%2F93738666-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FEXQQW0hsXyH0YD4ePoxb%252Fuploads%252FpWfRROQTX34h7E13mbcg%252Fclearout-integrations-1024x557.webp%3Falt%3Dmedia%26token%3D583ff7cc-91e3-4013-9964-323ccaa05af4&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=d5f446cf&#x26;sv=2" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Create a new scenario <a href="#hjcie" id="hjcie"></a>

* **Log in** to your Make account.
* Click **Create a new scenario** to start building your workflow

<div data-with-frame="true"><figure><img src="https://docs.clearout.io/~gitbook/image?url=https%3A%2F%2F93738666-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FEXQQW0hsXyH0YD4ePoxb%252Fuploads%252FydKzy5bXDKeQdyl56XHQ%252FScreenshot-2_1024x524-1024x453.png%3Falt%3Dmedia%26token%3D29f830d9-373d-4dde-bbad-24cd6669fe5b&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=86a11e6e&#x26;sv=2" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Set up a trigger connection

Every scenario starts with a module (connector) that triggers the workflow. For example, using **Google Sheets**:​

* Add **Google Sheets** as the first module.
* Connect your Google account to Make.
* Select the spreadsheet file and worksheet that contains the email addresses, then click **OK**.​

You can use any other trigger app (forms, CRM, etc.) in the same way.

<div data-with-frame="true"><figure><img src="https://docs.clearout.io/~gitbook/image?url=https%3A%2F%2F93738666-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FEXQQW0hsXyH0YD4ePoxb%252Fuploads%252FpJ8Lq0WzJnfCQx1G4EcD%252FScreenshot-3-1024x705.png%3Falt%3Dmedia%26token%3D0cf07e4d-b825-4977-9739-fa59eefe26a3&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=34ce979d&#x26;sv=2" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Select a Clearout action

After configuring your trigger, add a Clearout module to perform the desired action:​

* In the next empty module, search for **Clearout** and select it.
* From the list of available actions, choose one based on your requirement.
* Click **OK** to proceed.​

Clearout provides the following **key actions** in [Make.com](https://make.com)

**Verify Email Address**

Validate an email address to check its deliverability and quality

This action takes an email from the previous module and verifies whether it is:

* Valid
* In-valid
* Catch-all
* Disposable
* Risky

Using this, you can reduce bounce rates and improve email campaign performance.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/make_clearout_ev_action.png" alt=""><figcaption></figcaption></figure></div>

**Find Email**

Find a professional, pre-verified email address using:

* Person’s name
* Company domain

Each result includes a confidence score indicating the likelihood of the email being valid.

This is useful for:

* Lead generation
* Prospecting
* Outbound workflows

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/make_clearout_ef_action.png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### **Connect your Clearout account**

* In the Clearout module, click **Add** to create a new connection.​
* When prompted, paste your **Clearout API Token**

**Generate your Clearout API key:**

* **Log in** to your Clearout Account.
* Go to [**Developer → API**](https://app.clearout.io/developer/api/list).
* Click **Create API Token** to generate a new token.
* Copy the token and paste it into the **Create a connection** popup in Make, then save.

<div data-with-frame="true"><figure><img src="https://docs.clearout.io/~gitbook/image?url=https%3A%2F%2F93738666-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FEXQQW0hsXyH0YD4ePoxb%252Fuploads%252FlpWlEJhkaEzM7aqZJUUg%252FScreenshot-5-1024x551.png%3Falt%3Dmedia%26token%3D285ec79b-0875-4bc3-a31c-c81997e4ac85&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=65d6ff8f&#x26;sv=2" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### **Execute the scenario**

After all modules are configured:

1. Click **Run once** (or **Run**) in Make to execute the scenario.
2. Check the Clearout module’s output to see verification results for each processed email.

<div data-with-frame="true"><figure><img src="https://docs.clearout.io/~gitbook/image?url=https%3A%2F%2F93738666-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FEXQQW0hsXyH0YD4ePoxb%252Fuploads%252FFwX2XQ93SxMrvRGSwv7s%252FScreenshot-6-1024x667.png%3Falt%3Dmedia%26token%3Da212dfb7-6579-4cc8-a997-fc2e92ee9334&#x26;width=768&#x26;dpr=3&#x26;quality=100&#x26;sign=43e17af7&#x26;sv=2" alt=""><figcaption></figcaption></figure></div>

From here, you can add more modules (filters, routers, CRM updates, notifications) to route valid and invalid emails differently, fully **automating your verification flow with Make and Clearout.**
{% endstep %}
{% endstepper %}

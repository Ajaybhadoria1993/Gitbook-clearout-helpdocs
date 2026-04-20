# Zapier

Use **Zapier + Clearout** to verify and find emails automatically in the tools you already use, without writing code.

You can connect Clearout to 1,500+ apps so every new lead, signup, or contact is checked or enriched as it flows through your Zaps.

## How to Verify/Find emails in 5 steps <a href="#how-to-verify--find-emails-in-5-steps" id="how-to-verify--find-emails-in-5-steps"></a>

{% embed url="https://www.youtube.com/watch?v=AGdoITK6zR8" %}

{% stepper %}
{% step %}
#### Connect with Zapier <a href="#oh178" id="oh178"></a>

To integrate Clearout via Zapier, you’ll need a Zapier account.​ If you don’t have one yet, [create a Zapier account.](https://zapier.com/app/login)
{% endstep %}

{% step %}
#### Create a new Zap <a href="#hjcie" id="hjcie"></a>

* **Log in** to your Zapier account.
* Click **Make a Zap!** to create a new Zap.
* Give your Zap a clear name _(for example, **Validate new leads with Clearout**)_
{% endstep %}

{% step %}
#### Set up a Trigger <a href="#pxict" id="pxict"></a>

Every Zap starts with a **trigger** that fires when something happens in another app. Example:​

* Choose **Google Sheets** as the trigger app.
* Select a trigger event, such as **New Spreadsheet Row**.
* Pick the spreadsheet and worksheet that contain the email addresses you want to process, then click **Continue**.

You can use any other trigger app (forms, CRM, Ads, etc.) the same way.
{% endstep %}

{% step %}
**Select an Action**

After the trigger, add Clearout as the **Action**:

* Click **+** to add an action.
* Search for **Clearout** and select it.​
* Choose one of the available actions:​

**Key actions**

* **Verify Email Address**\
  Validate an email address to assess its deliverability and quality.\
  \
  Clearout checks if it is valid, invalid, catch‑all, disposable, or risky so you can prevent bounces and protect sender reputation before outreach.
* **Find Email**\
  **Discover** a professional, **pre‑verified email address** using a person’s name and company domain, with an AI‑driven **confidence score** that indicates the likelihood of the email being valid.\
  \
  This feature is particularly useful for lead enrichment, prospecting, and outbound workflows.

{% hint style="info" %}
**Important note**

Use Clearout Zap version ≥ 2.2.0 to avoid Zapier’s 30‑second action timeout. If you stay on an older version, longer‑running tasks may need Zapier’s webhook‑based callbacks. Otherwise, actions that run over 30 seconds may fail with “<mark style="color:$danger;">The app did not respond in‑time.</mark>”
{% endhint %}
{% endstep %}

{% step %}
**Connect your Clearout Account**

* In the Clearout action step, click **Connect a new account**.​
* When prompted, paste your **Clearout API Token**.​

How to generate your Clearout API key:

* **Log in** to the Clearout Dashboard.
* Go to [**Developer → API**](https://app.clearout.io/developer/api/list).
* Click **Generate API Token**, give it a name, and copy the token.​
* **Paste** this token into Zapier and save the connection.

Once connected, map the email fields from your trigger app into the Clearout action, test the Zap, and turn it on. From then on, Clearout will **automatically verify or find emails every time your Zap runs**.
{% endstep %}
{% endstepper %}

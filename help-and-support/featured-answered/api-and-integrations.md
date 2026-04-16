# API & Integrations

Clearout API enables developers and website administrators to integrate email verification and email finder capabilities directly into their existing systems, applications, and workflows. The API allows you to verify or find email addresses programmatically without using the web interface.

## API

<details>

<summary>What is the Clearout API?</summary>

The Clearout API allows developers to integrate email verification and email finding into their applications and workflows.

</details>

<details>

<summary>How do I generate an API key?</summary>

Go to **Menu** → **Developer** → **API** → **Create API Token**, name it, and create your token.

</details>

<details>

<summary>What does API response data include?</summary>

* Email status
* Safe-to-send status
* Status reason
* Disposable detection
* Role-based detection
* MX & SMTP details
* Timestamp of verification

</details>

<details>

<summary>Why am I getting “Unknown” results?</summary>

There can be multiple reasons for an email to end up as an unknown result, including:

* Greylisting
* Server timeout
* Temporary mail server issues

Unknown results do not consume credits.

</details>

<details>

<summary>Why did I hit API rate limits?</summary>

API rate limits are determined by the [plan associated](https://docs.clearout.io/developers/api/overview#plan-specific-limits) with your Clearout account. Each plan includes a specific **Requests Per Minute (RPM)** limit to ensure a fair usage policy across all users.

You can check your current limits under [Plans](https://app.clearout.io/account/manage-plans) in your Clearout dashboard.

If your application exceeds the allowed RPM, API requests will be responded with a HTTP 429 response code.

To increase your API rate limits, you can:

* [Upgrade](https://app.clearout.io/pricing) to a higher plan with increased RPM limits
* Purchase [add-ons](https://app.clearout.io/account/manage-plans) that provide additional API capacity

If you require higher limits for your use case, please contact **Clearout Support via chat or email at us@clearout.io** for assistance.Response time

</details>

***

## Integrations

<details>

<summary>What integrations does Clearout support?</summary>

Clearout supports CRM, ESP, Forms, WordPress, WooCommerce, Google Sheets, and automation tools like Zapier and Make.

</details>

<details>

<summary>How does ESP/CRM integration work?</summary>

* Connect your CRM/ESP
* Import lists
* Verify
* Export results back automatically

</details>

<details>

<summary>What are real-time form validation benefits?</summary>

* Block invalids/fake/junk emails at the point of contact
* Catch typos instantly
* Block disposable emails
* Reduce bounce rates
* Improve database quality

</details>

<details>

<summary>How does Google Sheets integration work?</summary>

Use the Clearout Add-on inside Google Sheets to verify emails directly without exporting files.

</details>

<details>

<summary>Can I automate email verification?</summary>

Yes. Connect Clearout with Zapier, Make, or Integrately to automate workflows.

</details>

<br>

# Email Verifier

<details>

<summary>What does the Clearout Email Verifier do?</summary>

Clearout Email Verifier checks whether an email address is valid and capable of receiving emails. It performs 20+ validation checks including format validation, domain checks, MX record verification, SMTP validation, and detection of disposable or role-based addresses to determine the deliverability of each email.

</details>

<details>

<summary>What validation checks does the Email Verifier perform?</summary>

Clearout performs multiple validation checks, including:

* Email format validation
* Domain and MX record verification
* Catch-all domain detection
* Disposable email detection
* Role-based email detection
* Gibberish email detection
* SMTP server validation

These checks help determine whether an email address is valid and safe to send to.

</details>

<details>

<summary>What is the accuracy rate of Clearout Email Verification?</summary>

Clearout Email Verifier provides **up to 99.73% accuracy** by combining machine learning with multiple validation checks and proprietary verification algorithms.

</details>

<details>

<summary>Does Clearout send emails to verify email addresses?</summary>

No. Clearout does **not send emails** to the recipient inbox.\
Verification is performed by securely connecting to the recipient's **SMTP server** to validate the email address.

</details>

<details>

<summary>Can Clearout detect catch-all (accept-all) domains?</summary>

Yes. Clearout can identify catch-all domains that accept all incoming emails regardless of whether the mailbox exists.

</details>

<details>

<summary>Can Clearout detect disposable email addresses?</summary>

Yes. Clearout detects temporary or disposable email domains commonly used for spam, fake signups, or short-term use.

</details>

<details>

<summary>Can I verify email addresses in real-time?</summary>

Yes. Clearout supports real-time email verification through:

* REST API
* Form Guard
* WordPress plugin

This allows you to verify emails at the point of form submission or signup.

</details>

<details>

<summary>Can I verify emails in bulk?</summary>

Yes. Clearout allows bulk email verification by uploading a file in .csv or .xlsx format or importing lists from supported integrations.

</details>

<details>

<summary>How many free email verifications are available?</summary>

After creating a Clearout account, you can verify up to 100 email addresses for free.

</details>

<details>

<summary>How much does one email verification cost?</summary>

Each email verification consumes 1 credit.

</details>

<details>

<summary>Can I integrate the Email Verifier with my software?</summary>

Yes. Clearout Email Verifier can be integrated into your applications using the [Clearout API](https://docs.clearout.io/developers/api/email-verify), which supports integration with any programming language.

</details>

<details>

<summary>What is AI Verdict in Clearout Email Verification?</summary>

AI Verdict is the classification result/human-readable result generated using Clearout’s machine-learning system that analyzes email addresses based on multiple parameters such as domain credibility, typos, and patterns to determine whether an email should be accepted, rejected, or reviewed.

</details>

<details>

<summary>Why can a “Guaranteed Deliverable” email still bounce?</summary>

While Clearout provides up to 99.73% verification accuracy, there are rare situations where a verified email may still bounce due to external mail server behavior.

This can happen because of:

* **Email status propagation delays**\
  Some mail servers take time to update mailbox status. If verification happens during this update window, the result may temporarily appear valid.
* **Anti-spam protected mail servers**\
  Certain servers hide the true mailbox status behind spam filters. In these cases, the actual status can only be confirmed after sending an email.
* **Email forwarding rules**\
  If an email address forwards to another mailbox, the verification system may detect the forwarding endpoint rather than the final destination.
* **Non-standard or internal mail server configurations**\
  Some mail systems (often internal corporate servers) do not follow standard SMTP validation responses, making accurate verification difficult.
* **Microsoft Office 365 behavior**\
  Some Office 365 servers respond as if a mailbox exists during verification but may still reject emails when delivery is attempted.
* **Educational (.edu) domains**\
  Many educational institutions configure their mail servers to always return a positive response, even when the mailbox does not exist. The actual status may only be revealed during real email delivery.

Because these behaviors depend on the **recipient mail server configuration**, they are outside the control of any email verification service.

</details>


---
description: Multi-layer validation checks for accurate, reliable email deliverability
icon: envelope
---

# Overview

Clearout Email Verifier ensures every email address you collect or use is **valid, reachable, and safe to send**. It combines real-time checks, mailbox-level diagnostics, and risk detection to prevent bad data from entering your CRM, marketing, or outreach workflows.

Whether you are validating form submissions instantly or cleaning millions of records in bulk, Clearout delivers **high-confidence results without sending any emails,** keeping your sender reputation protected.

<div data-with-frame="true"><figure><img src="../.gitbook/assets/email-validation-gtm-workflow.png" alt="Real-time email validation on GTM workflows" width="563"><figcaption><p>Email Validation for GTM workflows</p></figcaption></figure></div>

## Different Ways of Email Validation

Clearout supports multiple validation workflows to match how your teams collect and manage email data

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><h3>Instant Validation</h3><p></p><p>Validate emails instantly at the point of capture before they enter your system.</p><ul><li>Signup and lead forms</li><li>CRM data entry</li><li>Live API requests</li></ul></td><td><a href="quick-validation.md">quick-validation.md</a></td></tr><tr><td><h3>Bulk Validation</h3><p></p><p>Upload large lists (CSV/XLSX) and validate them at scale.</p><ul><li>Cold outreach lists</li><li>CRM cleanup</li><li>Imported or legacy data</li></ul></td><td><a href="bulk-validation.md">bulk-validation.md</a></td></tr><tr><td><h3>API-Based Validation</h3><p></p><p>Integrate Clearout directly into your backend or data pipeline for automated validation.</p><ul><li><a href="/broken/pages/30b386ddb6cfa13c4acec0d77478f79d5f845734#post-email_verify-instant">Instant Verification</a></li><li><a href="/broken/pages/30b386ddb6cfa13c4acec0d77478f79d5f845734#post-email_verify-bulk">Bulk List Verification</a></li></ul></td><td><a href="/broken/pages/30b386ddb6cfa13c4acec0d77478f79d5f845734">Broken link</a></td></tr></tbody></table>

## Understanding Email Verification Results <a href="#understanding_email_verification_results" id="understanding_email_verification_results"></a>

Email deliverability is critical for successful email programs. Clearout backs its verification results with a **99% deliverability rate guarantee**.&#x20;

When you verify email addresses with Clearout, the bounce rate will not exceed 3% for messages sent to "**Guaranteed Deliverable"** email addresses or addresses where the **Safe-to-Send** flag is "**Yes**" provided all qualifying criteria are met.\
\
**Criteria to qualify for Guaranteed Deliverability**

* Email addresses must be classified with the **Safe-to-Send** flag as **Yes**
* Emails must be sent within 24 hours of the verification time.
* Email addresses must have been acquired via an opt-in process; purchased or rented lists are excluded from the guarantee.
* Free service providers such as Yahoo and AOL are excluded.
* Mail servers behind certain anti-spam settings (for example, Microsoft 365) do not qualify.
* Bounces caused by technical difficulties, poor sender reputation, server capacity limits, misconfiguration of the mail server, server unavailability, or deliveries blocked due to internal rules or explicit sender blocks are not covered

### Safe To Send <a href="#safe_to_send" id="safe_to_send"></a>

The **Safe-to-Send** flag is based on industry best practices. In some cases, valid email addresses can still bounce for reasons beyond syntax or mailbox existence, so the Safe-to-Send flag indicates how safe an address is to use based on the probability of a bounce

<table><thead><tr><th width="157.99609375">Safe to Send Value</th><th>Description</th></tr></thead><tbody><tr><td>Yes</td><td>Sending emails to these addresses is safe, provided emails are sent within 24 hours of the verification time.</td></tr><tr><td>Risky</td><td>There is some risk associated with sending to these addresses. They are generally usable when the bounce rate must remain below 5% or when using your own sending infrastructure instead of an external Email Service Provider (ESP).</td></tr><tr><td>No</td><td>Invalid email addresses that you should avoid sending to.</td></tr><tr><td>Unknown</td><td>The status of the email cannot be determined at this time due to external or temporary factors.</td></tr></tbody></table>

The risk factor depends upon multiple reasons, like

* Mail servers that are incorrectly configured&#x20;
* Unusual SMTP response  &#x20;
* Any temporary mail account issue
* Mail servers configured to accept all messages with anti-spam protection that reveals true status only when sending (for example, some Office 365 domains)

### Status

Clearout categorizes email verification status into four primary statuses:  **Valid, Invalid, Catch All, or Unknown**. These statuses indicate the real-time deliverability of a given email addres&#x73;**.**

<table><thead><tr><th width="148.76953125">Primary Status</th><th>Description</th></tr></thead><tbody><tr><td>Valid</td><td>A valid email address has been verified as a real mailbox that is currently accepting email.</td></tr><tr><td>Invalid</td><td>An invalid email address has been verified as a bad recipient that does not exist or is not accepting email and will result in a bounce.</td></tr><tr><td>Catch All</td><td>It's a domain-level setting that accepts messages sent to any address under the domain, including invalid ones. Messages may be rejected later due to spam filters, mailbox limits, or security rules, so the "<strong>safe to send</strong>" status is marked as <strong>"risky".</strong></td></tr><tr><td>Unknown</td><td>This unknown status occurs when Clearout fails to receive a response from the recipient’s mail server. This event often occurs when the mail server is slow or temporarily unavailable. In some cases, retrying later returns a valid or invalid result.</td></tr></tbody></table>

### Sub-Statuses with Reason

Further details that provide more context on the primary status

<table><thead><tr><th>Code</th><th width="186.48828125">Reason</th><th width="340.9921875">Description</th><th width="144.8515625">Primary Status</th><th>Bounce Type</th></tr></thead><tbody><tr><td>200</td><td>Success</td><td>This email address is valid and safe to send emails.</td><td>Valid</td><td></td></tr><tr><td>400</td><td>Syntax error</td><td>A syntax error in an email address occurs when the address does not follow the proper format defined by email standards (<a href="https://datatracker.ietf.org/doc/html/rfc5322">RFC 5322</a>).</td><td>Invalid</td><td>Hard</td></tr><tr><td>401</td><td>Probably Spamtrap/Honeypot</td><td>These email addresses are believed to be spam traps and must not be used for sending.</td><td>Invalid</td><td>Soft</td></tr><tr><td>402</td><td>Mail server connection timeout</td><td>Unable to connect to the mail server within the expected time; retry later.</td><td>Unknown</td><td></td></tr><tr><td>403</td><td>Domain was not found</td><td>This email address is valid in syntax, but the domain doesn't have any records in DNS or have incomplete DNS Records.</td><td>Invalid</td><td>Hard</td></tr><tr><td>404</td><td>Not a Mail Server</td><td>This email address doesn't belong to a mail server.</td><td>Invalid</td><td>Hard</td></tr><tr><td>405</td><td>Mail server error</td><td>This email address belongs to a mail server that is returning a temporary error.</td><td>Unknown</td><td></td></tr><tr><td>406</td><td>Mailbox was not found</td><td>This email address is valid in syntax but does not exist.</td><td>Invalid</td><td>Hard</td></tr><tr><td>407</td><td>Mail server employed greylisting technique; so try after sometime</td><td>Domain IP of the specified email address is greylisted, adviced to retry sometime later.</td><td>Unknown</td><td></td></tr><tr><td>411</td><td>Catch All mail server</td><td>Mail server has been configured to receive all messages that are addressed to an incorrect email address for a domain.</td><td>Catch All</td><td></td></tr><tr><td>412</td><td>Unable to determine; retry later after an hour or so</td><td>This email address is not responding at the moment so that you can retry later an hour or so.</td><td>Unknown</td><td></td></tr><tr><td>413</td><td>Mailbox quota exceeded.</td><td>This email address exceeded the space quota and is not accepting any emails.</td><td>Invalid</td><td>Soft</td></tr><tr><td>414</td><td>Retry later after an hour or contact support</td><td>The server did not allow verification of the emails temporarily. As we do not charge for the unknowns, it is always advisable to retry verifying at a later point in time.</td><td>Unknown</td><td></td></tr><tr><td>416</td><td>No Answer Received From Authoritative Server</td><td>This email address belongs to a mail server that is not responding at the time of verification.</td><td>Unknown</td><td></td></tr><tr><td>417</td><td>DNS Query Timeout</td><td>Unable to resolve DNS within the stipulated time, so retry at a later time, increasing the timeout parameter (API verification).</td><td>Unknown</td><td></td></tr><tr><td>418</td><td>DNS Query Unhandled Error</td><td>This email address belongs to a mail server that is returning a temporary error.</td><td>Unknown</td><td></td></tr><tr><td>419</td><td>Insufficient System Resource (disk/memory)</td><td>This email server exceeded the space quota and is not accepting any emails.</td><td>Invalid</td><td>Soft</td></tr><tr><td>420</td><td>Mail server command timeout</td><td>Verifying this email address takes a longer time than expected. Please retry at a later time, increasing the timeout parameter(API verification).</td><td>Unknown</td><td></td></tr><tr><td>421</td><td>Message receiving limit reached</td><td>Inbound message limit reached for this recipient.</td><td>Invalid</td><td>Soft</td></tr><tr><td>428</td><td>Account inactive due to quota exceeded</td><td>Account disabled due to usage beyond allocated quota.</td><td>Invalid</td><td>Soft</td></tr><tr><td>601</td><td>Email is part of allowlist</td><td>Allowlisted email - validation bypassed</td><td>Valid</td><td></td></tr><tr><td>602</td><td>Email is part of blocklist</td><td>Blocklisted email - validation bypassed</td><td>Invalid</td><td></td></tr><tr><td>603</td><td>Domain is part of allowlist</td><td>Allowlisted domain - validation bypassed</td><td>Valid</td><td></td></tr><tr><td>604</td><td>Domain is part of blocklist</td><td>Blocklisted domain - validation bypassed</td><td>Invalid</td><td></td></tr><tr><td>606</td><td>Unsupported character</td><td>The email address contains invalid or unsupported characters and does not comply with standard email format specifications.</td><td>Invalid</td><td>Hard</td></tr><tr><td>701</td><td>Account disabled</td><td>Mailbox associated with the email account is disabled.</td><td>Invalid</td><td>Hard</td></tr></tbody></table>

### Associated Results <a href="#associated_results" id="associated_results"></a>

Associated result fields provide additional context about each email address beyond the primary status

<table><thead><tr><th width="223.4921875">Field</th><th>Description</th></tr></thead><tbody><tr><td>Disposable Email Address</td><td>It is recommended to exclude email addresses from temporary mailbox services, which are intended for short-term use, to avoid higher bounce rates.</td></tr><tr><td>Free Email Address</td><td>Email addresses from free providers like Gmail or Yahoo are acceptable to use, but non-free domains may perform better in some cases​.</td></tr><tr><td>Role-Based Email Address</td><td>Email addresses tied to a function (for example, support@ or sales@) rather than a person are generally not recommended for marketing emails.</td></tr><tr><td>Autosuggestion</td><td>When a potential typo is detected in the domain (for example, user@yaho.com → user@yahoo.com), the system suggests a correction; these suggestions are not pre-verified​.</td></tr><tr><td>MX Record</td><td>The Mail exchange (MX) record is used to route email for the domain and is returned in both bulk verification results and API responses​.</td></tr><tr><td>SMTP Provider</td><td>Email service provider handling mail exchange for the domain; useful for deciding how to treat the address in campaigns​</td></tr><tr><td>Verification Timestamp</td><td>Date and time when the email address was verified, used to assess list freshness​</td></tr><tr><td>Verification Time Taken</td><td>Time taken to complete verification for the email address, in milliseconds​</td></tr></tbody></table>

### Clearout Standard Columns <a href="#result_file_header" id="result_file_header"></a>

The Clearout standard columns <mark style="color:$info;">**are additional data fields that can be appended**</mark> to your original list after an email verification process to provide comprehensive information about the quality and status of each email address

<div data-with-frame="true"><figure><img src="../.gitbook/assets/Clearout-standard-column.png" alt="clearout bulk email validation standard result  columns"><figcaption><p>Email address appended with Clearout Standard Columns </p></figcaption></figure></div>

<table><thead><tr><th width="265.5078125">Name</th><th>Description</th></tr></thead><tbody><tr><td>Clearout Safe to Send</td><td><p>Indicates whether it is safe to send to the address. </p><p>Values: <strong>Yes, Risky, No, Unknown</strong></p></td></tr><tr><td>Clearout Verification Status</td><td><p>Indicates the verification status of the email address. </p><p>Values: <strong>Valid, Invalid, Catch All, Unknown</strong></p></td></tr><tr><td>Clearout Reason</td><td>Determines the reason for the current status of an email address. Multiple reasons described below.</td></tr><tr><td>Clearout Suggested Email</td><td>Suggestions on what the valid email address could be. Mostly helpful in case of typos.</td></tr><tr><td>Clearout Bounce Type</td><td>Invalid email addresses are categorized as Hard bounce &#x26; Soft bounce.</td></tr><tr><td>Clearout Disposable Status</td><td><p>Whether an email address is disposable or not. </p><p>Categorized as <strong>Yes or No</strong>.</p></td></tr><tr><td>Clearout Free Account Status</td><td><p>Whether an email address belongs to a free email provider or not. </p><p>Categorized as <strong>Yes or No</strong></p></td></tr><tr><td>Clearout Role Account Status</td><td><p>Whether an email address is a role account or not. </p><p>Categorized as <strong>Yes or No</strong></p></td></tr><tr><td>Clearout Gibberish Status</td><td><p>Calling attention towards random email addresses. </p><p>Categorized as <strong>Yes or No</strong></p></td></tr><tr><td>Clearout Account</td><td>Identification of a probable name of the holder of the email address.</td></tr><tr><td>Clearout Domain</td><td>Identification of a probable domain name to which the email address belongs.</td></tr><tr><td>Clearout MX Record</td><td>Shows the MX record for the given email domain of the email address under verification.</td></tr><tr><td>Clearout SMTP Provider</td><td>Shows the STMP provider of the mail exchange for the given email domain.</td></tr><tr><td>Clearout Verified At (UTC)</td><td>Provides the exact time at which the email address was verified.</td></tr><tr><td>Clearout Time Taken (ms)</td><td>Time taken to verify the email address, in milliseconds.</td></tr></tbody></table>

## Verification Settings

Clearout offers flexible settings to tailor validation behavior to your use case, such as options for real-time verification or batch processing, depending on your specific needs.

### Bulk Verification Mode

Clearout provides multiple validation modes based on accuracy and speed requirements.

* **Fastest Turnaround -** Optimized for extreme speed. The system provides a swift first-pass filter for large, unvetted data sets.
* **Highest Accuracy -** Gold standard for list cleaning. It safeguards your sender's reputation by maintaining bounce rates below 3%.

Choose the mode that best fits your workflow.

### **Gibberish Threshold Value**&#x20;

Adjust the gibberish threshold to control how strict the gibberish validation check is during real-time validation

<table><thead><tr><th width="186">Threshold Value</th><th>Description</th></tr></thead><tbody><tr><td>Off</td><td>Skip the gibberish check</td></tr><tr><td>Medium</td><td>Apply a moderate level of gibberish detection</td></tr><tr><td>High</td><td>Apply a strict check to determine whether an email address is gibberish</td></tr></tbody></table>

### Allowlist / Blocklist (ABL)

Blocklist and Allowlist settings let you control which emails and domains are allowed or blocked at the point of entry. You can create filters for specific email addresses, patterns, domains, wildcard domains, or TLDs.

<div data-with-frame="true"><figure><img src="../.gitbook/assets/Allow-block-list.png" alt="allowlist and blocklist setup"><figcaption><p> Allow/Block domains, email addresses based on your needs</p></figcaption></figure></div>

## Data Retention

Clearout follows strict data retention and privacy practices.

* Validation data is stored only as long as necessary (default 30 days)
* Retention is configurable from 1 to 45 days
* Data is handled in a GDPR- and compliance-friendly manner

Your data stays secure, private, and under your control.

<div data-full-width="false" data-with-frame="true"><figure><img src="../.gitbook/assets/security-compliances (1).png" alt="security compilance" width="375"><figcaption><p><em>Security Compliance Frameworks supported by Clearout</em></p></figcaption></figure></div>

## Credit charge

Clearout follows a transparent credit usage model.&#x20;

* **1 credit** is charged per email validation, excluding the Unknown result status.
* Credits are consumed only when validation is performed
* Duplicate email addresses within the same list are not charged.&#x20;

This ensures predictable usage and cost control at scale. [Click here](https://clearout.io/pricing-guide/) to read about credit charges in detail.

## Supported Integrations

Clearout integrates seamlessly into your existing tech stack.

<table data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><a href="../integrations/crm/"><mark style="color:$info;"><strong>CRM</strong></mark></a></td><td><p></p><ul><li>Validate contacts automatically</li><li>Keep sales and marketing data clean</li><li>Reduce manual cleanup</li></ul></td></tr><tr><td><a href="../developers/api/"><mark style="color:$info;"><strong>API</strong></mark></a></td><td><p></p><ul><li>Real-time and bulk validation endpoints</li><li>Built for scale and automation</li><li>Secure and reliable</li></ul></td></tr><tr><td><a href="../integrations/automation/"><mark style="color:$info;"><strong>Automations</strong></mark></a></td><td><p></p><ul><li><a href="../integrations/automation/zapier.md">Zapier</a></li><li><a href="../integrations/automation/make.md">Make</a></li><li><a href="../developers/webhooks/">Webhooks</a></li></ul></td></tr></tbody></table>

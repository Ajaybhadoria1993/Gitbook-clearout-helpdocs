---
description: Find any professional email address in real-time with confidence score
icon: magnifying-glass-music
---

# Overview

Clearout Email Finder is **an advanced email discovery** tool that helps sales, marketing, and recruitment teams find verified email addresses for any B2B professional.&#x20;

With high precision and real-time checks, Email Finder discovers safe email addresses with AI confidence scores to boost delivery rates and email outreach success.

{% hint style="info" %}
Email finder pre-verifies discovered email address with out incurring additional verification credit.
{% endhint %}

## Different Ways of Email Finding

Clearout Email Finder offers multiple ways to discover email addresses based on your use case. You can choose the appropriate method depending on whether you need instant results or want to process a list of prospects in bulk.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><p></p><h4><mark style="color:$info;">Instant Finding</mark></h4><p></p><p>Find email addresses instantly by searching one prospect at a time using their name and company/domain.</p><ul><li>Quick lookup for single prospects</li><li>Ideal for sales/recruiting workflows</li><li>Get results in a few seconds</li><li>Includes confidence score with each result</li></ul></td><td><a href="instant-finder.md">instant-finder.md</a></td></tr><tr><td><p></p><h4><mark style="color:$info;">Bulk Finding</mark></h4><p></p><p>Upload a list and find emails at scale by processing multiple prospects in one go.</p><ul><li>Supports CSV / XLSX uploads</li><li>Enrich lists with found email addresses</li><li>Download processed results (CSV/XLSX)</li><li>Summary insights like Found %, Duplicates, Business accounts</li></ul></td><td><a href="bulk-finder.md">bulk-finder.md</a></td></tr><tr><td><p></p><h4><mark style="color:$info;">API-Based Finding</mark></h4><p></p><p>Integrate Email Finder into your system and automate email discovery via API.</p><ul><li>Find emails using name + domain/company</li><li>Works for real-time and automated workflows</li><li>Best for CRMs / internal tools / pipelines</li><li>Start by generating your API key</li></ul></td><td><a href="/broken/pages/7b22d5e21f842be901bf681c46a3ffd0b7aa734c">Broken link</a></td></tr></tbody></table>

## Understanding Email Finder  <a href="#understanding_email_finder" id="understanding_email_finder"></a>

### Input

The Email Finder discovers a **pre-verified email address** using two simple inputs:​

* Full name of the person, such as "Bill Gates."
* Company or domain name (for example, "<mark style="color:blue;">microsoft.com</mark>").​

Each unique name-domain combination is treated as one finding, with different credit usage for person and generic (role) email addresses.​

### Output

For every finding request, the Email Finder returns a structured result that can include

* Discovered email address or generic alternative (for example, <mark style="color:blue;">bill@microsoft.com</mark> or <mark style="color:blue;">info@tesla.com</mark>).​ If not able to find it, the response will be "No email found."&#x20;
* The output also includes enrichment fields such as the **normalized name, company/domain, confidence score**, and indicators for whether the account is a business account or a role account.​
* The Email Finder History table contains a history entry that includes the name, company, the resulting email, the confidence score, and the date and time of the search.​

## Understanding Confidence Score

Email Finder Confidence Score is an **AI-driven indicator** that shows how accurately the discovered email address matches your lead's information (name, domain, company name), and it is calculated in real time by analyzing multiple data points and using advanced machine learning algorithms.

{% include "../.gitbook/includes/ef-table.md" %}

{% hint style="info" %}
**Quick Note:** Higher score = higher trust, better deliverability, and stronger alignment with true lead identity.
{% endhint %}

## Finder Settings

The **Email Finder settings** page lets users control how the email discovery process treats role-based addresses and domain formats.​

Accessing Email Finder settings

* Navigate to [**Settings → Email Finder**](https://app.clearout.io/settings/email_finder) from the left navigation menu.
* Use this page to configure global behavior that applies to all Email Finder lookups in your account.​

<div data-with-frame="true"><figure><img src="../.gitbook/assets/ef-setting.png" alt="Manage Email Finder Settings"><figcaption></figcaption></figure></div>

### Role-Based Emails <a href="#role-based-emails" id="role-based-emails"></a>

Role-based emails are generic addresses that are not tied to a specific person, for example, <mark style="color:blue;">support@amazon.com</mark> or <mark style="color:blue;">hr@hubspot.com</mark>.​

* **Include**:
  * Email Finder is allowed to return role-based email addresses when a professional address cannot be found.​
  * Use this when generic inboxes are acceptable for your outreach or workflows.​
* **Exclude** (default):
  * Email Finder will skip role-based email addresses and only return person-based addresses where possible.​
  * Use this when your use case requires direct, individual contacts and you want to avoid generic team or department inboxes.​

To update this behavior, select the desired option under **Role Based Emails** and your preference is saved for subsequent searches.​

### Domain Check <a href="#domain-check" id="domain-check"></a>

Domain check controls how strictly Email Finder interprets and validates the domain input when supplied values as company name and Website URL​

* **Strict**:
  * Use only the Domain/Website URL field; even if a company name is present, Clearout will exclusively rely on the domain for finding emails.
  * If a domain is missing in bulk uploads or API requests, the request will not be processed to prevent inaccurate results.
  * Helps match emails with verified company domains, avoiding incorrect email retrieval.
* **Relax** <mark style="color:$primary;">(default)</mark>:
  * Accepts more flexible domain forms (for example, URLs with protocols) and attempts to normalize them before performing the search or if the company name is provided, the system will try to resolve the equivalent domain.&#x20;
  * Recommended when importing mixed data from various sources where domains may include Website URL, domain names without protocol, or the company names.​

Choose **Strict** or **Relax** under **Domain Check** to align the Email Finder with the quality and structure of your domain inputs.

#### How It Works Across Different Email Finder Modes

**Bulk Email Finder:**

* The uploaded file must contain a website/domain column.
* If the file lacks a domain column, it will be rejected to ensure accuracy.

**Instant Email Finder** (Single Lookup):

* A domain input is mandatory when this setting is enabled.
* If only a company name is provided without a domain, the request will be declined to prevent mismatches.

## Credit charge <a href="#credit-charge" id="credit-charge"></a>

Clearout follows a transparent credit usage model.

* **4** **credits** are charged for a non-role based email address, and **2 credits** are charged for a role-based email address.
* No credits are charged when the result shows email not found.
* In Bulk Finder, exact duplicate entries are not charged.

This ensures predictable usage and cost control at scale. [Click here](https://clearout.io/pricing-guide/) to know the credit charges in detail.

## Supported Integrations <a href="#supported-integrations" id="supported-integrations"></a>

Clearout integrates seamlessly into your existing tech stack.

<table data-view="cards"><thead><tr><th></th></tr></thead><tbody><tr><td><p><a href="/broken/pages/u73SMGFU3ChmJ2Fftnbk"><strong>API</strong></a></p><ul><li>Real-time and bulk finding endpoints</li><li>Built for scale and automation</li><li>Secure and reliable</li></ul></td></tr><tr><td><p><strong>Automations</strong></p><ul><li><a href="../integrations/automation/zapier.md">Zapier</a></li><li><a href="../integrations/automation/make.md">Make</a></li><li><a href="../developers/webhooks/">Webhooks</a></li></ul></td></tr></tbody></table>






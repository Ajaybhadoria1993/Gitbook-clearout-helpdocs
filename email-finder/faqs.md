---
icon: circle-question
---

# FAQs

## General Questions

<details>

<summary>What is a real email address?</summary>

A real email address belongs to a genuine person or organization and can actively send and receive emails. It is associated with a valid mailbox and a configured email domain.

A real email address typically:

* Is connected to a working inbox
* Belongs to an identifiable individual or organization
* Passes domain checks such as **MX record validation**
* Can be validated through **SMTP or mailbox-level verification**

Real email addresses help ensure reliable communication and reduce the chances of spam or bounced emails.

</details>

<details>

<summary>What is an email finder and how does it work?</summary>

An email finder is a tool that helps discover professional email addresses using publicly available data points such as a person’s name and their company domain.

It works by analyzing known email patterns, domain configurations, and multiple data sources to identify the most likely email address associated with a person and organization.

</details>

<details>

<summary>How accurate are email search results?</summary>

The accuracy of email search results depends on factors such as the availability of public data, company email patterns, and domain configurations.

Email finder tools typically provide a confidence score or verification status to indicate how reliable the discovered email address is. In many cases, the results are further validated using email verification techniques to improve accuracy.

</details>

<details>

<summary>What information can I get from an email search?</summary>

An email search result may include details such as:

* The discovered email address
* Verification or deliverability status
* Confidence score
* Domain or company information
* Additional metadata related to the search

These details help users determine whether the email address is suitable for outreach or further verification.

</details>

<details>

<summary>How long does it take to find an email?</summary>

The time required depends on the type of search.

* **Single email searches** typically return results within seconds.
* **Bulk searches** may take longer depending on the number of records being processed and the complexity of the search.

Processing time may also vary based on domain responsiveness and data availability.

</details>

<details>

<summary>Why might an email not be found?</summary>

An email may not be found for several reasons, including:

* The person does not have a publicly identifiable email address
* The company does not follow a predictable email pattern
* The domain restricts external verification or discovery
* Insufficient data is available to generate a reliable result

In such cases, the search may return a “not found” or similar status.

</details>

<details>

<summary>Is the email found guaranteed to be valid?</summary>

No email finder can guarantee that a discovered email address is valid or active.

Because email finder tools generate possible addresses based on available data and patterns, it is recommended to verify the email address using an email verification tool before using it for outreach.

</details>

<details>

<summary>Is it possible to find an email address using a name and company domain?</summary>

Yes. Many email finder tools allow users to search for an email address using a person’s name along with their company domain.

The tool analyzes common email patterns used by the organization to identify the most likely email address associated with that person.

</details>

## Technical Questions

<details>

<summary>Why was an email not found for a contact?</summary>

An email may not be found if the provided information is incomplete, the company domain does not follow predictable email patterns, or no reliable data sources are available to discover the email address.

</details>

<details>

<summary>Can Email Finder be used through an API?</summary>

Yes. Clearout provides an [Email Finder API](https://docs.clearout.io/developers/api/email-finder) that allows developers to integrate email discovery directly into CRMs, applications, or automated workflows. You can also use [webhooks](https://docs.clearout.io/developers/webhooks/webhook-events-and-payloads#email-finder-events) to receive email finder results programmatically in your system once processing is complete.

</details>

## Billing Questions

<details>

<summary>How are Email Finder credits charged?</summary>

Credits are deducted only when an email address is successfully discovered. To find, 4 credits are charged for a non-role based email address, and 2 credits are charged for a role-based email address. For more information, visit our [pricing guide](https://clearout.io/pricing-guide/).

</details>

<details>

<summary>Will credits be deducted if an email is not found?</summary>

No. Credits are only charged when a email address is successfully discovered. If the result returns “**email not found**”, no credits are deducted.

</details>

Visit [Email Finder FAQs](../help-and-support/featured-answered/email-finder.md) to explore detailed answers and guidance.

---
description: Discover professional email addresses instantly in real time
icon: jet-fighter
---

# Instant Finder

As the name suggests, Instant Email Finder is used to get instant results. Once you have created an account, go to Email Finder, enter the prospect's name and the domain/company name, and click on search.&#x20;

<div data-with-frame="true"><figure><img src="../.gitbook/assets/clearout_instant_email_finder_update-2cf8c1b352709cda29739937c3f84288.gif" alt="Instant Email Finder Search and Results Overview" width="563"><figcaption></figcaption></figure></div>

This feature allows you to look up email addresses individually, and the results will be available in a few seconds.

## Where to Find It in App

* Log in to your [**Clearout dashboard**](https://app.clearout.io/dashboard).​
* In the top navigation, go to **Email Finder → Find Email**.​
* The Instant Finder screen displays input fields to enter the **prospect’s name and** **company/domain**, along with a **Search** button to find the email address instantly.

## How It Works

### Input

* Enter the **prospect’s name** in the name field.
* Enter the **company name or domain** in the corresponding input field.
* Click **Search** to start finding the email address.

<figure><img src="../.gitbook/assets/image (1).png" alt="Instant Email Finder Search and Results" width="563"><figcaption></figcaption></figure>

The result will be displayed within a few seconds or it will be available under the [Email Finder History.](instant-finder.md#finder-history-in-activities)

### Reading output <a href="#reading-output" id="reading-output"></a>

For each lookup, Email Finder returns the **discovered email address**, along with its normalized **name, company,** **email address**, and **confidence score** to help you understand the quality of the result.

Any email lookup done using Instant Finder reflects the result in the history table of the email finder. The email lookup details are retained for only 30 days. It comes with a download option too.

Any lookup with the status **"In-progress"** will be added to the history and populated automatically.

### Limits

* Instant Email Finder is designed for looking up email addresses for individual prospects.
* It is best suited for **quick discovery** rather than processing large lists.
* For discovering email addresses at scale, use [**Bulk Email Finder**](bulk-finder.md).

## Email Finder History <a href="#email-finder-history" id="email-finder-history"></a>

The **Email Finder History** section provides an audit trail of all instant email lookups.​

<div data-with-frame="true"><figure><img src="../.gitbook/assets/ef-history.png" alt="Instant Email Finder History"><figcaption></figcaption></figure></div>

* Columns include **Name**, **Company**, **Email Address**, **Confidence Score**, and **Date**.​
* You can:
  * Filter by **Created On** date range (for example, “Last 7 days”).​
  * Filter by **Status** (e.g., All / Completed / In Progress).​
  * Search by **Name / Company** using the search box above the table.​
  * Export the results using the download icon.​

## Download discovered email <a href="#verification-history-in-activities" id="verification-history-in-activities"></a>

All Instant Email Finder runs are logged in the [**Activities**](https://app.clearout.io/activities) section.​

* In the top navigation, go to **More → Activities.**
* Filter by **Email Finder** to see past runs.​
* Download the report (for example, CSV) and open it in your preferred tool to review or share results.​

{% hint style="info" %}
**Developer note**

Want to automate email discovery? Refer to the [Email Finder API](/broken/pages/7b22d5e21f842be901bf681c46a3ffd0b7aa734c#post-email_finder-instant) section for sample code and integration details.
{% endhint %}

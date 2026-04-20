---
description: Find verified emails at scale with Bulk Finder.
icon: weight-hanging
---

# Bulk Finder

The Clearout Bulk Email Finder is used to discover email addresses in bulk and download enriched results with confidence scores. **The bulk finder efficiently handles the simultaneous processing of hundreds or thousands of prospects, optimizing scalability**.

It provides flexibility by accommodating CSV or Excel data uploads and downloads. Intelligent functionalities, including automatic duplicate identification, quality metrics, and deliverability insights, guarantee data precision.

By preventing charges for duplicate or missing records, the solution encourages efficient use and aids in cost management.

## Where to Find It in App <a href="#where-to-find-it-in-app" id="where-to-find-it-in-app"></a>

* Log in to your [**Clearout dashboard**.](https://app.clearout.io/dashboard/)​
* In the top navigation, go to **Email Finder →** [**Add List**](https://app.clearout.io/email-finder/add-list).​
* Click **Add List** and upload your file (CSV/XLSX) to start bulk email finding.

## **Supported File Types**

| Format    | Details                                 | Sample Files                                          |
| --------- | --------------------------------------- | ----------------------------------------------------- |
| **.csv**  | Comma-separated value files             | [CSV](https://clearout.io/sample/email-finder/csv/)   |
| **.xlsx** | Excel workbook (first sheets supported) | [XLSX](https://clearout.io/sample/email-finder/xlsx/) |

### **Required Columns**

Your file **must include** these two columns:

<table><thead><tr><th width="170.2265625">Column</th><th width="304.68359375">Description</th><th>Example</th></tr></thead><tbody><tr><td><strong>Name</strong></td><td>Prospect's full name or first name</td><td>"John Smith" or "John"</td></tr><tr><td><strong>Domain/Company</strong></td><td>Company domain or company name</td><td>"microsoft.com" or "Microsoft"</td></tr></tbody></table>

{% hint style="info" %}
#### **Optional Columns**

You can add any additional columns you want and they'll be preserved in your results:

* Job Title
* Location
* Department
* Source
* Custom fields
* Any other data
{% endhint %}

### **File Size & Limits**

* **Maximum file size:** No strict limit (process files with millions of records)
* **Recommended:** For faster processing, consider splitting very large files (100k+ records) into multiple batches

## **Start Email Finding**

{% stepper %}
{% step %}
Click **Email Finder →** [**List**](https://app.clearout.io/email-finder/lists)**.​**
{% endstep %}

{% step %}
Find your uploaded list
{% endstep %}

{% step %}
Click the **"Find Emails"** butto&#x6E;**,** and processing begins!
{% endstep %}
{% endstepper %}

**Processing time depends on:**

* Number of records
* Current system load
* Data quality

You can close the page; the email finding process will continue in the background, and you will receive an email notification immediately after it is completed.

## Cancel Finding

Did you initiate the bulk email finding for the wrong file? Don't worry, Clearout supports cancellation of the file **"in progress".**

* By cancelling email finding, credits will be charged for any found email addresses, while unfound email addresses will be listed as 'Not found' with the reason 'Request Cancelled' without being charged.
* In some cases, cancelling the request may take up to 15 minutes to complete.

## **Duplicate File Identification**

Clearout **automatically assesses** whether a file upload has been run to find email addresses previously or not and tells you when a **duplicate file** is uploaded for email finding so you can confirm. This function is supported in the WebApp & API for the Email Finder.

## **Download Discovered List**

The results can be downloaded in .csv and .xlsx formats by clicking on 'Download' button

If you encounter any difficulty locating the downloaded result, please consider trying these steps. Try these

* Please check the 'Download' folder on your system.
* Please clear the 'cache' and try the download once more.
* Check browser pop-up blockers enabled
* Try downloading in "incognito" mode.
* Use a different browser
* [Contact us](../help-and-support/ask-a-question.md) if the issue continues to occur

{% hint style="info" %}
For large files, the download link will be shared over the registered email.
{% endhint %}

### Status <a href="#status_1" id="status_1"></a>

The status provides a broad picture of the quality of the email addresses found.

<table><thead><tr><th width="185.28125">Primary Status</th><th>Description</th></tr></thead><tbody><tr><td>Found</td><td>This status shows that the email finder has successfully found the email address of the ideal prospect.</td></tr><tr><td>Not Found</td><td>This status indicates that the email finder was unable to find the ideal prospect's email address, and it will mention the reason.</td></tr></tbody></table>

### Understanding Email Finding Results <a href="#understanding_email_finding_results" id="understanding_email_finding_results"></a>

#### Important Terms Related to The Results <a href="#important_terms_related_to_the_results" id="important_terms_related_to_the_results"></a>

<table><thead><tr><th width="220.03125">Name</th><th>Description</th></tr></thead><tbody><tr><td>Business Account</td><td>The appended columns show if an email address belongs to a business account.</td></tr><tr><td>Duplicate</td><td><p>Any email list with the same data (first name, last, name, domain/company name) more than once, leading to the same result, is categorized as duplicates.</p><p><br>The user will not be charged for the duplicates.</p></td></tr><tr><td>Confidence Level</td><td>An email deliverability scale that indicates how good the discovered email addresses are for a list and how good the list can be for cold email outreach campaigns. Categorized as high, medium, and low.</td></tr><tr><td>Confidence Score</td><td>An AI-based percentile allotted to each email address that indicates the accuracy level with which the discovered email address matches the lead in the query.</td></tr></tbody></table>

### **Result File Headers**

<table><thead><tr><th width="307.1171875">Name</th><th>Description</th></tr></thead><tbody><tr><td>Clearout Finder Full Name</td><td>Displays the full name used for the email finding on Clearout.</td></tr><tr><td>Clearout Finder First Name</td><td>Displays the first name used for the email finding on Clearout.</td></tr><tr><td>Clearout Finder Last Name</td><td>Displays the last name used for the email finding on Clearout.</td></tr><tr><td>Clearout Finder Domain</td><td>Displays the domain associated with the prospect.</td></tr><tr><td>Clearout Finder Company</td><td>Displays the name of the company associated with the prospect.</td></tr><tr><td>Clearout Finder Email Address</td><td>Displays the email address found by Clearout Email Finder.</td></tr><tr><td>Clearout Finder Confidence Score</td><td>Displays the Confidence score in form of numbers that may be different for each email address.</td></tr><tr><td>Clearout Finder Business Account</td><td>Displays if the found email address is a business account or not. The result is in the form of 'Yes' or 'No'.</td></tr><tr><td>Clearout Finder Status</td><td>Displays if Clearout was able to find an email address for the input.</td></tr><tr><td>Clearout Finder Reason</td><td>Provides more information about the status of the email found or the reason for not able to find an email address.</td></tr><tr><td>Clearout Finder Processed At (UTC)</td><td>Provides the exact time at which the email address was found.</td></tr></tbody></table>

## **Finder List Analysis**

This brief and quick analysis offers an instant review of the overall email finder result before downloading the actual detailed result.

#### The information it provides

* Percentage and count of the emails found.
* Total counts for 'Duplicate' and 'Business Accounts'

#### On the left, you will find a brief overview of the list.

* The name of the list
* The list includes the date of creation and the date of processing.
* Time taken for finding the results
* Total number of inputs in the list
* Billable count indicates the credits have been used.
* The Confidence Level is an email deliverability scale that indicates the quality of the discovered email addresses on a list and their effectiveness for cold email outreach campaigns. It can be high, low, or moderate depending on the quality of data provided

## **Remove List** <a href="#remove-list" id="remove-list"></a>

Bulk finder list files can be deleted either before or after finding email addresses by using the 'bin' icon next to the list name.

> Files cannot be deleted while finding is in progress

## Data Retention & Result File Availability <a href="#data-retention--file-availability" id="data-retention--file-availability"></a>

### **Retention Period**

* Input list and result files are retained for **30 days** from the date of processing
* After 30 days, input and result files are automatically deleted from the system

### **Email Notifications**

Clearout will send automated email notifications:

* **Day 25:** First reminder - "Your Bulk Finder results will be deleted in 5 days"
* **Day 29:** Final reminder - "Your Bulk Finder results will be deleted in 1 day"

**What You Should Do**

To preserve results beyond 30 days:

* Download result files within 30 days of processing
* Save files locally or to cloud backup storage
* Export to your CRM or third-party systems using integrations
* Use the API for programmatic data storage

### **After Deletion**

* Results cannot be recovered or re-downloaded from the platform
* You will need to rerun the bulk finder to get results again
* All associated metadata and analysis will also be removed

{% hint style="info" %}
**Developer note**

Want to automate this? Use the [Bulk Finder API](/broken/pages/7b22d5e21f842be901bf681c46a3ffd0b7aa734c#post-email_finder-bulk) to run the same bulk email finding from your application
{% endhint %}

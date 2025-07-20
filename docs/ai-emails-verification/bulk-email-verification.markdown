---
layout: page
title: "Bulk Email Verification" 
permalink: /docs/bulk-email-verification/
nav_order: 5
parent: "AI Powered Email Verification"
published: May 21, 2024
updated: May 23, 2025
---

# {{page.title}}

<div style="font-size:0.78em;color: #797878; margin-bottom:1.5em;">
     <span>Updated on {{page.updated}}</span>
    <span style="margin-left:2em;">Published on {{page.published}}</span>
</div>

<hr style="border:none;height:3px;background-color:#e0e0e0;margin:0;">
<hr style="border:none;height:3px;background-color:#bebebe;margin-top:0.2em;margin-bottom:1.5em;">


{: .important }
> Current Limits for Bulk Email Verification:
> * The maximum limit for a single batch of email verification is 50,000 emails or fewer.
> * If you need to verify more than 50,000 emails, you can process them in multiple batches, with each batch containing no more than 50,000 emails.
> * You may submit up to three batches per day under this default limit.
> <br><br>
>    → Need a Higher Limit?
>    This limit can be increased on a case-by-case basis. If you require a higher quota, please contact our team at help@dataoorts.com to request an increase.
><br><br>
>    → Single Email Verification:
>    There are no limits for single email verification—verify as many emails as you need, asynchronously!
>

{: .highlight }
> For interactive web-based bulk email verification, the currently accepted file types are TXT, XLSX, and CSV. If you need access to additional file types,
> please request it Here. Ensure that your file contains only a single column or single row of email addresses.

{: .important }
> The cost of email verification is $0.0001 per email. Ensure your account has sufficient balance for bulk email verification.

## To verify bulk emails, Visit [Here](https://mails.dataoorts.com/batch) and follow these steps:
* **Get Your API Key** – Obtain your Unify API key from [Here](https://cloud.dataoorts.com/unify_api) and paste it into the [API Section](https://mails.dataoorts.com/batch) to validate your Dataoorts account.
* **Upload Your File** – Select the file containing the Emails(Less than 50K)—Upload, then press Submit to begin processing.

![Bulk Email Verification WebUI - Hosted in Hugging Face](bulk_email_verification.png)

* **Save Your Job ID** – After initial checks, your batch job ID will be returned, and your email-file will enter the processing queue. Since this ID is volatile due to enhanced security, Ensure you Save it somewhere in secure place for fetching the job result.
* **Wait Briefly** – Take a short break, Perhaps enjoy a cup of tea.
* **Retrieve Results** – Visit Here, Enter your Unify API Key and job ID, and access the verified emails in JSON format, ready for download.

![Bulk Email Verification WebUI - Hosted in Hugging Face](bulk_email_verification_2.png)

{: .important }
>Developers: Bulk Email Verification API
> If you're searching for an API, we also offer access to all our services with api, Including AI-powered bulk email verification. Get the API documentation [Here](https://dataoorts.document360.io/v1/docs/api-email-verification).
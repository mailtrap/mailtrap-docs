---
title: Retool and Mailtrap Integration
description: Step-by-step guide on how to integrate Mailtrap with your Retool application to send emails via REST API.
---

# Overview

This guide shows you how to integrate Mailtrap with your Retool application to send emails.

Mailtrap is an email-sending solution for developer and product teams. Focused on fast delivery and high inboxing rates for transactional and promo emails. Provides highly customizable API and 24/7 tech support.

## Prerequisites

- A Retool account and a project
- A Mailtrap account for sending emails

## Step 1: Create a REST API resource (Mailtrap)

Open Retool and go to the **Resources** tab. Once there, click on **Create new** > **Resource**.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/retool-resources-create-new.png" alt="Retool Resources tab showing Create new dropdown with Resource option" width="563"><figcaption><p>Create new Resource in Retool</p></figcaption></figure></div>

On the next page, select **REST API**.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/retool-rest-api-select.png" alt="Retool resource type selection showing REST API option" width="563"><figcaption><p>Select REST API</p></figcaption></figure></div>

Then, configure the resource:

- Enter your desired resource name
- Add the Mailtrap root URL: `https://send.api.mailtrap.io/`
- Choose **Bearer** for authentication and add your [Mailtrap API key](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/account-and-organization/api-tokens)

{% hint style="info" %}
This URL lets you use other endpoints later on depending on your use case (i.e., create contacts). If you plan on sending mass emails, the root URL should be `https://bulk.api.mailtrap.io/`
{% endhint %}

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/retool-rest-api-config.png" alt="Retool REST API resource configuration with Mailtrap URL and Bearer authentication" width="563"><figcaption><p>REST API resource configuration</p></figcaption></figure></div>

Once you insert the required details, click **Save changes** and go back to your project.

## Step 2: Configure a query

As the next step, add a query to the Query Library. Queries stored here can be reused across any of your Retool apps.

In this example, we'll create a query that sends an email with fixed content defined in the query settings. However, you can use any Mailtrap endpoint with Retool such as managing contacts, updating email templates, or sending messages to a sandbox. For more information, check the official [Mailtrap API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api).

Create a new **Query** and:

- Select the resource you created that connects the Mailtrap email API
- Choose **POST** and add the API endpoint: `api/send`
- Add a **Content-Type** header with `application/json` as value
- Choose **RAW** as the Body type and use the following code snippet:

{% code title="Request Body" %}
```json
{
  "from": {
    "email": "hello@yourdomain.com"
  },
  "to": [
    {
      "email": "recipient@example.com"
    }
  ],
  "subject": "Hello from Retool",
  "text": "Lorem ipsum"
}
```
{% endcode %}

{% hint style="warning" %}
This is just an example body for sending emails from a simple form. Feel free to adjust it according to your needs. Make sure to use your 'from' address with a verified sending domain.
{% endhint %}

Here's what your new query should look like:

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/retool-query-config.png" alt="Retool Query editor showing POST request configuration with Mailtrap API endpoint and JSON body" width="563"><figcaption><p>Query configuration</p></figcaption></figure></div>

## Step 3: Test the integration

Finally, to test your configuration, click on the **Test** button in the upper-right corner of the Query editor. You should see the following response:

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/retool-test-response.png" alt="Retool Query editor showing successful API response after test" width="563"><figcaption><p>Successful test response</p></figcaption></figure></div>

Here it is in the Gmail inbox:

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/retool-email-received.png" alt="Gmail inbox showing received email from Retool integration" width="563"><figcaption><p>Email received in Gmail</p></figcaption></figure></div>

And here it is in the [Email Logs](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/statistics/email-logs) tab in the Mailtrap dashboard:

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/retool-email-logs.png" alt="Mailtrap Email Logs showing sent email details from Retool" width="563"><figcaption><p>Email in Mailtrap Email Logs</p></figcaption></figure></div>

{% hint style="success" %}
If you plan on collecting email addresses for a list, you can connect your Retool project with [Mailtrap Contacts](https://mailtrap.io/mailtrap-contacts/) and store your addresses in the Mailtrap dashboard automatically. For reference, check out the official [Mailtrap Contacts API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/0a35b03ff78c5-contacts-api).
{% endhint %}

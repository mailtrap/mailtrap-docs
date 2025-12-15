---
title: API integration
description: >-
  Integrate Mailtrap email API. Get API credentials, choose transactional or
  bulk sending, use SDKs or code samples, and start sending.
icon: plug
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# API Integration

Use API credentials to integrate Mailtrap with your project.

{% stepper %}
{% step %}
**Choose your sending domain**

Go to the Sending Domains tab and choose the domain you want to send emails from. Remember that you'll be able to start sending emails once the domain is verified.
{% endstep %}

{% step %}
**Open the Integration tab**

Navigate to the Integration tab for your selected domain.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (3) (1).png" alt="" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
**Select your stream type**

Click the Integrate button under Transactional Stream or Bulk Stream.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (4).png" alt="" width="375"><figcaption></figcaption></figure></div>

Transactional Stream is used to send automated, non-promotional application emails triggered by the specific user action.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (5).png" alt="" width="563"><figcaption></figcaption></figure></div>

Bulk Stream is used to send a single marketing campaign to a large group of recipients in bulk.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (6).png" alt="" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
**Switch to API**

Toggle the switch to API.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/api-integration-credentials-streams.png" alt="" width="563"></div>
{% endstep %}

{% step %}
**Configure your integration**

Build the authenticated HTTP request in your programming language or framework and configure it with Mailtrap Host and API Token.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/api-integration-credentials-transactional.png" alt="Transactional Stream API credentials showing Host and API Token" width="563"><figcaption><p>Transactional Stream API credentials</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/api-integration-credentials-bulk.png" alt="Bulk Stream API credentials showing Host and API Token" width="563"><figcaption><p>Bulk Stream API credentials</p></figcaption></figure></div>

Alternatively, choose the programming language or framework from the menu under Code Samples and copy the sample configuration already containing your credentials. In this menu, you'll find official SDKs for [PHP](https://github.com/railsware/mailtrap-php), [Python](https://github.com/railsware/mailtrap-python), [Ruby](https://github.com/railsware/mailtrap-ruby), and [Node.js](https://github.com/railsware/mailtrap-nodejs).

{% hint style="info" %}
Note: For now, only Ruby, PHP (Laravel + Symfony), and Node.js SDKs support Bulk Stream, but others are in development. Request and response examples are also available [here](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/67f1d70aeb62c-send-email-including-templates).
{% endhint %}

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/api-integration-code-samples-transactional.png" alt="Code Samples dropdown showing programming languages including cURL, C++, C#, Go, Java, Node.js, Ruby, Python, and PHP" width="563"><figcaption><p>Transactional Stream code samples</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/api-integration-code-samples-bulk.png" alt="Code Samples dropdown for Bulk Stream showing available programming languages and frameworks" width="563"><figcaption><p>Bulk Stream code samples</p></figcaption></figure></div>
{% endstep %}

{% step %}
**Test your integration**

Complete your script and run it. If you did everything correctly, you should find the sent email in the inbox of the email address you indicated in the script. The email will also appear in Email Logs in Mailtrap.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (7).png" alt="" width="563"><figcaption></figcaption></figure></div>
{% endstep %}
{% endstepper %}

Remember that each domain has different API tokens that you can always access by clicking on the desired domain and going to the Integration tab.

You can also create additional API tokens by going to Settings → API Tokens and clicking Add Token.

<a href="../account-and-organization/privacy-and-security/api-tokens.md" class="button primary" data-icon="magnifying-glass">Learn more about API Tokens</a>

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/api-tokens-add-token.png" alt="API Tokens page with Add Token button highlighted" width="563"></div>

Mailtrap Email Sending API supports:

* attachments
* [email templates](email-sandbox/email-marketing/email-templates.md)
* [custom variables](custom-variables.md)
* [email categories](analytics/categories.md)

{% hint style="info" %}
If you need any help with API integration, please, contact our support team at [support@mailtrap.io](mailto:support@mailtrap.io).
{% endhint %}

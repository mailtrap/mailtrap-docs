---
title: SMTP integration
description: >-
  Integrate Mailtrap SMTP. Get SMTP credentials, choose transactional or bulk
  sending, use code samples, and start sending.
icon: envelope-open
---

# SMTP Integration

Learn how to integrate your application via SMTP.

### Locating your Mailtrap credentials

{% stepper %}
{% step %}
Go to the **Sending Domains** tab and choose the domain you want to send emails from.&#x20;

Keep in mind that the [domain must be verified](https://docs.mailtrap.io/email-api-smtp/setup/sending-domain) in order for you to start sending emails.

<figure><img src="../.gitbook/assets/Screenshot 2026-02-20 at 10.26.54.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Navigate to the **Integrations** tab for your selected domain and select whether you want to use our **Transactional Stream** or [**Bulk Stream**](https://docs.mailtrap.io/email-api-smtp/setup/bulk-stream).

<figure><img src="../.gitbook/assets/Screenshot 2026-02-20 at 10.29.17.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Transactional Stream** is used to send automated, non-promotional application emails that are triggered by the user's specific action.

**Bulk Stream** is used to send a single marketing campaign to a large group of recipients in bulk.
{% endhint %}
{% endstep %}

{% step %}
Once you choose your preferred sending stream, click on **SMTP**. There, you will be able to see your Mailtrap credentials.

<figure><img src="../.gitbook/assets/Screenshot 2026-02-20 at 10.32.53.png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

### Method #1. Manual SMTP configuration

If you're using a tool like WordPress or Salesforce, you can simply copy/paste credentials such as **Host**, **Port**, **Username**, and **Password**. Here are some examples:

{% tabs %}
{% tab title="WordPress" %}
If you want to send emails from WordPress, you can use one of the many plugins (e.g., WP Mail SMTP or Post SMTP). For example, if you are using WP Mail SMTP, you can just navigate to the settings page and insert the Mailtrap credentials there.

<figure><img src="../.gitbook/assets/wordpress smtp.png" alt="" width="375"><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Salesforce" %}
To send emails from Salesforce, simply add your Mailtrap credentials to your Email Relay configuration, just like so:

<figure><img src="../.gitbook/assets/smtp salesforce.png" alt="" width="563"><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

### Method #2. Copy/pasting code samples

If you have a programming project, you can also copy/paste one of the pre-made code samples for various programming languages and frameworks. For instance:

{% tabs %}
{% tab title="Nodemailer" %}
For Nodemailer, all you need to do is copy/paste the pre-made transporter object from Mailtrap into your main configuration file (i.e., **index.js**).

```javascript
var transport = nodemailer.createTransport({
  host: "live.smtp.mailtrap.io",
  port: 587,
  auth: {
    user: "api",
    pass: "<YOUR_API_TOKEN>"
  }
});
```
{% endtab %}

{% tab title="Laravel" %}
Similarly, for Laravel, you can just copy the code snippet from Mailtrap into your **.env** file:

```php
MAIL_MAILER=smtp
MAIL_HOST=live.smtp.mailtrap.io
MAIL_PORT=587
MAIL_USERNAME=api
MAIL_PASSWORD=<YOUR_API_TOKEN>
```
{% endtab %}
{% endtabs %}

### Verifying your configuration

Once you add Mailtrap SMTP to your project, try sending an email from the tool of your choice or the project you're working on. If you did everything correctly, you should find the sent email in the inbox of the email address you indicated in the script. The email will also appear in the [Mailtrap Email Logs](https://docs.mailtrap.io/email-api-smtp/analytics/logs).

<figure><img src="../.gitbook/assets/Screenshot 2026-02-20 at 11.06.56.png" alt=""><figcaption></figcaption></figure>

Remember that each domain has different SMTP credentials that you can always access by clicking on the desired domain and going to the **Integrations** tab.

You can also create additional API tokens (or SMTP passwords) by going to **Settings** → **API Tokens** and clicking **Add Token**.

<a href="setup/api-tokens.md" class="button primary" data-icon="magnifying-glass">Learn more about API Tokens</a>

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/smtp-tokens-add-token.png" alt="" width="563"></div>

{% hint style="info" %}
If you need any help with SMTP integration, please, contact our support team at [support@mailtrap.io](mailto:support@mailtrap.io).
{% endhint %}

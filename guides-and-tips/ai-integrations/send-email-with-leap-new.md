---
title: Leap.new and Mailtrap Integration
description: >-
  Step-by-step guide on how to integrate Mailtrap with your Leap.new application
  to send emails.
---

# Leap.new and Mailtrap

This guide shows you how to integrate Mailtrap with your Leap.new application to send emails.

Mailtrap is an email-sending solution for developer and product teams. Focused on fast delivery and high inboxing rates for transactional and promo emails. Provides highly customizable API and 24/7 tech support.

## Prerequisites

* A Leap.new account and a project
* A Mailtrap account for sending emails

{% stepper %}
{% step %}
### Create a landing page/contact form

Log in to your Leap.new account and use a prompt like the following one to create a simple project with basic fields:

{% hint style="info" %}
create me a simple contact form with email, name, and message fields, and a send button
{% endhint %}
{% endstep %}

{% step %}
### Add your Mailtrap credentials

After a minute or two, Leap.new will generate your project. Once it's done, you need to insert your Mailtrap credentials.

To do this, open **Settings** and navigate to **Secrets**, and click on the **Add new variable** button.

Once there, use the **New secret** button to add the following two variables:

* `MAILTRAP_API_TOKEN` – This is the [Mailtrap API token](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/account-and-organization/privacy-and-security/api-tokens), which you can create at any time in your account dashboard.
* `MAILTRAP_FROM_EMAIL` – This is the email address with the verified Mailtrap sending domain you've added after creating an account.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/leap-new-secrets-settings.png" alt="Leap.new Settings showing Secrets configuration with MAILTRAP variables" width="563"><figcaption><p>Leap.new Secrets settings</p></figcaption></figure></div>

Once you're done adding the variables, simply tell the Leap.new AI that you're done with a prompt like this one:

{% hint style="info" %}
I've added the MAILTRAP\_API\_TOKEN and MAILTRAP\_FROM\_EMAIL secrets
{% endhint %}

The AI will then go over Mailtrap Email API documentation, connect it to your project, and confirm once it's done.

{% hint style="warning" %}
If you haven't already, make sure to let AI know you want the messages to be sent to the address inputted in the email field. For this, you can use a prompt such as:

"I want the message to be sent to the address inputted in the email field, meaning the to field should use the email from the form data"
{% endhint %}
{% endstep %}

{% step %}
### Start sending emails

Finally, to test your configuration, fill out the form and hit the **Send** button. If you followed everything thus far, you should receive the email in your inbox in a few seconds.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/leap-new-email-received.png" alt="Gmail inbox showing received email from Leap.new contact form" width="563"><figcaption><p>Email received in Gmail</p></figcaption></figure></div>

You can also view the email in the [Email Logs](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/statistics/email-logs) tab in the Mailtrap dashboard.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/leap-new-email-logs.png" alt="Mailtrap Email Logs showing the sent email details" width="563"><figcaption><p>Email in Mailtrap Email Logs</p></figcaption></figure></div>
{% endstep %}
{% endstepper %}

{% hint style="success" %}
If you plan on collecting email addresses for a list, you can connect your Leap.new project with [Mailtrap Contacts](https://mailtrap.io/mailtrap-contacts/) and store your addresses in the Mailtrap dashboard automatically. For reference, check out the official [Mailtrap Contacts API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/0a35b03ff78c5-contacts-api).
{% endhint %}

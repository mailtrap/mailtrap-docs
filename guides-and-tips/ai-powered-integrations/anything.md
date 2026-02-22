---
title: Anything and Mailtrap Integration
description: >-
  Step-by-step guide on how to integrate Mailtrap with your Anything application
  to send emails.
---

# Anything

[Anything](https://www.createanything.com/) is an AI agent that can turn your ideas into sites, apps, tools, products, and more with simple prompts. In this article, you’ll learn how to connect it to Mailtrap and add email-sending functionality to your projects.

**Prerequisites**:&#x20;

* Add and [verify your email sending domain](https://docs.mailtrap.io/email-api-smtp/setup/sending-domain) since Mailtrap allows you to send emails only from a verified domain.
* Make sure your [API Token](https://docs.mailtrap.io/email-api-smtp/setup/api-tokens) has admin access level to that domain.

### Step 1. Add your Mailtrap credentials

To add your Mailtrap credentials, open **Project Settings** in the sidebar, navigate to **Secrets**, and click on the **Add new secret** button.

<figure><img src="../.gitbook/assets/any 1.png" alt=""><figcaption></figcaption></figure>

This way, you need to add the following two secrets:

* `MAILTRAP_API_TOKEN`&#x20;

This is the [Mailtrap API token](https://docs.mailtrap.io/email-api-smtp/setup/api-tokens), which you can create at any time from your account. And here’s what the secret should look like:

<figure><img src="../.gitbook/assets/any 2.png" alt=""><figcaption></figcaption></figure>

* `MAILTRAP_FROM_EMAIL`&#x20;

This is the email address with the verified Mailtrap sending domain you’ve added after creating an account. And here’s the secret:

<figure><img src="../.gitbook/assets/any 3.png" alt=""><figcaption></figcaption></figure>

Once you’re done adding the secrets, simply tell the Anything AI that you’re done with a prompt like this one, for example:

> Please use Mailtrap email API for sending emails from my project, I've added the MAILTRAP\_API\_TOKEN and MAILTRAP\_FROM\_EMAIL secrets

The AI will then go over [Mailtrap Email API documentation](https://docs.mailtrap.io/developers), connect it to your project, and confirm once it’s done.

### Step 2. Start sending emails

Once you add your credentials, try sending an email from your project. If you followed everything thus far, you should receive the email in your inbox in a few seconds.

Here it is in a Gmail inbox I used as my `to` address:

<figure><img src="../.gitbook/assets/any 4.png" alt=""><figcaption></figcaption></figure>

And here it is in the [Mailtrap Email Logs](https://docs.mailtrap.io/email-api-smtp/analytics/logs):

<figure><img src="../.gitbook/assets/any 5.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
If you plan on collecting email addresses for a list, you can connect your Anything project with [Mailtrap Contacts](https://mailtrap.io/mailtrap-contacts/) and store your addresses in your Mailtrap account automatically. For reference, check out the official [Mailtrap Contacts API documentation](https://docs.mailtrap.io/developers/promotional/contacts).
{% endhint %}

### Next steps

* Use [Mailtrap Templates](https://docs.mailtrap.io/email-marketing/campaigns/email-templates) to send branded emails with variables.
* Configure [Mailtrap Contacts](https://mailtrap.io/mailtrap-contacts/) to push user information to your Mailtrap Lists, so you can later send campaigns to them or use Automations.
* [Add automation triggers](https://docs.mailtrap.io/email-marketing/automations) in Mailtrap to send follow-ups to new contacts.
* Track open and click rates with [Mailtrap Analytics](https://mailtrap.io/actionable-analytics/).

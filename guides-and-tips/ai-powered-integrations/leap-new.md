---
title: Leap.new and Mailtrap Integration
description: >-
  Step-by-step guide on how to integrate Mailtrap with your Leap.new application
  to send emails.
---

# Leap.new

Leap.new is an AI developer agent that lets you build and deploy production-grade applications directly to your own cloud on AWS & GCP. In this guide, you’ll learn how to integrate it with Mailtrap and add email-sending capabilities to your Leap.new projects.

**Prerequisites**:&#x20;

* A Leap.new account and a project.
* A Mailtrap account for sending emails.

### Step 1. Add your Mailtrap credentials

To add your Mailtrap credentials, open **Settings**, navigate to **Secrets**, and click on the **New secret** button.

<figure><img src="../.gitbook/assets/leap new 1.png" alt=""><figcaption></figcaption></figure>

This way, you need to add the following two variables:

* `MAILTRAP_API_TOKEN` – This is the [Mailtrap API token](https://docs.mailtrap.io/email-api-smtp/setup/api-tokens), which you can create at any time in your account.
* `MAILTRAP_FROM_EMAIL` – This is the email address with the verified Mailtrap sending domain you’ve added after creating an account.

<figure><img src="../.gitbook/assets/leap new 2.png" alt=""><figcaption></figcaption></figure>

Once you’re done adding the variables, simply tell the Leap.new AI that you’re done with a prompt like this one, for example:

> Please use Mailtrap email api for sending, I've added the required environment variables

The AI will then go over [Mailtrap Email API documentation](https://docs.mailtrap.io/developers), connect it to your project, and confirm once it’s done.

### Step 2. Start sending emails

Finally, to test your configuration, try sending an email from your project. If you followed everything thus far, you should receive the email in your inbox in a few seconds. Here it is in a Gmail inbox I used as my `to` address:

<figure><img src="../.gitbook/assets/leap new 3.png" alt=""><figcaption></figcaption></figure>

And here it is in the Mailtrap [Email Logs](https://docs.mailtrap.io/email-api-smtp/analytics/logs).

<figure><img src="../.gitbook/assets/Leap new 4.png" alt=""><figcaption></figcaption></figure>

**Before you go**: If you want to collect email addresses for a list, you can connect your Leap.new project with [Mailtrap Contacts](https://docs.mailtrap.io/email-marketing/contacts/overview) and store your addresses in the Mailtrap Lists automatically. For reference, check out the official [Mailtrap Contacts API documentation](https://docs.mailtrap.io/developers/email-marketing/overview).

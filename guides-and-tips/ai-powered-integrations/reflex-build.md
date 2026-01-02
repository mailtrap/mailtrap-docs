---
title: Reflex Build and Mailtrap Integration
description: >-
  Step-by-step guide on how to integrate Mailtrap with your Reflex Build
  application to send emails.
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

# Reflex Build

Reflex Build is an AI-powered development tool that enables you to create full-stack web apps, dashboards, and components through natural language prompts. In this guide, you’ll learn how to integrate it with Mailtrap and add email-sending capabilities to your Reflex projects.

Prerequisites:&#x20;

* A Reflex Build account and a project.
* A Mailtrap account for sending emails.

### Step 1. Add your Mailtrap credentials

To add your Mailtrap credentials, open **Settings** in the sidebar, navigate to **Secrets**, and click on the **Add new variable** button.

<figure><img src="../.gitbook/assets/reflex build 1.png" alt=""><figcaption></figcaption></figure>

This way, you need to add the following two variables:

* `MAILTRAP_API_TOKEN`&#x20;

This is the [Mailtrap API token](https://help.mailtrap.io/article/103-api-tokens), which you can create at any time in your account under **Settings** → **API Tokens**. And here’s what the variable should look like:

<figure><img src="../.gitbook/assets/reflex build 2.png" alt=""><figcaption></figcaption></figure>

* `MAILTRAP_FROM_EMAIL`&#x20;

This is the email address with the verified Mailtrap sending domain you’ve added after creating an account. And here’s the variable:

<figure><img src="../.gitbook/assets/reflex build 3.png" alt=""><figcaption></figcaption></figure>

Once you’re done adding the variables, simply tell the Reflex Build AI that you’re done with a prompt like this one, for example:

> Please use Mailtrap email api for sending, I've added the required environment variables

The AI will then go over [Mailtrap Email API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api), connect it to your project, and confirm once it’s done.

### Step 2. Start sending emails

Finally, to test your configuration, try sending an email from your project. If you followed everything thus far, you should receive the email in your inbox in a few seconds. Here it is in a Gmail inbox I used as my `to` address:

<figure><img src="../.gitbook/assets/reflex logs to.png" alt=""><figcaption></figcaption></figure>

And here it is in the Mailtrap [Email Logs](https://help.mailtrap.io/article/71-email-logs):

<figure><img src="../.gitbook/assets/reflex email logs.png" alt=""><figcaption></figcaption></figure>

Before you go: If you plan on collecting email addresses for a list, you can connect your Reflex Build project with [Mailtrap Contacts](https://mailtrap.io/mailtrap-contacts/) and store your addresses in the Mailtrap Lists automatically. For reference, check out the official [Mailtrap Contacts API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/0a35b03ff78c5-contacts-api).

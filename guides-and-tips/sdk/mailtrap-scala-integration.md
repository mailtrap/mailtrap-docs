---
title: <i class="fa-code">:code:</i> Mailtrap Scala Integration
description: Learn how to integrate Mailtrap with Scala apps and projects for email sending using SMTP and RESTful API methods.
---

# Overview

Mailtrap can be integrated with Scala apps and projects for email sending.

# Email API/SMTP for Scala

## SMTP integration

To integrate SMTP with your Scala app, navigate to the **Integrations** tab and copy-paste the credentials or ready-made code snippets.

{% hint style="info" %}
You'll have to use Play-Mailer configuration, as Scala doesn't have built-in support for SMTP sending.
{% endhint %}

![Mailtrap SMTP integration for Scala with Play-Mailer configuration](../../../.gitbook/assets/mailtrap-scala-integration-smtp.png)

Read more about SMTP integration in the [SMTP Integration guide](../../documentation/email-api-smtp/smtp-integration.md).

## RESTful integration

To integrate Mailtrap using RESTful API, simply copy/paste the API endpoint and API Token into the configuration file of a Scala framework or library that supports HTTP requests.

For more details, refer to the [API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api).

![Mailtrap RESTful API integration for Scala](../../../.gitbook/assets/mailtrap-scala-integration-api.png)

Read more about API integration in the [API Integration guide](../../documentation/email-api-smtp/api-integration.md).

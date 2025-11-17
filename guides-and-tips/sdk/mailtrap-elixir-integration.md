---
title: <i class="fa-flask">:flask:</i> Mailtrap Elixir Integration
description: Learn how to integrate Mailtrap with your Elixir applications using SDK, SMTP, or RESTful API for email sending
---

# Overview

Mailtrap can be integrated with Elixir apps and projects for email sending.

# Email API/SMTP for Elixir

## SDK integration

You can integrate Mailtrap into your Elixir project or application using the [official SDK](https://github.com/railsware/mailtrap-elixir). The SDK offers access to Transactional Stream, Email Testing, and Account Management.

## SMTP integration

To integrate SMTP with your Elixir app, navigate to the Integrations tab and copy-paste the credentials.

{% hint style="info" %}
SMTP integration is compatible with any Elixir framework or library that sends emails via SMTP.
{% endhint %}

![SMTP credentials for Elixir integration](../../../.gitbook/assets/mailtrap-elixir-integration-smtp-credentials.png)

Read more about SMTP integration in the [SMTP Integration guide](../../documentation/email-api-smtp/smtp-integration.md).

## RESTful API integration

To integrate Mailtrap using RESTful API, simply copy/paste the API endpoint and API Token into the configuration file of the Elixir framework or library that supports HTTP requests. For more details, refer to the [API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api).

![API credentials for Elixir integration](../../../.gitbook/assets/mailtrap-elixir-integration-api-credentials.png)

Read more about API integration in the [API Integration guide](../../documentation/email-api-smtp/api-integration.md).

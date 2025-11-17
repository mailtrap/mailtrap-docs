---
title: Mailtrap Node.js Integration
description: Learn how to integrate Mailtrap with Node.js applications using SDK, SMTP, or RESTful API for email sending.
---

Mailtrap can be integrated with Node.js apps for email sending purposes with SDK, SMTP, and RESTful API.

# Email API/SMTP for Node.js

## SDK integration

To integrate Mailtrap into your Node.js project, you can use the [official SDK](https://github.com/railsware/mailtrap-nodejs), which gives you access to both Transactional and Bulk Streams, and Templates. You can install it either via yarn or npm.

## SMTP integration

To integrate SMTP with your Node.js app, navigate to the **Integration** tab under Sending Domains and copy/paste the ready-made code snippet or credentials.

Note that you'll have to use Nodemailer, as Node.js doesn't have built-in support for SMTP sending.

<figure><img src="../.gitbook/assets/mailtrap-nodejs-smtp-integration.png" alt="Mailtrap SMTP integration interface showing Node.js code sample with Nodemailer transport configuration including host, port, authentication credentials, and STARTTLS requirement"><figcaption><p>SMTP Integration for Node.js</p></figcaption></figure>

Read more about SMTP integration in the [Email API/SMTP - SMTP Integration](../../documentation/sending/smtp-sending/smtp-integration.md) article.

## RESTful API integration

To integrate Mailtrap using RESTful API, use the sample configuration among **Code samples** under the API section.

API integration can be used with any Node.js framework or library that supports HTTP requests. For more details, refer to the [API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api).

<figure><img src="../.gitbook/assets/mailtrap-nodejs-api-integration.png" alt="Mailtrap API integration interface showing Node.js code sample with API host endpoint, API token, Mailtrap client initialization, and email sender configuration"><figcaption><p>API Integration for Node.js</p></figcaption></figure>

Read more about API integration in the [Email API/SMTP - API Integration](../../documentation/sending/api-sending/api-integration.md) article.

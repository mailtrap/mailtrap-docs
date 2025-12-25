---
title: Mailtrap Documentation
description: >-
  Complete email infrastructure for developers. Send production emails, test in
  sandbox, and run email campaigns - all in one platform.
icon: house
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

# Documentation

Build, test, and send emails with confidence using Mailtrap's comprehensive email platform designed for developers and product teams.

## Official SDKs

Get started quickly with our official SDKs for your favorite programming language.

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><i class="fa-node-js">:node-js:</i> <strong>Node.js</strong></td><td><em>Official Node.js SDK for Mailtrap</em></td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/sdk/nodejs">Node.js</a></td><td></td></tr><tr><td><i class="fa-php">:php:</i> <strong>PHP</strong></td><td><em>Official PHP SDK for Mailtrap</em></td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/sdk/php">PHP</a></td><td></td></tr><tr><td><i class="fa-gem">:gem:</i> <strong>Ruby</strong></td><td><em>Official Ruby SDK for Mailtrap</em></td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/sdk/ruby">Ruby</a></td><td></td></tr><tr><td><i class="fa-microsoft">:microsoft:</i> <strong>.NET</strong></td><td><em>Official .NET SDK for Mailtrap</em></td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/sdk/dotnet">.NET</a></td><td></td></tr><tr><td><i class="fa-java">:java:</i> <strong>Java</strong></td><td><em>Official Java SDK for Mailtrap</em></td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/sdk/java">Java</a></td><td></td></tr><tr><td><i class="fa-python">:python:</i> <strong>Python</strong></td><td><em>Official Python SDK for Mailtrap</em></td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/sdk/python">Python</a></td><td></td></tr><tr><td><i class="fa-laravel">:laravel:</i> <strong>Laravel</strong></td><td><em>Laravel integration with Mailtrap PHP SDK</em></td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/sdk/php">PHP</a></td><td></td></tr><tr><td><i class="fa-symfony">:symfony:</i> <strong>Symfony</strong></td><td><em>Symfony integration with Mailtrap PHP SDK</em></td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/sdk/php">PHP</a></td><td></td></tr></tbody></table>

{% columns %}
{% column %}
**Get started in 5 Minutes**

Setting up Mailtrap should be the easiest part of your email journey. With clear endpoints, copy-paste-ready examples, and instant authentication, you'll send your first email in minutes — not hours.

No guesswork, no complexity — just your first successful email, fast.

[Get started](getting-started/email-api-smtp.md) [API reference](https://api-docs.mailtrap.io/)
{% endcolumn %}

{% column %}
{% code title="index.js" overflow="wrap" %}
```javascript
// Send your first email
const { MailtrapClient } = require("mailtrap");

const client = new MailtrapClient({
  token: "YOUR_API_TOKEN"
});

await client.send({
  from: { email: "hello@example.com" },
  to: [{ email: "user@example.com" }],
  subject: "Hello from Mailtrap!",
  text: "Welcome to Mailtrap Email API"
});
```
{% endcode %}
{% endcolumn %}
{% endcolumns %}

## Quick start guides

Choose your product and get up and running quickly with our step-by-step guides.

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><i class="fa-paper-plane">:paper-plane:</i> <strong>Email API/SMTP</strong></td><td>Send Production Emails</td><td><em>Deliver transactional emails reliably with our API or SMTP service. Get detailed analytics and ensure high deliverability.</em></td><td><a href="getting-started/email-api-smtp.md">email-api-smtp.md</a></td><td></td></tr><tr><td><i class="fa-bug">:bug:</i> <strong>Email Sandbox</strong></td><td>Test Before Sending</td><td><em>Catch and inspect emails in a safe testing environment. Preview, analyze, and debug emails before they reach real inboxes.</em></td><td><a href="getting-started/email-sandbox.md">email-sandbox.md</a></td><td></td></tr><tr><td><i class="fa-cart-arrow-up">:cart-arrow-up:</i> <strong>Email Marketing</strong></td><td>Run Email Campaigns</td><td><em>Design, send, and track marketing campaigns. Manage subscribers and analyze campaign performance.</em></td><td><a href="getting-started/email-marketing.md">email-marketing.md</a></td><td></td></tr></tbody></table>

## Explore features

Discover the full range of features and capabilities across our email platform.

{% columns %}
{% column width="33%" %}
<i class="fa-paper-plane">:paper-plane:</i> **Email API/SMTP**

* [API Integration](email-api-smtp/api-integration.md)
* [SMTP Integration](email-api-smtp/smtp-integration.md)
* [Email Templates](email-api-smtp/email-templates/)
* [Email Logs](email-api-smtp/analytics/logs.md)
* [Webhooks](email-api-smtp/webhooks.md)
{% endcolumn %}

{% column width="33%" %}
<i class="fa--bug">:-bug:</i> **Email Sandbox**

* [Email Template Inspector](email-sandbox/testing/email-template.md)
* [HTML Check](email-sandbox/testing/email-html.md)
* [Deliverability Tests](email-sandbox/testing/spam-blacklist-reports.md)
* [Sandbox API](email-sandbox/sandbox-api-integration.md)
* [Team Collaboration](email-sandbox/sharing-sandboxes.md)
{% endcolumn %}

{% column width="33%" %}
<i class="fa-cart-arrow-up">:cart-arrow-up:</i> **Email Marketing**

* [Campaign Management](email-marketing/campaigns/)
* [Contacts Management](email-marketing/contacts/)
* [Email Templates](email-marketing/email-templates.md)
* [Statistics](email-marketing/statistics.md)
* [Segments](email-marketing/contacts/segments.md)
{% endcolumn %}
{% endcolumns %}

## Guides & integrations

Learn how to integrate Mailtrap with your favorite tools and migrate from other services.

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><i class="fa-link">:link:</i> <strong>Integrations</strong></td><td>Third-party Tools</td><td><em>Connect Mailtrap with Laravel, Rails, Node.js, Python and more popular frameworks.</em></td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/integrations">Integrations</a></td></tr><tr><td><i class="fa-globe">:globe:</i> <strong>DNS Setup</strong></td><td>Domain Configuration</td><td><em>Configure SPF, DKIM, and DMARC records with guides for all major DNS providers.</em></td><td><a href="email-api-smtp/setup/sending-domain.md">sending-domain.md</a></td></tr></tbody></table>

## Ready to get started?

{% hint style="info" %}
**New to Mailtrap?** Start with our [Email Sandbox](getting-started/email-sandbox.md) to test your emails in a safe environment, then move to [Email API/SMTP](getting-started/email-api-smtp.md) for production sending.
{% endhint %}

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><i class="fa-rocket-launch">:rocket-launch:</i> <strong>Start with a Free plan</strong></td><td><em>Get started with Mailtrap's free plan. No credit card required. Test emails, send up to 4000 emails/m, and explore all features.</em></td><td><a href="https://mailtrap.io/register/signup?utm_source=gitbook&#x26;utm_medium=knowlege_base&#x26;utm_campaign=article" class="button secondary">Sing up free</a></td><td></td></tr><tr><td><i class="fa-message">:message:</i> <strong>Talk to Sales</strong></td><td><em>Need a custom plan or have enterprise requirements? Our team is ready to help you find the perfect solution.</em></td><td><a href="https://mailtrap.io/talk-to-sales/?utm_source=gitbook&#x26;utm_medium=knowlege_base&#x26;utm_campaign=article" class="button secondary">Contact Sales</a></td><td></td></tr></tbody></table>

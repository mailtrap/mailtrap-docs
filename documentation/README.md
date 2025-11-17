---
title: Mailtrap Documentation
description: >-
  Complete email infrastructure for developers. Send production emails, test in
  sandbox, and run email campaigns - all in one platform.
icon: house
---

# Documentation

Build, test, and send emails with confidence using Mailtrap's comprehensive email platform designed for developers and teams.

{% columns %}
{% column %}
#### Get Started in 5 Minutes

Setting up Mailtrap should be the easiest part of your email journey. With clear endpoints, copy-paste-ready examples, and instant authentication, you'll send your first email in minutes—not hours.

No guesswork, no complexity—just your first successful email, fast.

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

## Quick Start Guides

Choose your product and get up and running quickly with our step-by-step guides.

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><strong>📤 Email API/SMTP</strong></td><td><strong>Send Production Emails</strong></td><td>Deliver transactional emails reliably with our API or SMTP service. Get detailed analytics and ensure high deliverability.</td><td><a href="getting-started/email-api-smtp.md">email-api-smtp.md</a></td><td></td></tr><tr><td><strong>🧪 Email Sandbox</strong></td><td><strong>Test Before Sending</strong></td><td>Catch and inspect emails in a safe testing environment. Preview, analyze, and debug emails before they reach real inboxes.</td><td><a href="getting-started/email-sandbox.md">email-sandbox.md</a></td><td></td></tr><tr><td><strong>📨 Email Marketing</strong></td><td><strong>Run Email Campaigns</strong></td><td>Design, send, and track marketing campaigns. Manage subscribers and analyze campaign performance.</td><td><a href="email-marketing/campaigns.md">campaigns.md</a></td><td></td></tr></tbody></table>

## Explore Features

Discover the full range of features and capabilities across our email platform.

{% columns %}
{% column width="33%" %}
**Email API/SMTP**

* [Send emails via API](email-api-smtp/send-emails-via-api.md)
* [SMTP integration](email-api-smtp/smtp-integration.md)
* [Email templates](email-api-smtp/templates.md)
* [Email logs & analytics](email-api-smtp/email-logs.md)
* [Webhooks](email-api-smtp/webhooks.md)
{% endcolumn %}

{% column width="33%" %}
**Email Sandbox**

* [Email testing](email-sandbox/email-testing.md)
* [HTML preview](email-sandbox/html-preview.md)
* [Spam analysis](email-sandbox/spam-analysis.md)
* [API testing](email-sandbox/api-testing.md)
* [Team collaboration](email-sandbox/sharing-sandboxes.md)
{% endcolumn %}

{% column width="33%" %}
**Email Marketing**

* [Campaign builder](email-marketing/campaigns.md)
* [Contact management](email-marketing/contacts.md)
* [Email designer](email-marketing/email-designer.md)
* [Campaign analytics](email-marketing/campaign-analytics.md)
* [List segmentation](email-marketing/segmentation.md)
{% endcolumn %}
{% endcolumns %}

## Guides & Integrations

Learn how to integrate Mailtrap with your favorite tools and migrate from other services.

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>🔄 Switching Guides</strong></td><td><strong>Migrate to Mailtrap</strong></td><td>Step-by-step guides for migrating from SendGrid, Mailgun, AWS SES, and other email services.</td><td><a href="../guides-and-tips/switching-guides/">switching-guides</a></td></tr><tr><td><strong>🔗 Integrations</strong></td><td><strong>Third-party Tools</strong></td><td>Connect Mailtrap with Laravel, Rails, Django, WordPress, and more popular frameworks.</td><td><a href="../guides-and-tips/integrations/">integrations</a></td></tr><tr><td><strong>🌐 DNS Setup</strong></td><td><strong>Domain Configuration</strong></td><td>Configure SPF, DKIM, and DMARC records with guides for all major DNS providers.</td><td><a href="../guides-and-tips/dns-setup-guides/">dns-setup-guides</a></td></tr><tr><td><strong>🤖 AI Integration</strong></td><td><strong>AI-Powered Features</strong></td><td>Leverage AI for email content generation, subject line optimization, and smart analytics.</td><td><a href="../guides-and-tips/ai-integration-guide.md">ai-integration-guide.md</a></td></tr></tbody></table>

## Popular Resources

{% columns %}
{% column %}
**Documentation**

* [API Reference](https://api-docs.mailtrap.io/)
* [Email API/SMTP Features](email-api-smtp/)
* [Email Sandbox Features](email-sandbox/)
* [Email Marketing Features](email-marketing/)
* [Account Management](account-and-permissions/)
* [Billing & Pricing](billing/)
{% endcolumn %}

{% column %}
**Support & Community**

* [FAQs](faqs/)
* [Troubleshooting](troubleshooting/)
* [Status Page](https://status.mailtrap.io/)
* [Blog & Updates](https://mailtrap.io/blog/)
* [Contact Support](https://mailtrap.io/support/)
{% endcolumn %}
{% endcolumns %}

## Ready to Get Started?

{% hint style="info" %}
**New to Mailtrap?** Start with our [Email Sandbox](getting-started/email-sandbox.md) to test your emails in a safe environment, then move to [Email API/SMTP](getting-started/email-api-smtp.md) for production sending.
{% endhint %}

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><strong>🚀 Start with a Free plan</strong></td><td>Get started with Mailtrap's free plan. No credit card required. Test emails, send to 100 contacts, and explore all features.</td><td><a href="https://mailtrap.io/signup">Sign up free</a></td><td></td></tr><tr><td><strong>💬 Talk to Sales</strong></td><td>Need a custom plan or have enterprise requirements? Our team is ready to help you find the perfect solution.</td><td><a href="https://mailtrap.io/contact-sales">Contact sales</a></td><td></td></tr></tbody></table>

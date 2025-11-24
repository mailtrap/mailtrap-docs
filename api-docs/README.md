---
title: Mailtrap API Reference
description: Complete API documentation for Mailtrap email infrastructure
icon: code
---

# Mailtrap API Reference

Welcome to the Mailtrap API documentation. Our APIs provide comprehensive access to email sending, testing, contact management, and account administration features.

## Available APIs

{% columns %}
{% column %}
### [Email API/SMTP](email-api/overview.md)
Send transactional and bulk emails with reliable delivery.
- Transactional emails
- Bulk campaigns
- Email templates
- Domain management
{% endcolumn %}

{% column %}
### [Email Sandbox](sandbox/overview.md)
Test emails safely in isolated environments.
- Test inboxes
- Email inspection
- SMTP testing
- API automation
{% endcolumn %}

{% column %}
### [Email Marketing](contacts/overview.md)
Manage contacts and marketing campaigns.
- Contact management
- List segmentation
- Import/export
- Event tracking
{% endcolumn %}
{% endcolumns %}

{% columns %}
{% column %}
### [Webhooks](webhooks/overview.md)
Receive real-time event notifications.
- Delivery events
- Engagement tracking
- Bounce handling
- Custom processing
{% endcolumn %}

{% column %}
### [Email Templates](templates/overview.md)
Create reusable email designs.
- Dynamic content
- Variable substitution
- Version control
- A/B testing
{% endcolumn %}

{% column %}
### [Account Management](general/overview.md)
Control users and settings.
- User permissions
- Billing management
- Security settings
- Audit logs
{% endcolumn %}
{% endcolumns %}

## Quick Start

{% stepper %}
{% step %}
### Get API Credentials

1. Sign up for a [Mailtrap account](https://mailtrap.io/signup)
2. Navigate to [API Tokens](https://mailtrap.io/api-tokens)
3. Generate a new API token with required permissions
{% endstep %}

{% step %}
### Install SDK

Choose your preferred programming language:

{% tabs %}
{% tab title="Node.js" %}
```bash
npm install mailtrap
```
{% endtab %}

{% tab title="Python" %}
```bash
pip install mailtrap
```
{% endtab %}

{% tab title="PHP" %}
```bash
composer require railsware/mailtrap-php
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
gem install mailtrap
```
{% endtab %}

{% tab title="Java" %}
```xml
<dependency>
    <groupId>io.mailtrap</groupId>
    <artifactId>mailtrap-java</artifactId>
    <version>2.0.0</version>
</dependency>
```
{% endtab %}

{% tab title=".NET" %}
```bash
dotnet add package Mailtrap
```
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Send First Email

```javascript
import { MailtrapClient } from "mailtrap";

const client = new MailtrapClient({
  token: process.env.MAILTRAP_API_KEY
});

await client.send({
  from: { email: "sender@example.com" },
  to: [{ email: "recipient@example.com" }],
  subject: "Hello World",
  text: "Welcome to Mailtrap!"
});
```
{% endstep %}
{% endstepper %}

## Next Steps

Choose an API to explore:

{% hint style="success" %}
**Getting Started?** Begin with the [Email API](email-api/overview.md) for sending your first email.
{% endhint %}

{% hint style="info" %}
**Testing?** Use the [Email Sandbox](sandbox/overview.md) to safely test email functionality.
{% endhint %}

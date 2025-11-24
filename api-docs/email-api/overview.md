---
title: Email API/SMTP Overview
description: Send transactional and bulk emails through Mailtrap's reliable infrastructure
icon: envelope
---

# Email API/SMTP Overview

Mailtrap's Email API provides a powerful and reliable way to send transactional and bulk emails through our infrastructure. Whether you're sending order confirmations, password resets, or marketing campaigns, our API has you covered.

## Getting Started

{% stepper %}
{% step %}
### Get Your API Key

Navigate to [API Tokens](https://mailtrap.io/api-tokens) in your Mailtrap account and generate a new API token with sending permissions.

{% hint style="info" %}
Keep your API token secure and never expose it in client-side code.
{% endhint %}
{% endstep %}

{% step %}
### Verify Your Sending Domain

Before sending emails, you need to verify ownership of your sending domain:

1. Go to [Sending Domains](https://mailtrap.io/sending/domains)
2. Add your domain
3. Configure DNS records (SPF, DKIM, DMARC)
4. Verify the records

{% hint style="warning" %}
Emails sent from unverified domains will be rejected.
{% endhint %}
{% endstep %}

{% step %}
### Install an SDK

Choose an SDK for your programming language:

{% tabs %}
{% tab title="Node.js" %}
```bash
npm install mailtrap
# or
yarn add mailtrap
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
### Send Your First Email

Here's a minimal example to send your first email:

{% tabs %}
{% tab title="Node.js" %}
```typescript
import { MailtrapClient } from "mailtrap";

const client = new MailtrapClient({
  token: process.env.MAILTRAP_API_KEY
});

await client.send({
  from: { email: "sender@yourdomain.com" },
  to: [{ email: "recipient@example.com" }],
  subject: "Hello from Mailtrap",
  text: "Welcome to Mailtrap Email API!"
});
```
{% endtab %}

{% tab title="Python" %}
```python
import mailtrap as mt

client = mt.MailtrapClient(token="YOUR_API_KEY")

mail = mt.Mail(
    sender=mt.Address(email="sender@yourdomain.com"),
    to=[mt.Address(email="recipient@example.com")],
    subject="Hello from Mailtrap",
    text="Welcome to Mailtrap Email API!"
)

client.send(mail)
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mailtrap\MailtrapClient;
use Mailtrap\Mime\MailtrapEmail;
use Symfony\Component\Mime\Address;

$mailtrap = MailtrapClient::initSendingEmails(
    apiKey: $_ENV['MAILTRAP_API_KEY']
);

$email = (new MailtrapEmail())
    ->from(new Address('sender@yourdomain.com'))
    ->to(new Address('recipient@example.com'))
    ->subject('Hello from Mailtrap')
    ->text('Welcome to Mailtrap Email API!');

$mailtrap->send($email);
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require 'mailtrap'

client = Mailtrap::Client.new(api_key: 'YOUR_API_KEY')

mail = Mailtrap::Mail.from_content(
  from: { email: 'sender@yourdomain.com' },
  to: [{ email: 'recipient@example.com' }],
  subject: 'Hello from Mailtrap',
  text: 'Welcome to Mailtrap Email API!'
)

client.send(mail)
```
{% endtab %}
{% endtabs %}
{% endstep %}
{% endstepper %}

## Email Sending Options

### Transactional Emails

Best for real-time, one-to-one emails triggered by user actions:

* Order confirmations
* Password resets
* Account notifications
* System alerts
* Welcome emails

**Endpoint:** `https://send.api.mailtrap.io/api/send`
**Rate Limit:** 100 requests per second

### Batch Sending

Send up to 500 emails in a single API call:

* Personalized notifications
* Event invitations
* Account updates
* Targeted campaigns

**Endpoint:** `https://send.api.mailtrap.io/api/batch`
**Limits:** 500 messages per call, 50 MB total payload

### Bulk Stream

Optimized for high-volume marketing campaigns:

* Newsletters
* Promotional campaigns
* Product announcements
* Marketing emails

**Endpoint:** `https://bulk.api.mailtrap.io/api/send`
**Rate Limit:** 10 requests per second

## Features

{% columns %}
{% column %}
### Email Templates
Create reusable templates with variables for consistent branding and easy updates.

[Manage Templates →](https://mailtrap.io/email-templates)
{% endcolumn %}

{% column %}
### Analytics & Tracking
Monitor delivery rates, opens, clicks, and bounces in real-time.

[View Analytics →](https://mailtrap.io/analytics)
{% endcolumn %}

{% column %}
### Webhooks
Receive real-time notifications for email events like delivery, bounce, and opens.

[Configure Webhooks →](../webhooks/overview.md)
{% endcolumn %}
{% endcolumns %}

## Testing with Sandbox

Before going to production, test your email integration with our Sandbox:

```typescript
// Switch to sandbox mode for testing
const client = new MailtrapClient({
  token: process.env.MAILTRAP_API_KEY,
  sandbox: true,
  testInboxId: 123456 // Your test inbox ID
});
```

{% hint style="info" %}
Sandbox emails are captured in your test inbox instead of being delivered to recipients.
{% endhint %}

## Best Practices

1. **Verify Your Domain**: Always verify your sending domain for better deliverability
2. **Use Templates**: Create reusable templates for consistent branding
3. **Handle Errors**: Implement proper error handling and retry logic
4. **Monitor Analytics**: Track delivery rates and engagement metrics
5. **Respect Rate Limits**: Stay within API rate limits to avoid throttling
6. **Test First**: Use Sandbox mode to test your integration before production

## Support & Resources

* [API Reference](https://api-docs.mailtrap.io)
* [SDK Documentation](https://github.com/mailtrap)
* [Knowledge Base](https://help.mailtrap.io)
* [Status Page](https://status.mailtrap.io)
* [Contact Support](mailto:support@mailtrap.io)

## Next Steps

{% hint style="success" %}
Ready to dive deeper? Explore the full API reference below to see all available endpoints and options.
{% endhint %}
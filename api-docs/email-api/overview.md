---
title: Email API Overview
description: Send transactional and bulk emails through Mailtrap's reliable infrastructure
icon: memo-circle-check
---

# Overview

Mailtrap's Email API provides a powerful and reliable way to send transactional and bulk emails through our infrastructure. Whether you're sending order confirmations, password resets, or marketing campaigns, our API has you covered.

## Getting Started

{% stepper %}
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
### Get Your API Key

Navigate to [API Tokens](https://mailtrap.io/api-tokens) in your Mailtrap account and generate a new API token with sending permissions.

{% hint style="info" %}
Keep your API token secure and never expose it in client-side code.
{% endhint %}
{% endstep %}

{% step %}
### Install SDK or Use API

Choose an SDK for your programming language or use the API directly with cURL:

{% tabs %}
{% tab title="cURL" %}
No installation required. Use cURL or any HTTP client to make API requests directly.
{% endtab %}

{% tab title="Node.js" %}
```bash
npm install mailtrap
# or
yarn add mailtrap
```
{% endtab %}

{% tab title="PHP" %}
```bash
composer require railsware/mailtrap-php
```
{% endtab %}

{% tab title="Python" %}
```bash
pip install mailtrap
```
{% endtab %}

{% tab title="Ruby" %}
```bash
gem install mailtrap
```
{% endtab %}

{% tab title=".NET" %}
```bash
dotnet add package Mailtrap
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
{% endtabs %}
{% endstep %}

{% step %}
### Send Your First Email

Here's a minimal example to send your first email:

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://send.api.mailtrap.io/api/send \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "from": {"email": "sender@yourdomain.com"},
    "to": [{"email": "recipient@example.com"}],
    "subject": "Hello from Mailtrap",
    "text": "Welcome to Mailtrap Email API!"
  }'
```
{% endtab %}

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

{% tab title=".NET" %}
```csharp
using Mailtrap;

var client = new MailtrapClient("YOUR_API_KEY");

var mail = new SendEmailRequest
{
    From = new EmailAddress { Email = "sender@yourdomain.com" },
    To = new[] { new EmailAddress { Email = "recipient@example.com" } },
    Subject = "Hello from Mailtrap",
    Text = "Welcome to Mailtrap Email API!"
};

await client.SendAsync(mail);
```
{% endtab %}

{% tab title="Java" %}
```java
import io.mailtrap.api.sendingemails.SendingEmails;
import io.mailtrap.config.MailtrapConfig;
import io.mailtrap.factory.MailtrapClientFactory;
import io.mailtrap.model.request.emails.Address;
import io.mailtrap.model.request.emails.MailtrapMail;

var config = new MailtrapConfig.Builder()
    .token("YOUR_API_KEY")
    .build();

var client = MailtrapClientFactory.createMailtrapClient(config);

var mail = new MailtrapMail.Builder()
    .from(new Address("sender@yourdomain.com"))
    .to(List.of(new Address("recipient@example.com")))
    .subject("Hello from Mailtrap")
    .text("Welcome to Mailtrap Email API!")
    .build();

client.sendingApi().emails().send(mail);
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

### Bulk Stream

Optimized for high-volume marketing campaigns:

* Newsletters
* Promotional campaigns
* Product announcements
* Marketing emails

**Endpoint:** `https://bulk.api.mailtrap.io/api/send`

{% hint style="info" %}
Learn more about [Bulk Stream](https://docs.mailtrap.io/docs/mailtrap-docs/m/email-api-smtp/setup/get-started-bulk-stream) and when to use it for your marketing emails.
{% endhint %}

### Batch Sending

Send up to 500 emails in a single API call:

* Personalized notifications
* Event invitations
* Account updates
* Targeted campaigns

**Endpoint:** `https://send.api.mailtrap.io/api/batch` or `https://bulk.api.mailtrap.io/api/batch`

{% hint style="info" %}
Use `send.api.mailtrap.io` for transactional batch emails or `bulk.api.mailtrap.io` for marketing batch emails, depending on your [stream](https://docs.mailtrap.io/docs/mailtrap-docs/m/email-api-smtp/setup/get-started-bulk-stream).
{% endhint %}

**Limits:** 500 messages per call, 50 MB total payload

## Features

{% columns %}
{% column %}
### Email Templates
Create reusable templates with variables for consistent branding and easy updates.

[Manage Templates](https://mailtrap.io/email-templates)
{% endcolumn %}

{% column %}
### Analytics & Tracking
Monitor delivery rates, opens, clicks, and bounces in real-time.

[View Analytics](https://mailtrap.io/analytics)
{% endcolumn %}

{% column %}
### Webhooks
Receive real-time notifications for email events like delivery, bounce, and opens.

[Configure Webhooks](../webhooks/overview.md)
{% endcolumn %}
{% endcolumns %}

## Testing with Sandbox

Before going to production, test your email integration with our Sandbox. All official SDKs support Sandbox mode with an easy switch.

{% hint style="success" %}
We recommend using environment variables to manage the switch between Sandbox and Production modes.
{% endhint %}

{% tabs %}
{% tab title="Node.js" %}
```typescript
import { MailtrapClient } from "mailtrap";

// Switch to sandbox mode for testing
const client = new MailtrapClient({
  token: process.env.MAILTRAP_API_KEY,
  sandbox: true,
  testInboxId: 123456 // Your test inbox ID
});

await client.send({
  from: { email: "sender@yourdomain.com" },
  to: [{ email: "recipient@example.com" }],
  subject: "Test Email",
  text: "This email will be captured in your Sandbox inbox."
});
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mailtrap\MailtrapClient;
use Mailtrap\Mime\MailtrapEmail;
use Symfony\Component\Mime\Address;

// Switch to sandbox mode for testing
$mailtrap = MailtrapClient::initSendingEmails(
    apiKey: $_ENV['MAILTRAP_API_KEY'],
    isSandbox: true,
    inboxId: 123456 // Your test inbox ID
);

$email = (new MailtrapEmail())
    ->from(new Address('sender@yourdomain.com'))
    ->to(new Address('recipient@example.com'))
    ->subject('Test Email')
    ->text('This email will be captured in your Sandbox inbox.');

$mailtrap->send($email);
```
{% endtab %}

{% tab title="Python" %}
```python
import mailtrap as mt

# Switch to sandbox mode for testing
client = mt.MailtrapClient(
    token="YOUR_API_KEY",
    sandbox=True,
    test_inbox_id=123456  # Your test inbox ID
)

mail = mt.Mail(
    sender=mt.Address(email="sender@yourdomain.com"),
    to=[mt.Address(email="recipient@example.com")],
    subject="Test Email",
    text="This email will be captured in your Sandbox inbox."
)

client.send(mail)
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require 'mailtrap'

# Switch to sandbox mode for testing
client = Mailtrap::Client.new(
  api_key: 'YOUR_API_KEY',
  sandbox: true,
  inbox_id: 123456 # Your test inbox ID
)

mail = Mailtrap::Mail.from_content(
  from: { email: 'sender@yourdomain.com' },
  to: [{ email: 'recipient@example.com' }],
  subject: 'Test Email',
  text: 'This email will be captured in your Sandbox inbox.'
)

client.send(mail)
```
{% endtab %}

{% tab title=".NET" %}
```csharp
using Mailtrap;

// Switch to sandbox mode for testing
var client = new MailtrapClient("YOUR_API_KEY", sandbox: true, testInboxId: 123456);

var mail = new SendEmailRequest
{
    From = new EmailAddress { Email = "sender@yourdomain.com" },
    To = new[] { new EmailAddress { Email = "recipient@example.com" } },
    Subject = "Test Email",
    Text = "This email will be captured in your Sandbox inbox."
};

await client.SendAsync(mail);
```
{% endtab %}

{% tab title="Java" %}
```java
import io.mailtrap.config.MailtrapConfig;
import io.mailtrap.factory.MailtrapClientFactory;
import io.mailtrap.model.request.emails.Address;
import io.mailtrap.model.request.emails.MailtrapMail;

// Switch to sandbox mode for testing
var config = new MailtrapConfig.Builder()
    .token("YOUR_API_KEY")
    .sandbox(true)
    .testInboxId(123456L) // Your test inbox ID
    .build();

var client = MailtrapClientFactory.createMailtrapClient(config);

var mail = new MailtrapMail.Builder()
    .from(new Address("sender@yourdomain.com"))
    .to(List.of(new Address("recipient@example.com")))
    .subject("Test Email")
    .text("This email will be captured in your Sandbox inbox.")
    .build();

client.sendingApi().emails().send(mail);
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Sandbox emails are captured in your test inbox instead of being delivered to recipients. Find your test inbox ID in your [Mailtrap Sandbox](https://mailtrap.io/inboxes).
{% endhint %}

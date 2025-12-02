---
title: Mailtrap API Reference
description: Complete API documentation for Mailtrap email infrastructure
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
```bash
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
The .NET SDK is available via [GitHub Packages](https://github.com/mailtrap/mailtrap-dotnet). First, add the GitHub source:

```bash
dotnet nuget add source https://nuget.pkg.github.com/mailtrap/index.json \
  --name github-mailtrap \
  --username GITHUB_USERNAME \
  --password GITHUB_PAT
```

Then install the package:

```bash
dotnet add package Mailtrap -s github-mailtrap
```
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Send First Email

{% tabs %}
{% tab title="Node.js" %}
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
{% endtab %}

{% tab title="Python" %}
```python
import mailtrap as mt

client = mt.MailtrapClient(token="YOUR_API_KEY")

mail = mt.Mail(
    sender=mt.Address(email="sender@example.com"),
    to=[mt.Address(email="recipient@example.com")],
    subject="Hello World",
    text="Welcome to Mailtrap!"
)

client.send(mail)
```
{% endtab %}

{% tab title="PHP" %}
```php
<?php
use Mailtrap\MailtrapClient;
use Mailtrap\Mime\MailtrapEmail;
use Symfony\Component\Mime\Address;

$mailtrap = MailtrapClient::initSendingEmails(
    apiKey: $_ENV['MAILTRAP_API_KEY']
);

$email = (new MailtrapEmail())
    ->from(new Address('sender@example.com'))
    ->to(new Address('recipient@example.com'))
    ->subject('Hello World')
    ->text('Welcome to Mailtrap!');

$response = $mailtrap->send($email);
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require 'mailtrap'

client = Mailtrap::Client.new(api_key: 'YOUR_API_KEY')

mail = Mailtrap::Mail.from_content(
  from: { email: 'sender@example.com' },
  to: [{ email: 'recipient@example.com' }],
  subject: 'Hello World',
  text: 'Welcome to Mailtrap!'
)

client.send(mail)
```
{% endtab %}

{% tab title="Java" %}
```java
import io.mailtrap.config.MailtrapConfig;
import io.mailtrap.factory.MailtrapClientFactory;
import io.mailtrap.model.Address;
import io.mailtrap.model.MailtrapMail;
import java.util.List;

var config = new MailtrapConfig.Builder()
    .token("YOUR_API_KEY")
    .build();

var client = MailtrapClientFactory
    .createMailtrapClient(config);

var mail = MailtrapMail.builder()
    .from(new Address("sender@example.com"))
    .to(List.of(new Address("recipient@example.com")))
    .subject("Hello World")
    .text("Welcome to Mailtrap!")
    .build();

client.sendingApi().emails().send(mail);
```
{% endtab %}

{% tab title=".NET" %}
```csharp
using Mailtrap;
using Mailtrap.Emails.Requests;

var apiToken = "YOUR_API_KEY";
using var factory = new MailtrapClientFactory(apiToken);
var client = factory.CreateClient();

var request = SendEmailRequest
    .Create()
    .From("sender@example.com")
    .To("recipient@example.com")
    .Subject("Hello World")
    .Text("Welcome to Mailtrap!");

await client.Email().Send(request);
```
{% endtab %}
{% endtabs %}
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

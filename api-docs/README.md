---
title: Mailtrap API Reference
description: Complete API documentation for Mailtrap email infrastructure
icon: code
---

# API Reference

Welcome to the Mailtrap API documentation. Our APIs provide comprehensive access to email sending, testing, contact management, and account administration features.

## Available APIs

{% columns %}
{% column %}
#### [Email API/SMTP](email-api/overview.md)

Send transactional and bulk emails with reliable delivery.

* Transactional emails
* Bulk campaigns
* Email templates
* Domain management
{% endcolumn %}

{% column %}
#### [Email Sandbox](/broken/pages/B8j01j7ouS67D5z3NoHl)

Test emails safely in isolated environments.

* Test inboxes
* Email inspection
* SMTP testing
* API automation
{% endcolumn %}

{% column %}
#### [Email Marketing](/broken/pages/5wpYnnvtHgJffci9NucS)

Manage contacts and marketing campaigns.

* Contact management
* List segmentation
* Import/export
* Event tracking
{% endcolumn %}
{% endcolumns %}

{% columns %}
{% column %}
#### [Webhooks](/broken/pages/ZvDDTOXdlgq15U9tIaEN)

Receive real-time event notifications.

* Delivery events
* Engagement tracking
* Bounce handling
* Custom processing
{% endcolumn %}

{% column %}
#### [Email Templates](https://github.com/railsware/mailtrap-gitbook/blob/main/api-docs/templates/overview.md)

Create reusable email designs.

* Dynamic content
* Variable substitution
* Version control
* A/B testing
{% endcolumn %}

{% column %}
#### [Account Management](general/overview.md)

Control users and settings.

* User permissions
* Billing management
* Security settings
* Audit logs
{% endcolumn %}
{% endcolumns %}

## Quick Start

{% stepper %}
{% step %}
#### Get API Credentials

1. Sign up for a [Mailtrap account](https://mailtrap.io/signup)
2. Navigate to [API Tokens](https://mailtrap.io/api-tokens)
3. Generate a new API token with required permissions
{% endstep %}

{% step %}
#### Install SDK

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
#### Send First Email

{% tabs %}
{% tab title="Node.js" %}
```javascript
import { MailtrapClient } from "mailtrap";

const mailtrap = new MailtrapClient({
  token: process.env.MAILTRAP_API_KEY, // You can create your API key here https://mailtrap.io/api-tokens
});

mailtrap
  .send({
    from: { name: "Mailtrap Test", email: "sender@example.com" },
    to: [{ email: "recipient@example.com" }],
    subject: "Hello from Mailtrap Node.js",
    text: "Plain text body",
  })
  .then(console.log)
  .catch(console.error);
```
{% endtab %}

{% tab title="Python" %}
```python
import mailtrap as mt

API_TOKEN = "<YOUR_API_TOKEN>"  # your API key here https://mailtrap.io/api-tokens

client = mt.MailtrapClient(token=API_TOKEN)

# Create mail object
mail = mt.Mail(
    sender=mt.Address(email="sender@example.com", name="John Smith"),
    to=[mt.Address(email="recipient@example.com")],
    subject="You are awesome!",
    text="Congrats for sending test email with Mailtrap!",
)

client.send(mail)
```
{% endtab %}

{% tab title="PHP" %}
```php
<?php

use Mailtrap\Helper\ResponseHelper;
use Mailtrap\MailtrapClient;
use Mailtrap\Mime\MailtrapEmail;
use Symfony\Component\Mime\Address;

require __DIR__ . '/vendor/autoload.php';

$mailtrap = MailtrapClient::initSendingEmails(
    apiKey: getenv('MAILTRAP_API_KEY') // your API key here https://mailtrap.io/api-tokens
);

$email = (new MailtrapEmail())
    ->from(new Address('sender@example.com'))
    ->to(new Address('recipient@example.com'))
    ->subject('Hello from Mailtrap PHP')
    ->text('Plain text body');

$response = $mailtrap->send($email);

// Access response body as array (helper optional)
var_dump(ResponseHelper::toArray($response));
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require 'mailtrap'

# Create mail object
mail = Mailtrap::Mail.from_content(
  from: { email: 'mailtrap@example.com', name: 'Mailtrap Test' },
  to: [
    { email: 'your@email.com' }
  ],
  reply_to: { email: 'support@example.com', name: 'Mailtrap Reply-To' },
  subject: 'You are awesome!',
  text: 'Congrats for sending test email with Mailtrap!'
)

# Create client and send
client = Mailtrap::Client.new(api_key: 'your-api-key')
client.send(mail)

# You can also pass the request parameters directly
client.send(
  from: { email: 'mailtrap@example.com', name: 'Mailtrap Test' },
  to: [
    { email: 'your@email.com' }
  ],
  subject: 'You are awesome!',
  text: 'Congrats for sending test email with Mailtrap!'
)

```
{% endtab %}

{% tab title="Java" %}
```java
import io.mailtrap.client.MailtrapClient;
import io.mailtrap.config.MailtrapConfig;
import io.mailtrap.factory.MailtrapClientFactory;
import io.mailtrap.model.request.emails.Address;
import io.mailtrap.model.request.emails.MailtrapMail;

import java.util.List;

public class MailtrapJavaSDKTest {

    private static final String TOKEN = "<YOUR MAILTRAP TOKEN>";
    private static final String SENDER_EMAIL = "sender@domain.com";
    private static final String RECIPIENT_EMAIL = "recipient@domain.com";

    public static void main(String[] args) {
        final MailtrapConfig config = new MailtrapConfig.Builder()
            .token(TOKEN)
            .build();

        final MailtrapClient client = MailtrapClientFactory.createMailtrapClient(config);

        final MailtrapMail mail = MailtrapMail.builder()
            .from(new Address(SENDER_EMAIL))
            .to(List.of(new Address(RECIPIENT_EMAIL)))
            .subject("Hello from Mailtrap Sending!")
            .text("Welcome to Mailtrap Sending!")
            .build();

        // Send an email using Mailtrap Sending API
        try {
            System.out.println(client.send(mail));
        } catch (Exception e) {
            System.out.println("Caught exception : " + e);
        }
    }
}
```
{% endtab %}

{% tab title=".NET" %}
```csharp
using Mailtrap;
using Mailtrap.Emails.Models;
using Mailtrap.Emails.Requests;

using var mailtrapClientFactory = new MailtrapClientFactory("YOUR_API_TOKEN");
var client = mailtrapClientFactory.CreateClient();

var mail = new SendEmailRequest
{
      From = new EmailAddress("sender@yourdomain.com"),
      To = new[] { new EmailAddress("recipient@example.com") },
      Subject = "Hello from Mailtrap",
      TextBody = "Welcome to Mailtrap Email API!"
};

await client.Email().Send(mail);
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
**Testing?** Use the [Email Sandbox](/broken/pages/B8j01j7ouS67D5z3NoHl) to safely test email functionality.
{% endhint %}

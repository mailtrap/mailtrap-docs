---
title: Mailtrap API Reference
description: Complete API documentation for the Mailtrap email platform
icon: code
---

# Overview

Welcome to the Mailtrap API documentation. Our APIs provide comprehensive access to email sending, testing, contact management, and account administration features.

The Mailtrap API follows REST principles. Authenticated users can interact with any endpoint using standard HTTP methods. All requests must be sent over HTTPS, as TLS encryption is enforced.

## Documentation structure

The API documentation is organized into the following sections:

{% columns %}
{% column width="33.33333333333333%" %}
#### Email Sending

Endpoints to send transactional and [bulk](https://docs.mailtrap.io/email-api-smtp/setup/bulk-stream) (promotional) emails, as well as manage sending domains, suppressions, and delivery statistics.
{% endcolumn %}

{% column width="33.33333333333333%" %}
#### [Email Sandbox](https://docs.mailtrap.io/developers/email-sandbox/email-sandbox-api)

Endpoints for testing and inspecting emails in a safe environment.\
**Note**: Email Sending and Email Sandbox use different base URLs.
{% endcolumn %}

{% column %}
#### [Promotional](https://docs.mailtrap.io/developers/email-marketing/contacts-api)

Endpoints to manage [contacts](https://docs.mailtrap.io/email-marketing/contacts). Contacts can be used to run campaigns and set up automations.
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
#### [Templates](https://docs.mailtrap.io/developers/management/templates)

Endpoints to manage [email templates](https://docs.mailtrap.io/email-api-smtp/email-templates) used for email sending, email sandbox, and campaigns.
{% endcolumn %}

{% column %}
#### [Account Management](https://docs.mailtrap.io/developers/account-management/general-api)

Endpoints for programmatic management of account details and access permissions.
{% endcolumn %}
{% endcolumns %}

## Quick Start

{% stepper %}
{% step %}
#### Get API Credentials

1. Navigate to [API Tokens](https://mailtrap.io/api-tokens).
2. Generate a new API token with the required permissions.

{% hint style="info" %}
You must have a [verified domain](https://docs.mailtrap.io/email-api-smtp/setup/sending-domain) to send emails.

Keep your API token secure and never expose it in client-side code.
{% endhint %}
{% endstep %}

{% step %}
#### Install an SDK

Choose an SDK for your programming language, or use the API directly with cURL.

Supported SDKs:

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
#### Send your first email

Below are minimal examples for sending an email:

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

### Email Sending Options

#### [Transactional emails](https://docs.mailtrap.io/developers/sending/send-email-transactional)

Best suited for real-time, one-to-one emails triggered by user actions, such as:

* Order confirmations
* Password resets
* Account notifications
* System alerts
* Welcome emails

**Endpoint**:

`https://send.api.mailtrap.io/api/send`

#### [Bulk stream](https://docs.mailtrap.io/developers/sending/send-email-bulk)

Optimized for high-volume marketing and promotional campaigns, including:

* Newsletters
* Promotional campaigns
* Product announcements
* Marketing emails

**Endpoint**:

`https://bulk.api.mailtrap.io/api/send`

#### [Batch sending](https://docs.mailtrap.io/developers/sending/send-email-batch)

Send up to **500** **emails** in a single API call. Useful for:

* Personalized notifications
* Event invitations
* Account updates
* Targeted campaigns

**Endpoints**:

* Transactional:\
  `https://send.api.mailtrap.io/api/batch`
* Bulk:\
  `https://bulk.api.mailtrap.io/api/batch`

### Testing with Email Sandbox

Before going to production, test your email integration using **Email Sandbox**. All official SDKs support Sandbox mode and allow you to easily switch between testing and production environments.

We recommend using environment variables to manage the switch between Sandbox and Production modes.

{% tabs %}
{% tab title="Node.js" %}
```javascript
import { MailtrapClient } from "mailtrap";

const apiKey = process.env.MAILTRAP_API_KEY;
const isSandbox = process.env.MAILTRAP_USE_SANDBOX === "true";
const inboxId = isSandbox ? Number(process.env.MAILTRAP_INBOX_ID) : undefined; // required only for sandbox

const client = new MailtrapClient({
  token: apiKey,
  sandbox: isSandbox,
  testInboxId: inboxId, // undefined is ignored for production
});

client
  .send({
    from: {
      name: "Mailtrap Test",
      email: isSandbox ? "sandbox@example.com" : "no-reply@your-domain.com",
    },
    to: [{ email: "recipient@example.com" }],
    subject: isSandbox ? "[SANDBOX] Demo email" : "Welcome onboard",
    text: "This is a minimal body for demonstration purposes.",
  })
  .then(console.log)
  .catch(console.error);
```
{% endtab %}

{% tab title="Python" %}
```python
import os
import mailtrap as mt

API_KEY = os.environ["MAILTRAP_API_KEY"]
IS_SANDBOX = os.environ.get("MAILTRAP_USE_SANDBOX", "true").lower() == "true"
INBOX_ID = os.environ.get("MAILTRAP_INBOX_ID")

client = mt.MailtrapClient(
  token=API_KEY,
  sandbox=IS_SANDBOX,
  inbox_id=INBOX_ID,  # None is ignored for production
)

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

$apiKey    = getenv('MAILTRAP_API_KEY');
$isSandbox = filter_var(getenv('MAILTRAP_USE_SANDBOX'), FILTER_VALIDATE_BOOL);
$inboxId   = $isSandbox ? getenv('MAILTRAP_INBOX_ID') : null; // required only for sandbox

$client = MailtrapClient::initSendingEmails(
    apiKey: $apiKey,
    isSandbox: $isSandbox,
    inboxId: $inboxId // null is ignored for production
);

$email = (new MailtrapEmail())
    ->from(new Address($isSandbox ? 'sandbox@example.com' : 'no-reply@your-domain.com'))
    ->to(new Address('recipient@example.com'))
    ->subject($isSandbox ? '[SANDBOX] Demo email' : 'Welcome onboard')
    ->text('This is a minimal body for demonstration purposes.');

$response = $client->send($email);

// Access response body as array (helper optional)
var_dump(ResponseHelper::toArray($response));
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require 'mailtrap'

client = Mailtrap::Client.new(api_key: 'your-api-key', sandbox: true, inbox_id: YOUR_INBOX_ID)
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

public class MailtrapJavaSDKSandboxTest {

    private static final String TOKEN = "<YOUR MAILTRAP TOKEN>";
    private static final String SENDER_EMAIL = "sender@domain.com";
    private static final String RECIPIENT_EMAIL = "recipient@domain.com";
    private static final long INBOX_ID = 1L;

    public static void main(String[] args) {
        final MailtrapConfig config = new MailtrapConfig.Builder()
            .token(TOKEN)
            .sandbox(true)
            .inboxId(INBOX_ID)
            .build();

        final MailtrapClient client = MailtrapClientFactory.createMailtrapClient(config);

        final MailtrapMail mail = MailtrapMail.builder()
            .from(new Address(SENDER_EMAIL))
            .to(List.of(new Address(RECIPIENT_EMAIL)))
            .subject("Hello from Mailtrap Sandbox Sending!")
            .text("Welcome to Mailtrap Sandbox Sending!")
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
var apiToken = "<API-TOKEN>";
var inboxId = <INBOX-ID>; // Only needed for sandbox
using var mailtrapClientFactory = new MailtrapClientFactory(apiToken);
IMailtrapClient mailtrapClient = mailtrapClientFactory.CreateClient();

SendEmailRequest request = SendEmailRequest
    .Create()
    .From("hello@demomailtrap.co", "Mailtrap Test")
    .To("world@demomailtrap.co")
    .Subject("You are awesome!")
    .Text("Congrats for sending test email with Mailtrap!");

SendEmailResponse? response = await mailtrapClient
    .Test(inboxId)
    .Send(request);+
```
{% endtab %}
{% endtabs %}

#### How Sandbox works

Sandbox emails are captured in your test inbox instead of being delivered to real recipients.

To find your **Sandbox ID**:

1. Open your Sandbox inbox in Mailtrap.
2. Copy the ID from the inbox URL.

**Example**: `https://mailtrap.io/inboxes/2564102/messages`\
Sandbox ID: **2564102**

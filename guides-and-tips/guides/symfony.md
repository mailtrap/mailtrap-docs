---
title: Symfony
description: >-
  Integrate Mailtrap with Symfony to send emails through Symfony's Mailtrap
  bridge, the Mailtrap PHP SDK or SMTP, receive webhook events, and test with
  Email Sandbox.
cover: ../.gitbook/assets/symfony-cover.png
coverY: 0
---

# Symfony

Integrate Mailtrap with Symfony apps and projects to send and test emails using Symfony's Mailtrap bridge, the Mailtrap SDK, or SMTP.

<a href="https://github.com/mailtrap/mailtrap-php/tree/main/src/Bridge/Symfony" class="button primary">Mailtrap Symfony bridge on GitHub</a>

### Overview

Mailtrap can be integrated with Symfony apps and projects for email sending and testing. You can connect it in three ways:

* **Symfony Mailtrap Mailer (recommended)**: Symfony's own `symfony/mailtrap-mailer` bridge, available in Symfony 7.2 and later. It needs no service registration, maps Symfony's standard tag and metadata headers to Mailtrap categories and custom variables, and includes a webhook parser.
* **SDK integration**: the Symfony bridge in the [Mailtrap PHP SDK](https://github.com/mailtrap/mailtrap-php) adds a `mailtrap+sdk` transport to Symfony Mailer. Use it on Symfony 6.0 to 7.1, or when your app also needs the Mailtrap API client for templates, batch sending, or contacts.
* **SMTP integration**: Symfony Mailer's built-in SMTP transport with your Mailtrap SMTP credentials. It needs no extra package and works on any Symfony version, including those before 6.0.

#### Which integration to use

|                               | Symfony Mailtrap Mailer                             | SDK integration          | SMTP integration        |
| ----------------------------- | --------------------------------------------------- | ------------------------ | ----------------------- |
| Package                       | `symfony/mailtrap-mailer`                           | `railsware/mailtrap-php` | None                    |
| DSN scheme                    | `mailtrap+api`, `mailtrap+smtp`, `mailtrap+sandbox` | `mailtrap+sdk`           | `smtp`                  |
| Symfony                       | 7.2 or later                                        | 6.0 or later             | Any with Symfony Mailer |
| PHP                           | 8.2 or later (8.4 or later on Symfony 8)            | 8.0 or later             | As Symfony requires     |
| Service registration          | Not needed                                          | Needed                   | Not needed              |
| Transactional Stream          | Yes                                                 | Yes                      | Yes                     |
| Bulk Stream                   | Yes, with `mailtrap+api`                            | Yes                      | Yes                     |
| Email Sandbox                 | Yes, Symfony 7.4 or later                           | Yes                      | Yes                     |
| Category and custom variables | `TagHeader`, `MetadataHeader`                       | `MailtrapEmail` methods  | `X-MT-*` headers        |
| Email templates               | No                                                  | With the SDK client      | No                      |
| Batch sending                 | No                                                  | With the SDK client      | No                      |
| Webhook parser                | Yes                                                 | No                       | No                      |

The webhook parser comes with `symfony/mailtrap-mailer`, but it handles events for your emails whichever integration sends them. On Symfony 7.4, or 8.1 and later, you can install the package for webhooks alone.

#### Prerequisites

Before we start, you'll need to:

* [Verify your sending domain](https://docs.mailtrap.io/general/sending-domain)
* [Create and save an API token](https://docs.mailtrap.io/general/api-tokens)

### Email Live Sending for Symfony

#### Symfony Mailtrap Mailer

Symfony maintains its own Mailtrap bridge. It doesn't need a service registration and can send through the API or SMTP.

{% hint style="info" %}
Symfony Mailtrap Mailer requires Symfony 7.2 or later and PHP 8.2 or later. On Symfony 8.0, it requires PHP 8.4 or later, and on Symfony 8.1, PHP 8.4.1 or later. Sending to Email Sandbox requires Symfony 7.4 or later.
{% endhint %}

Install the bridge together with an HTTP client, which the `mailtrap+api` and `mailtrap+sandbox` transports need:

```bash
composer require symfony/mailtrap-mailer symfony/http-client
```

Then set `MAILER_DSN` in your `.env` file:

```bash
# API
MAILER_DSN=mailtrap+api://YOUR_API_TOKEN@default

# SMTP
MAILER_DSN=mailtrap+smtp://YOUR_API_TOKEN@default
```

With the `default` host, both DSNs send through the Transactional Stream. To add a category and custom variables, use Symfony's `TagHeader` and `MetadataHeader`:

```php
use Symfony\Component\Mailer\Header\MetadataHeader;
use Symfony\Component\Mailer\Header\TagHeader;

$email->getHeaders()->add(new TagHeader('Welcome email'));
$email->getHeaders()->add(new MetadataHeader('user_id', '45982'));
```

Mailtrap allows one tag per email. Read more in the [Symfony Mailer documentation](https://symfony.com/doc/current/mailer.html).

#### Minimal example

To check the setup, send a test email from the console. The sender address must use your verified sending domain:

```bash
php bin/console mailer:test recipient@example.com --from=hello@yourdomain.com
```

The `mailer:test` command is available in Symfony 6.2 and later. To send from your app, inject `MailerInterface`, for example in a controller:

```php
<?php

namespace App\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Mailer\MailerInterface;
use Symfony\Component\Mime\Email;
use Symfony\Component\Routing\Attribute\Route;

class MailerController extends AbstractController
{
    #[Route('/email')]
    public function sendEmail(MailerInterface $mailer): Response
    {
        $email = (new Email())
            ->from('hello@yourdomain.com')
            ->to('recipient@example.com')
            ->subject('Welcome to our app')
            ->text('Hi Jon, welcome aboard!')
            ->html('<p>Hi Jon, welcome aboard!</p>');

        $mailer->send($email);

        return new Response('Email sent');
    }
}
```

The email appears in your [Email Logs](https://docs.mailtrap.io/email-live-sending/analytics/logs) as soon as it's sent.

{% hint style="info" %}
If your app uses Symfony Messenger, Mailer sends emails asynchronously by default. Run a worker with `php bin/console messenger:consume` to send them. The `mailer:test` command skips Messenger.
{% endhint %}

#### Webhooks

Symfony Mailtrap Mailer includes a parser for Mailtrap [webhooks](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/general/webhooks). It verifies the signature of each request and turns Mailtrap events into Symfony's mailer events.

{% hint style="warning" %}
Only these versions always check the signature:

* Symfony 7.4: `symfony/mailtrap-mailer` 7.4.19 or later
* Symfony 8.1 and later: `symfony/mailtrap-mailer` 8.1.7 or later

Earlier versions either don't check it at all (Symfony 7.2 and 7.3, and `symfony/mailtrap-mailer` before 7.4.12 or 8.0.12) or skip the check when the secret is empty. On Symfony 7.2, 7.3, and 8.0, upgrade before you use the parser.
{% endhint %}

To set it up:

* Install the Webhook component. If you send with the SDK or SMTP, also install `symfony/mailtrap-mailer`, which provides the parser:

```bash
composer require symfony/webhook
```

Symfony Flex adds the `/webhook/{type}` route in `config/routes/webhook.yaml`. If your app doesn't use Flex, create the file yourself:

```yaml
webhook:
    resource: '@FrameworkBundle/Resources/config/routing/webhook.php'
    prefix: /webhook
```

* Route the `mailtrap` webhook to the parser in `config/packages/webhook.yaml`:

```yaml
framework:
    webhook:
        routing:
            mailtrap:
                service: 'mailer.webhook.request_parser.mailtrap'
                secret: '%env(MAILTRAP_WEBHOOK_SECRET)%'
```

* In Mailtrap, go to **Webhooks**, click **Create New Webhook**, and set:
  * **Webhook URL**: `https://yoursite.example.com/webhook/mailtrap`
  * **Payload format**: JSON. The parser doesn't accept JSON Lines.
  * **Select area**: **Live Sending**, then the stream, your domain, and the events you need
* Save the webhook, open it, and add its **Signing Secret** to your `.env.local` file, or set it as an environment variable, so it stays out of version control:

```bash
MAILTRAP_WEBHOOK_SECRET=YOUR_SIGNING_SECRET
```

* Handle the events in a consumer, for example in `src/Webhook/MailtrapWebhookConsumer.php`:

```php
<?php

namespace App\Webhook;

use Symfony\Component\RemoteEvent\Attribute\AsRemoteEventConsumer;
use Symfony\Component\RemoteEvent\Consumer\ConsumerInterface;
use Symfony\Component\RemoteEvent\Event\Mailer\MailerDeliveryEvent;
use Symfony\Component\RemoteEvent\Event\Mailer\MailerEngagementEvent;
use Symfony\Component\RemoteEvent\RemoteEvent;

#[AsRemoteEventConsumer('mailtrap')]
final class MailtrapWebhookConsumer implements ConsumerInterface
{
    public function consume(RemoteEvent $event): void
    {
        if ($event instanceof MailerDeliveryEvent) {
            // $event->getName() is "delivered", "bounce", or "dropped"
            // $event->getRecipientEmail(), $event->getReason()
        } elseif ($event instanceof MailerEngagementEvent) {
            // $event->getName() is "open", "click", "unsubscribe", or "spam"
        }

        // $event->getId() is the message ID, $event->getPayload() is the full Mailtrap event
    }
}
```

Symfony maps Mailtrap events like this:

| Mailtrap event          | Symfony event           | Name          |
| ----------------------- | ----------------------- | ------------- |
| `delivery`              | `MailerDeliveryEvent`   | `delivered`   |
| `bounce`, `soft bounce` | `MailerDeliveryEvent`   | `bounce`      |
| `suspension`, `reject`  | `MailerDeliveryEvent`   | `dropped`     |
| `open`                  | `MailerEngagementEvent` | `open`        |
| `click`                 | `MailerEngagementEvent` | `click`       |
| `unsubscribe`           | `MailerEngagementEvent` | `unsubscribe` |
| `spam`                  | `MailerEngagementEvent` | `spam`        |

The email's category is available as `$event->getTags()` and its custom variables as `$event->getMetadata()`. To tell a soft bounce from a bounce, read `$event->getPayload()['event']`.

To check the setup, open the saved webhook in Mailtrap and click **Run Test**. A test sent from the **Create New Webhook** form has no signature yet, so the parser rejects it.

Each webhook covers one stream and has its own signing secret. To receive events from both streams, create a second webhook and a routing entry for it, for example `mailtrap_bulk` with that webhook's secret, the URL `https://yoursite.example.com/webhook/mailtrap_bulk`, and a consumer with `#[AsRemoteEventConsumer('mailtrap_bulk')]`.

{% hint style="info" %}
Symfony passes each event to your consumer through Symfony Messenger. If your app routes messages to an async transport, run a worker for it, for example `php bin/console messenger:consume async`, where `async` is your transport's name.
{% endhint %}

#### Bulk Stream

To send through the [Bulk Stream](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-live-sending/setup/bulk-stream) with Symfony Mailtrap Mailer, use the `mailtrap+api` scheme with the bulk host:

```bash
MAILER_DSN=mailtrap+api://YOUR_API_TOKEN@bulk.api.mailtrap.io
```

The `mailtrap+smtp` scheme always connects to the Transactional Stream.

#### SDK integration

The [Mailtrap Symfony bridge](https://github.com/mailtrap/mailtrap-php/tree/main/src/Bridge/Symfony) is part of the official Mailtrap PHP SDK and plugs into Symfony Mailer. You can switch between the Transactional Stream, the Bulk Stream, and Email Sandbox by changing the `MAILER_DSN` variable. The SDK supports:

* Transactional, bulk, and batch email sending
* Email template management
* Contact and contact list management
* Sending domain management
* Sandbox email sending and sandbox project management

{% hint style="info" %}
The Symfony bridge works with Symfony 6.0 and later and requires PHP 8.0 or later.
{% endhint %}

#### Installation

Install the SDK together with Symfony Mailer and an HTTP client:

```bash
composer require railsware/mailtrap-php symfony/http-client nyholm/psr7 symfony/mailer
```

#### Configuration

* Register the Mailtrap transport factory in `config/services.yaml`:

```yaml
services:

    # ...

    Mailtrap\Bridge\Transport\MailtrapSdkTransportFactory:
        tags:
            - { name: 'mailer.transport_factory' }
```

* Set `MAILER_DSN` in your `.env` file with your API token:

```bash
MAILER_DSN=mailtrap+sdk://YOUR_API_TOKEN@default
```

The `default` host sends through the Transactional Stream. To send through the [Bulk Stream](https://docs.mailtrap.io/email-live-sending/setup/bulk-stream), use `MAILER_DSN=mailtrap+sdk://YOUR_API_TOKEN@bulk.api.mailtrap.io` instead.

* Make sure `config/packages/mailer.yaml` reads the variable:

```yaml
framework:
    mailer:
        dsn: '%env(MAILER_DSN)%'
```

#### Categories and custom variables

Add a [category](https://docs.mailtrap.io/email-live-sending/analytics/categories) and [custom variables](https://docs.mailtrap.io/email-live-sending/advanced/custom-variables) to filter and analyze your emails in Mailtrap. Use `MailtrapEmail` instead of `Email`:

```php
use Mailtrap\Mime\MailtrapEmail;

$email = (new MailtrapEmail())
    ->from('hello@yourdomain.com')
    ->to('recipient@example.com')
    ->subject('Welcome to our app')
    ->text('Hi Jon, welcome aboard!')
    ->category('Welcome email')
    ->customVariables([
        'user_id' => '45982',
        'batch_id' => 'PSJ-12',
    ]);

$mailer->send($email);
```

Each email can have one category. Custom variables are limited to 1,000 bytes per email.

#### Send with an email template

The `mailtrap+sdk` transport requires an HTML or text body. To send a [Mailtrap email template](https://docs.mailtrap.io/general/email-templates), use the SDK client directly.

* Add your API token to the `.env` file:

```bash
MAILTRAP_API_KEY=YOUR_API_TOKEN
```

* Create a console command, for example in `src/Command/SendTemplateMailCommand.php`:

```php
<?php

namespace App\Command;

use Mailtrap\MailtrapClient;
use Mailtrap\Mime\MailtrapEmail;
use Symfony\Component\Console\Attribute\AsCommand;
use Symfony\Component\Console\Command\Command;
use Symfony\Component\Console\Input\InputInterface;
use Symfony\Component\Console\Output\OutputInterface;
use Symfony\Component\Mime\Address;

#[AsCommand(name: 'app:send-template-mail')]
class SendTemplateMailCommand extends Command
{
    protected function execute(InputInterface $input, OutputInterface $output): int
    {
        $email = (new MailtrapEmail())
            ->from(new Address('hello@yourdomain.com', 'Your App'))
            ->to(new Address('recipient@example.com', 'Jon'))
            ->templateUuid('YOUR_TEMPLATE_UUID')
            ->templateVariables([
                'user_name' => 'Jon',
            ]);

        MailtrapClient::initSendingEmails(
            apiKey: $_ENV['MAILTRAP_API_KEY'],
        )->send($email);

        return Command::SUCCESS;
    }
}
```

* Run it:

```bash
php bin/console app:send-template-mail
```

{% hint style="info" %}
Don't set a subject, text, HTML body, or category when you send a template. The template defines them, and the API returns a validation error if you add them.
{% endhint %}

#### Batch sending

To send the same email to many recipients in one API call, use `batchSend()` in the same way:

```php
$mailtrap = MailtrapClient::initSendingEmails(
    apiKey: $_ENV['MAILTRAP_API_KEY'],
    // isBulk: true, // uncomment to send through the Bulk Stream
);

$baseEmail = (new MailtrapEmail())
    ->from(new Address('hello@yourdomain.com', 'Your App'))
    ->subject('Batch email subject')
    ->text('Batch email text')
    ->html('<p>Batch email text</p>');

$recipientEmails = [
    (new MailtrapEmail())->to(new Address('recipient1@example.com', 'Recipient 1')),
    (new MailtrapEmail())->to(new Address('recipient2@example.com', 'Recipient 2')),
];

$mailtrap->batchSend($recipientEmails, $baseEmail);
```

The base email can't include `to`, `cc`, or `bcc` addresses. The batch API accepts up to 500 emails per call.

For more examples, see the [Symfony bridge README](https://github.com/mailtrap/mailtrap-php/tree/main/src/Bridge/Symfony) on GitHub.

#### SMTP integration

You can also send with Symfony Mailer's built-in SMTP transport, which works with any Symfony version that has Symfony Mailer. To get your credentials:

1. Go to the [Sending Setup](https://mailtrap.io/api-smtp/sending-setup) page under **Live Sending** and choose your domain.
2. Select the Transactional or Bulk Stream.
3. Toggle the switch to **SMTP** and copy the credentials.

Add them to `MAILER_DSN` in your `.env` file:

```bash
MAILER_DSN=smtp://api:YOUR_API_TOKEN@live.smtp.mailtrap.io:587
```

For the Bulk Stream, use `bulk.smtp.mailtrap.io` with the Bulk Stream credentials. Mailtrap SMTP supports ports 587 (recommended), 2525, 25, and 465. If your credentials contain special characters, URL-encode them in the DSN.

To add a category and custom variables to emails sent over SMTP, set the `X-MT-Category` and `X-MT-Custom-Variables` headers:

```php
$email->getHeaders()
    ->addTextHeader('X-MT-Category', 'Welcome email')
    ->addTextHeader('X-MT-Custom-Variables', json_encode(['user_id' => '45982']));
```

{% hint style="info" %}
SMTP integration needs no package besides `symfony/mailer`. It uses Symfony Mailer's standard `smtp` transport.
{% endhint %}

Read more in the [SMTP integration guide](https://docs.mailtrap.io/email-live-sending/setup/smtp-integration).

### Email Sandbox for Symfony

[Email Sandbox](https://docs.mailtrap.io/getting-started/email-sandbox) catches every email your Symfony app sends, so you can inspect it without reaching real recipients. You don't need a verified domain to use it. You'll find the sandbox ID in your sandbox's URL.

#### Symfony Mailtrap Mailer

In Symfony 7.4 and later, Symfony's Mailtrap bridge can also send to Email Sandbox. It uses the `inboxId` option for the sandbox ID:

```bash
MAILER_DSN=mailtrap+sandbox://YOUR_API_TOKEN@default?inboxId=YOUR_SANDBOX_ID
```

#### SDK integration

If you use the Mailtrap Symfony bridge, point `MAILER_DSN` to the Sandbox API and add your sandbox ID:

```bash
MAILER_DSN=mailtrap+sdk://YOUR_API_TOKEN@sandbox.api.mailtrap.io?sandboxId=YOUR_SANDBOX_ID
```

{% hint style="info" %}
In the SDK, the older `inboxId` option still works but is deprecated. Replace `?inboxId=` with `?sandboxId=` in your DSN.
{% endhint %}

#### SMTP integration

To use the SMTP transport, go to **Sandboxes**, open your sandbox, and copy the credentials from the **Integration** tab. Then add them to `MAILER_DSN`:

```bash
MAILER_DSN=smtp://YOUR_SANDBOX_USERNAME:YOUR_SANDBOX_PASSWORD@sandbox.smtp.mailtrap.io:2525
```

Each sandbox has its own username and password. Read more in the [Sandbox SMTP integration guide](https://docs.mailtrap.io/email-sandbox/setup/sandbox-smtp-integration).

#### Switch from Sandbox to live sending

When you're ready to send to real recipients, update `MAILER_DSN`:

* **Symfony Mailtrap Mailer**: change `mailtrap+sandbox` to `mailtrap+api` and remove `inboxId`.
* **SDK**: change the host to `default` (or `bulk.api.mailtrap.io`) and remove `sandboxId`.
* **SMTP**: replace the Sandbox credentials with your Email Live Sending SMTP credentials.

Set `MAILER_DSN` per environment, so your development and staging servers send to Sandbox and production sends to real recipients.

#### Known limits

* The `mailtrap+smtp` scheme always connects to `live.smtp.mailtrap.io` and ignores the host in the DSN, so it can't send through the Bulk Stream. Use `mailtrap+api` with the bulk host, or the `smtp` scheme with `bulk.smtp.mailtrap.io`, instead.
* Symfony Mailtrap Mailer can't send Mailtrap email templates, and the `mailtrap+sdk` transport requires an HTML or text body. To send a template, use the SDK client.
* Batch sending isn't available through Symfony Mailer. Use the SDK client's `batchSend()`.
* An email can have one category. Symfony Mailtrap Mailer throws an error if you add a second `TagHeader`.
* The webhook parser accepts only the JSON payload format and the Mailtrap events listed in the Webhooks section. If a request contains an event it doesn't know, it rejects the whole request.
* Neither bridge receives inbound email.
* Sending to Email Sandbox with Symfony Mailtrap Mailer requires Symfony 7.4 or later.

#### Troubleshooting

* **"The "mailtrap+sdk" scheme is not supported" error**

Symfony can't find the Mailtrap transport factory. Add the `MailtrapSdkTransportFactory` service to `config/services.yaml`, as shown in the SDK configuration steps. The same cause can show up as an error that tells you to install `symfony/mailtrap-mailer`.

* **"The host is not supported" error**

The `mailtrap+sdk` DSN accepts only `default`, `send.api.mailtrap.io`, `bulk.api.mailtrap.io`, and `sandbox.api.mailtrap.io` as hosts. Check the host in `MAILER_DSN`.

* **"You cannot send an email to a sandbox with an empty "sandboxId" parameter" error**

Add `?sandboxId=YOUR_SANDBOX_ID` to your Sandbox DSN.

* **Emails aren't sent**

If your app uses Symfony Messenger, emails wait in a queue until a worker sends them. Run `php bin/console messenger:consume`, or send a test email with `mailer:test`, which skips Messenger.

* **"Sending from domain is not allowed" error**

The sender address doesn't use a verified sending domain. Make sure every `from` address in your emails uses your verified domain. See [Domain not allowed](https://docs.mailtrap.io/email-live-sending/troubleshooting/sending-from-domain-not-allowed) for more fixes.

If you need help with your Symfony integration, contact our support team at **support@mailtrap.io**.

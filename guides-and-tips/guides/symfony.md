# Symfony

Integrate Mailtrap with Symfony apps and projects to send and test emails using the Mailtrap SDK, Symfony's Mailtrap bridge, or SMTP.

<a href="https://github.com/mailtrap/mailtrap-php/tree/main/src/Bridge/Symfony" class="button primary">Mailtrap Symfony bridge on GitHub</a>

### Overview

Mailtrap can be integrated with Symfony apps and projects for email sending and testing. You can connect it in three ways:

* **SDK integration**: the Symfony bridge in the [Mailtrap PHP SDK](https://github.com/mailtrap/mailtrap-php) adds a `mailtrap+sdk` transport to Symfony Mailer, so you keep sending with `MailerInterface`.
* **Symfony Mailtrap Mailer**: Symfony's own `symfony/mailtrap-mailer` bridge, available in Symfony 7.2 and later.
* **SMTP integration**: Symfony Mailer's built-in SMTP transport with your Mailtrap SMTP credentials.

#### Prerequisites

Before we start, you'll need to:

* [Verify your sending domain](https://docs.mailtrap.io/general/sending-domain)
* [Create and save an API token](https://docs.mailtrap.io/general/api-tokens)

### Email Live Sending for Symfony

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

#### Symfony Mailtrap Mailer

Symfony maintains its own Mailtrap bridge for Symfony 7.2 and later. It doesn't need a service registration and can send through the API or SMTP. Install it:

```bash
composer require symfony/mailtrap-mailer
```

Then set `MAILER_DSN` in your `.env` file:

```bash
# API
MAILER_DSN=mailtrap+api://YOUR_API_TOKEN@default

# SMTP
MAILER_DSN=mailtrap+smtp://YOUR_API_TOKEN@default
```

Both DSNs send through the Transactional Stream. To add a category and custom variables, use Symfony's `TagHeader` and `MetadataHeader`:

```php
use Symfony\Component\Mailer\Header\MetadataHeader;
use Symfony\Component\Mailer\Header\TagHeader;

$email->getHeaders()->add(new TagHeader('Welcome email'));
$email->getHeaders()->add(new MetadataHeader('user_id', '45982'));
```

Mailtrap allows one tag per email. Read more in the [Symfony Mailer documentation](https://symfony.com/doc/current/mailer.html).

#### SMTP integration

You can also send with Symfony Mailer's built-in SMTP transport. To get your credentials:

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
SMTP integration doesn't need the Mailtrap SDK. It uses Symfony Mailer's standard `smtp` transport.
{% endhint %}

Read more in the [SMTP integration guide](https://docs.mailtrap.io/email-live-sending/setup/smtp-integration).

### Email Sandbox for Symfony

[Email Sandbox](https://docs.mailtrap.io/getting-started/email-sandbox) catches every email your Symfony app sends, so you can inspect it without reaching real recipients. You don't need a verified domain to use it.

#### SDK integration

If you use the Mailtrap Symfony bridge, point `MAILER_DSN` to the Sandbox API and add your sandbox ID:

```bash
MAILER_DSN=mailtrap+sdk://YOUR_API_TOKEN@sandbox.api.mailtrap.io?sandboxId=YOUR_SANDBOX_ID
```

You'll find the sandbox ID in your sandbox's URL.

{% hint style="info" %}
The older `inboxId` option still works but is deprecated. Replace `?inboxId=` with `?sandboxId=` in your DSN.
{% endhint %}

#### Symfony Mailtrap Mailer

In Symfony 7.4 and later, Symfony's Mailtrap bridge can also send to Email Sandbox. It uses the `inboxId` option for the sandbox ID:

```bash
MAILER_DSN=mailtrap+sandbox://YOUR_API_TOKEN@default?inboxId=YOUR_SANDBOX_ID
```

#### SMTP integration

To use the SMTP transport, go to **Sandboxes**, open your sandbox, and copy the credentials from the **Integration** tab. Then add them to `MAILER_DSN`:

```bash
MAILER_DSN=smtp://YOUR_SANDBOX_USERNAME:YOUR_SANDBOX_PASSWORD@sandbox.smtp.mailtrap.io:2525
```

Each sandbox has its own username and password. Read more in the [Sandbox SMTP integration guide](https://docs.mailtrap.io/email-sandbox/setup/sandbox-smtp-integration).

#### Switch from Sandbox to live sending

When you're ready to send to real recipients, update `MAILER_DSN`:

* **SDK**: change the host to `default` (or `bulk.api.mailtrap.io`) and remove `sandboxId`.
* **Symfony Mailtrap Mailer**: change `mailtrap+sandbox` to `mailtrap+api` and remove `inboxId`.
* **SMTP**: replace the Sandbox credentials with your Email Live Sending SMTP credentials.

Set `MAILER_DSN` per environment, so your development and staging servers send to Sandbox and production sends to real recipients.

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

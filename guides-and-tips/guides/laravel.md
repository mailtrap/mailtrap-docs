---
cover: ../.gitbook/assets/laravel-cover.png
coverY: 0
---

# Laravel

Integrate Mailtrap with Laravel apps and projects to send and test emails using the Mailtrap SDK, SMTP, or RESTful API.

<a class="button primary">Mailtrap Laravel bridge on GitHub</a><br>

### Overview

Mailtrap can be integrated with Laravel apps and projects for email sending and testing. You can connect it in three ways:

* **SDK integration**: the Laravel bridge in the[ Mailtrap PHP SDK](https://github.com/mailtrap/mailtrap-php) adds a mailtrap-sdk mail transport, so you keep sending with Mailables and Notifications.
* **SMTP integration**: Laravel's built-in smtp mailer with your Mailtrap SMTP credentials.
* **RESTful API integration**: direct HTTP requests to the Mailtrap Email API.

#### Prerequisites

Before we start, you'll need to:

* [Verify your sending domain](https://docs.mailtrap.io/general/sending-domain)
* [Create and save an API token](https://docs.mailtrap.io/general/api-tokens)

### Email Live Sending for Laravel

#### SDK integration

The[ Mailtrap Laravel bridge](https://github.com/mailtrap/mailtrap-php/tree/main/src/Bridge/Laravel) is part of the official Mailtrap PHP SDK and plugs into Laravel's native mail system. You can switch between the Transactional Stream, the Bulk Stream, and Email Sandbox by changing environment variables. The SDK supports:

* Transactional, bulk, and batch email sending
* Email template management
* Contact and contact list management
* Sending domain management
* Sandbox email sending and sandbox project management

{% hint style="info" %}
The Laravel bridge works with Laravel 9.x and later and requires PHP 8.0 or later.
{% endhint %}

#### Installation

Install the SDK together with an HTTP client. We recommend the Symfony HTTP client:

```shellscript
composer require railsware/mailtrap-php symfony/http-client nyholm/psr7 symfony/maile
```

If you prefer Guzzle, run this instead:

```shellscript
composer require railsware/mailtrap-php guzzlehttp/guzzle php-http/guzzle7-adapter symfony/mailer
```

Laravel registers the Mailtrap service provider automatically through package discovery.

### Configuration

* Add the `mailtrap-sdk` mailer to the `mailers` array in `config/mail.php`:

```php
'mailers' => [

    // ...

    'mailtrap-sdk' => [
        'transport' => 'mailtrap-sdk',
    ],

],
```

* Set `mailtrap-sdk` as your default mailer and add your API token in the `.env` file. The sender address must use your verified sending domain:

```shellscript
MAIL_MAILER="mailtrap-sdk"

MAILTRAP_HOST="send.api.mailtrap.io"
MAILTRAP_API_KEY="YOUR_API_TOKEN"

MAIL_FROM_ADDRESS="hello@yourdomain.com"
MAIL_FROM_NAME="${APP_NAME}"
```

To send through the [Bulk Stream](https://docs.mailtrap.io/email-live-sending/setup/bulk-stream), set `MAILTRAP_HOST="bulk.api.mailtrap.io"` instead.

* Clear the configuration cache so Laravel picks up the new variables:

```shellscript
php artisan config:clear
```

#### Minimal example

* Generate a Mailable class:

```shellscript
php artisan make:mail WelcomeMail
```

* Then define its subject and content in `app/Mail/WelcomeMail.php`:

```shellscript
<?php

namespace App\Mail;

use Illuminate\Bus\Queueable;
use Illuminate\Mail\Mailable;
use Illuminate\Mail\Mailables\Content;
use Illuminate\Mail\Mailables\Envelope;
use Illuminate\Queue\SerializesModels;

class WelcomeMail extends Mailable
{
    use Queueable, SerializesModels;

    public function __construct(public string $name)
    {
    }

    public function envelope(): Envelope
    {
        return new Envelope(
            subject: 'Welcome to our app',
        );
    }

    public function content(): Content
    {
        return new Content(
            view: 'mail.welcome-email',
        );
    }
}
```

* Create the email view in `resources/views/mail/welcome-email.blade.php`:

```html
<p>Hi {{ $name }}, welcome aboard!</p>
```

* To send a test email, add an Artisan command to `routes/console.php`:

```php
<?php

use App\Mail\WelcomeMail;
use Illuminate\Support\Facades\Artisan;
use Illuminate\Support\Facades\Mail;

Artisan::command('send-welcome-mail', function () {
    Mail::to('recipient@example.com')->send(new WelcomeMail('Jon'));
})->purpose('Send a welcome email');
```

* Run the command:

```shellscript
php artisan send-welcome-mail
```

The email appears in your [Email Logs](https://docs.mailtrap.io/email-live-sending/analytics/logs) as soon as it's sent.

{% hint style="info" %}
If `mailtrap-sdk` isn't your default mailer, choose it per email with `Mail::mailer('mailtrap-sdk')->to(...)->send(...)`. To send in the background, use `queue()` instead of `send()` and run a queue worker.
{% endhint %}

#### Categories and custom variables

Add a [category](https://docs.mailtrap.io/email-live-sending/analytics/categories) and [custom variables](https://docs.mailtrap.io/email-live-sending/advanced/custom-variables) to filter and analyze your emails in Mailtrap. Set them as headers in the Mailable's `envelope()` method:

```php
use Illuminate\Mail\Mailables\Envelope;
use Mailtrap\EmailHeader\CategoryHeader;
use Mailtrap\EmailHeader\CustomVariableHeader;
use Symfony\Component\Mime\Email;

public function envelope(): Envelope
{
    return new Envelope(
        subject: 'Welcome to our app',
        using: [
            function (Email $email) {
                $email->getHeaders()
                    ->add(new CategoryHeader('Welcome email'))
                    ->add(new CustomVariableHeader('user_id', '45982'))
                    ->add(new CustomVariableHeader('batch_id', 'PSJ-12'));
            },
        ],
    );
}
```

Each email can have one category. Custom variables are limited to 1,000 bytes per email.

#### Send with an email template

The `mailtrap-sdk` transport requires an HTML or text body. To send a [Mailtrap email template](https://docs.mailtrap.io/general/email-templates), use the SDK client directly, for example in `routes/console.php`:

```php
<?php

use Illuminate\Support\Facades\Artisan;
use Mailtrap\MailtrapClient;
use Mailtrap\Mime\MailtrapEmail;
use Symfony\Component\Mime\Address;

Artisan::command('send-template-mail', function () {
    $email = (new MailtrapEmail())
        ->from(new Address('hello@yourdomain.com', 'Your App'))
        ->to(new Address('recipient@example.com', 'Jon'))
        ->templateUuid('YOUR_TEMPLATE_UUID')
        ->templateVariables([
            'user_name' => 'Jon',
        ]);

    MailtrapClient::initSendingEmails(
        apiKey: config('services.mailtrap-sdk.apiKey'),
    )->send($email);
})->purpose('Send a template email');
```

{% hint style="info" %}
Don't set a subject, text, HTML body, or category when you send a template. The template defines them, and the API returns a validation error if you add them.
{% endhint %}

#### Batch sending

To send the same email to many recipients in one API call, use `batchSend()`:

```php
<?php

use Illuminate\Support\Facades\Artisan;
use Mailtrap\MailtrapClient;
use Mailtrap\Mime\MailtrapEmail;
use Symfony\Component\Mime\Address;

Artisan::command('batch-send-mail', function () {
    $mailtrap = MailtrapClient::initSendingEmails(
        apiKey: config('services.mailtrap-sdk.apiKey'),
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
})->purpose('Send a batch email');
```

For more examples, see the [Laravel bridge README](https://github.com/mailtrap/mailtrap-php/tree/main/src/Bridge/Laravel) on GitHub.

#### **SMTP integration**

You can also send with Laravel's built-in `smtp` mailer. To get your credentials:

1. Go to the [Snding Setup](https://mailtrap.io/api-smtp/sending-setup) page under **Live Sending** and choose your domain.
2. Select the Transactional or Bulk Stream.
3. Toggle the switch to **SMTP** and copy the credentials, or copy the ready-made Laravel code sample.

Add the credentials to your `.env` file:

```shellscript
MAIL_MAILER=smtp
MAIL_HOST=live.smtp.mailtrap.io
MAIL_PORT=587
MAIL_USERNAME=api
MAIL_PASSWORD=YOUR_API_TOKEN

MAIL_FROM_ADDRESS="hello@yourdomain.com"
MAIL_FROM_NAME="${APP_NAME}"
```

For the Bulk Stream, use `MAIL_HOST=bulk.smtp.mailtrap.io` with the Bulk Stream credentials. Mailtrap SMTP supports ports 587 (recommended), 2525, 25, and 465. Run `php artisan config:clear` after you change the `.env` file.

To add a category to emails sent over SMTP, set the `X-MT-Category` header in the Mailable's `headers()` method:

```php
use Illuminate\Mail\Mailables\Headers;

public function headers(): Headers
{
    return new Headers(
        text: [
            'X-MT-Category' => 'Welcome email',
        ],
    );
}
```

{% hint style="info" %}
SMTP integration doesn't need the Mailtrap SDK, so you can also use it on Laravel versions older than 9.x. It uses Laravel's standard `smtp` mailer.
{% endhint %}

Read more in the [SMTP integration guide](https://docs.mailtrap.io/email-live-sending/setup/smtp-integration).

**RESTful API integration**

To call the Email API directly, use Laravel's HTTP client. First, add your API token to `config/services.php`:

```php
'mailtrap' => [
    'token' => env('MAILTRAP_API_KEY'),
],
```

Then send a request to the Transactional Stream endpoint:

```php
use Illuminate\Support\Facades\Http;

$response = Http::withToken(config('services.mailtrap.token'))
    ->post('https://send.api.mailtrap.io/api/send', [
        'from' => ['email' => 'hello@yourdomain.com', 'name' => 'Your App'],
        'to' => [['email' => 'recipient@example.com']],
        'subject' => 'Welcome!',
        'text' => 'Thanks for signing up.',
    ]);
```

For the Bulk Stream, send the same request to `https://bulk.api.mailtrap.io/api/send`. For all fields and responses, see the [API reference](https://docs.mailtrap.io/api-docs/email-sending/transactional).

Read more about [API integration](https://docs.mailtrap.io/email-live-sending/setup/api-integration).

### Email Sandbox for Laravel

[Email Sandbox](https://docs.mailtrap.io/getting-started/email-sandbox) catches every email your Laravel app sends, so you can inspect it without reaching real recipients. You don't need a verified domain to use it.

#### **SDK integration**

If you use the Laravel bridge, point it to the Sandbox API and add your sandbox ID to the .env file:

```shellscript
MAIL_MAILER="mailtrap-sdk"

MAILTRAP_HOST="sandbox.api.mailtrap.io"
MAILTRAP_API_KEY="YOUR_API_TOKEN"
MAILTRAP_SANDBOX_ID=YOUR_SANDBOX_ID
```

You'll find the sandbox ID in your sandbox's URL. Run `php artisan config:clear` after you change the variables.

{% hint style="info" %}
The older `MAILTRAP_INBOX_ID` variable still works but is deprecated. If your `config/services.php` defines its own `mailtrap-sdk` entry, change its `inboxId` key to `'sandboxId' => env('MAILTRAP_SANDBOX_ID')` when you rename the variable.
{% endhint %}

#### **SMTP integration**

To use the `smtp` mailer, go to **Sandboxes**, open your sandbox, and copy the credentials from the **Integration** tab. You can also select Laravel under **Code Samples** and copy the ready-made configuration.

```shellscript
MAIL_MAILER=smtp
MAIL_HOST=sandbox.smtp.mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=YOUR_SANDBOX_USERNAME
MAIL_PASSWORD=YOUR_SANDBOX_PASSWORD
```

Each sandbox has its own username and password. Read more in the[ Sandbox SMTP integration guide](https://docs.mailtrap.io/email-sandbox/setup/sandbox-smtp-integration).

#### **Switch from Sandbox to live sending**

When you're ready to send to real recipients, update your .env file and clear the configuration cache:

* **SDK**: set `MAILTRAP_HOST` to `send.api.mailtrap.io` (or `bulk.api.mailtrap.io`) and remove `MAILTRAP_SANDBOX_ID`.
* **SMTP**: replace the Sandbox credentials with your Email Live Sending SMTP credentials.

Set these values per environment, so your development and staging servers send to Sandbox and production sends to real recipients.

#### Troubleshooting

* **`IncompleteDsnException` error**

Laravel didn't load the Mailtrap configuration automatically, which can happen on older Laravel versions. Add it manually to config/services.php:

```php
'mailtrap-sdk' => [
    'host' => env('MAILTRAP_HOST', 'send.api.mailtrap.io'),
    'apiKey' => env('MAILTRAP_API_KEY'),
    'sandboxId' => env('MAILTRAP_SANDBOX_ID'),
],
```

Then run `php artisan config:clear`.

Changes in .env don't take effect

Laravel caches its configuration. Run php artisan config:clear after every change to your mail variables.

* **Changes in `.env` don't take effect**

Laravel caches its configuration. Run `php artisan config:clear` after every change to your mail variables.

* **"Sending from domain is not allowed" error**

The sender address doesn't use a verified sending domain. Make sure `MAIL_FROM_ADDRESS`, and any `from` address you set in a Mailable, uses your verified domain. See[ Domain not allowed](https://docs.mailtrap.io/email-live-sending/troubleshooting/sending-from-domain-not-allowed) for more fixes.

If you need help with your Laravel integration, contact our support team at **support@mailtrap.io**.

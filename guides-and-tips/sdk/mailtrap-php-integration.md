---
title: <i class="fa-php">:php:</i> Mailtrap PHP integration
description: >-
  Integrate Mailtrap with PHP applications using SDK, SMTP, or RESTful API for
  reliable email sending
icon: php
---

# PHP Integration

<a href="https://github.com/mailtrap/mailtrap-php" class="button primary">Mailtrap PHP SDK on GitHub</a>

## PHP Integration

### Overview

Mailtrap can be integrated with PHP apps and projects for email sending.

### Email API/SMTP for PHP

#### SDK integration

The [Mailtrap PHP SDK](https://github.com/mailtrap/mailtrap-php) is a modern, type-safe library for sending transactional and bulk emails from PHP applications. The SDK supports:

* Transactional email sending
* Batch email sending
* Dedicated <i class="fa-laravel">:laravel:</i> [**Laravel**](https://github.com/mailtrap/mailtrap-php/tree/feature/improve-examples/src/bridge/laravel) and <i class="fa-symfony">:symfony:</i> [**Symfony**](https://github.com/mailtrap/mailtrap-php/tree/main/src/Bridge/Symfony) bridges
* Template management
* Contact management
* Sandbox testing
* Account management

Additionally, you can watch the [course released by Symfony Casts](https://symfonycasts.com/screencast/mailtrap) for a step-by-step integration walkthrough.

### Installation

Install the SDK using Composer:

{% code title="Composer" %}
```bash
composer require railsware/mailtrap-php
```
{% endcode %}

### Minimal Example

Here's a minimal example to send your first email:

{% code title="send_email.php" %}
```php
<?php

require 'vendor/autoload.php';

use Mailtrap\Config;
use Mailtrap\EmailHeader\CategoryHeader;
use Mailtrap\Helper\ResponseHelper;
use Mailtrap\MailtrapClient;
use Symfony\Component\Mime\Address;
use Symfony\Component\Mime\Email;

$apiKey = 'your-api-token';
$mailtrap = MailtrapClient::initSendingEmails(
    apiKey: $apiKey
);

$email = (new Email())
    ->from(new Address('hello@example.com', 'Mailtrap Test'))
    ->to(new Address('recipient@example.com'))
    ->subject('Hello from Mailtrap!')
    ->text('Welcome to Mailtrap Email Sending!')
    ->html('<p>Welcome to <strong>Mailtrap</strong> Email Sending!</p>');

try {
    $response = $mailtrap->send($email);
    var_dump(ResponseHelper::toArray($response));
} catch (Exception $e) {
    echo 'Error: ' . $e->getMessage();
}
```
{% endcode %}

{% hint style="info" %}
Get your API token from the Mailtrap dashboard under **Settings → API Tokens**.
{% endhint %}

#### SMTP integration

To integrate SMTP with your PHP app, navigate to the **Integrations** tab, choose the desired PHP framework, and copy-paste the credentials or ready-made code snippets.

{% hint style="info" %}
SMTP integration is compatible with any PHP framework or library that sends emails via SMTP.
{% endhint %}

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/mailtrap-php-smtp-integration.png" alt="" width="563"></div>

Read more about SMTP integration [here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/smtp-integration).

#### RESTful API integration

To integrate Mailtrap using RESTful API, use the configuration available among **Code samples** under the API section.

API integration can be used with any PHP framework or library that supports HTTP requests. For more details, refer to the [API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api).

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/mailtrap-php-api-integration.png" alt="" width="563"></div>

Read more about API integration [here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/api-integration).

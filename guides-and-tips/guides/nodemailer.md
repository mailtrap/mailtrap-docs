---
cover: ../.gitbook/assets/nodemailer-cover.png
coverY: 0
---

# Nodemailer

Integrate Mailtrap with Nodemailer to send and test emails from Node.js apps using the Mailtrap transport or SMTP.

<a href="https://github.com/mailtrap/mailtrap-nodejs" class="button primary">Mailtrap Node.js SDK on GitHub</a>

### Overview

Mailtrap can be integrated with Nodemailer for email sending and testing. You can connect it in two ways:

* **Mailtrap transport**: the [Mailtrap Node.js SDK](https://github.com/mailtrap/mailtrap-nodejs) includes a Nodemailer transport that sends through the Mailtrap Email API, so you keep sending with `transport.sendMail()`.
* **SMTP integration**: Nodemailer's built-in SMTP transport with your Mailtrap SMTP credentials.

#### Prerequisites

Before we start, you'll need to:

* [Verify your sending domain](https://docs.mailtrap.io/general/sending-domain)
* [Create and save an API token](https://docs.mailtrap.io/general/api-tokens)

### Email Live Sending for Nodemailer

#### Mailtrap transport

The Mailtrap transport is part of the official [Mailtrap Node.js SDK](https://github.com/mailtrap/mailtrap-nodejs). It plugs into Nodemailer and sends through the Mailtrap Email API instead of SMTP. You can switch between the Transactional Stream, the Bulk Stream, and Email Sandbox with one transport option. The SDK supports:

* Transactional, bulk, and batch email sending
* Email template management
* Contact and contact list management
* Sending domain management
* Sandbox email sending and sandbox project management

{% hint style="info" %}
The SDK requires Node.js 22 or later and works with Nodemailer 9 and 10.
{% endhint %}

#### Installation

Install the SDK together with Nodemailer:

```bash
npm install mailtrap nodemailer
```

If you use TypeScript with Nodemailer 9, also install the type definitions. Nodemailer 10 includes its own:

```bash
npm install -D @types/nodemailer
```

#### Configuration

* Add your API token to a `.env` file in your project:

```bash
MAILTRAP_API_TOKEN="YOUR_API_TOKEN"
```

* Then create a Nodemailer transport with `MailtrapTransport`:

```javascript
import Nodemailer from "nodemailer";
import { MailtrapTransport } from "mailtrap";

const transport = Nodemailer.createTransport(
  MailtrapTransport({
    token: process.env.MAILTRAP_API_TOKEN,
  })
);
```

To send through the [Bulk Stream](https://docs.mailtrap.io/email-live-sending/setup/bulk-stream), add `bulk: true`:

```javascript
const transport = Nodemailer.createTransport(
  MailtrapTransport({
    token: process.env.MAILTRAP_API_TOKEN,
    bulk: true,
  })
);
```

#### Minimal example

* Create a `send.mjs` file. The sender address must use your verified sending domain:

```javascript
import Nodemailer from "nodemailer";
import { MailtrapTransport } from "mailtrap";

const transport = Nodemailer.createTransport(
  MailtrapTransport({
    token: process.env.MAILTRAP_API_TOKEN,
  })
);

transport
  .sendMail({
    from: { address: "hello@yourdomain.com", name: "Your App" },
    to: "recipient@example.com",
    subject: "Welcome to our app",
    text: "Hi Jon, welcome aboard!",
    html: "<p>Hi Jon, welcome aboard!</p>",
  })
  .then(console.log, console.error);
```

* Run it:

```bash
node --env-file=.env send.mjs
```

The email appears in your [Email Logs](https://docs.mailtrap.io/email-live-sending/analytics/logs) as soon as it's sent.

{% hint style="info" %}
The transport sends `from`, `to`, `cc`, `bcc`, `replyTo`, `subject`, `text`, `html`, `headers`, and `attachments`. Other Nodemailer message options, such as `alternatives`, `icalEvent`, or `priority`, aren't sent.
{% endhint %}

#### Categories and custom variables

Add a [category](https://docs.mailtrap.io/email-live-sending/analytics/categories) and [custom variables](https://docs.mailtrap.io/email-live-sending/advanced/custom-variables) to filter and analyze your emails in Mailtrap. Pass them as `category` and `customVariables` in `sendMail()`:

```javascript
transport.sendMail({
  from: { address: "hello@yourdomain.com", name: "Your App" },
  to: "recipient@example.com",
  subject: "Welcome to our app",
  text: "Hi Jon, welcome aboard!",
  category: "Welcome email",
  customVariables: {
    user_id: "45982",
    batch_id: "PSJ-12",
  },
});
```

Each email can have one category. Custom variables are limited to 1,000 bytes per email.

#### Send with an email template

To send a [Mailtrap email template](https://docs.mailtrap.io/general/email-templates), pass its UUID in `templateUuid` and its variables in `templateVariables`. You'll find the UUID in the template's **Integration** tab:

```javascript
transport.sendMail({
  from: { address: "hello@yourdomain.com", name: "Your App" },
  to: "recipient@example.com",
  templateUuid: "YOUR_TEMPLATE_UUID",
  templateVariables: {
    user_name: "Jon",
  },
});
```

{% hint style="info" %}
The template defines the subject and content, so the transport doesn't send `subject`, `text`, `html`, or `category` with a template.
{% endhint %}

#### Attachments

Add attachments the same way as in any Nodemailer message:

```javascript
transport.sendMail({
  from: { address: "hello@yourdomain.com", name: "Your App" },
  to: "recipient@example.com",
  subject: "Your invoice",
  text: "Your invoice is attached.",
  attachments: [
    {
      filename: "invoice.pdf",
      path: "./invoice.pdf",
    },
  ],
});
```

To send batch emails, use the SDK's `MailtrapClient` instead of the transport. For more examples, see the [Mailtrap Node.js SDK examples](https://github.com/mailtrap/mailtrap-nodejs/tree/main/examples) on GitHub.

#### SMTP integration

You can also send with Nodemailer's built-in SMTP transport. To get your credentials:

1. Go to the [Sending Setup](https://mailtrap.io/api-smtp/sending-setup) page under **Live Sending** and choose your domain.
2. Select the Transactional or Bulk Stream.
3. Toggle the switch to **SMTP** and copy the credentials.

Create the transport with your credentials:

```javascript
import Nodemailer from "nodemailer";

const transport = Nodemailer.createTransport({
  host: "live.smtp.mailtrap.io",
  port: 587,
  auth: {
    user: "api",
    pass: process.env.MAILTRAP_API_TOKEN,
  },
});
```

For the Bulk Stream, use `host: "bulk.smtp.mailtrap.io"` with the Bulk Stream credentials. Mailtrap SMTP supports ports 587 (recommended), 2525, 25, and 465. Set `secure: true` only when you use port 465.

To add a category and custom variables to emails sent over SMTP, set the `X-MT-Category` and `X-MT-Custom-Variables` headers:

```javascript
transport.sendMail({
  from: { address: "hello@yourdomain.com", name: "Your App" },
  to: "recipient@example.com",
  subject: "Welcome to our app",
  text: "Hi Jon, welcome aboard!",
  headers: {
    "X-MT-Category": "Welcome email",
    "X-MT-Custom-Variables": JSON.stringify({ user_id: "45982" }),
  },
});
```

{% hint style="info" %}
SMTP integration doesn't need the Mailtrap SDK, so you can also use it on Node.js versions older than 22.
{% endhint %}

Read more in the [SMTP integration guide](https://docs.mailtrap.io/email-live-sending/setup/smtp-integration).

### Email Sandbox for Nodemailer

[Email Sandbox](https://docs.mailtrap.io/getting-started/email-sandbox) catches every email your Node.js app sends, so you can inspect it without reaching real recipients. You don't need a verified domain to use it.

#### Mailtrap transport

If you use the Mailtrap transport, set `sandbox: true` and add your sandbox ID:

```javascript
const transport = Nodemailer.createTransport(
  MailtrapTransport({
    token: process.env.MAILTRAP_API_TOKEN,
    sandbox: true,
    sandboxId: Number(process.env.MAILTRAP_SANDBOX_ID),
  })
);
```

You'll find the sandbox ID in your sandbox's URL. You can't combine `sandbox: true` with `bulk: true`.

{% hint style="info" %}
The `sandboxId` option requires version 6.2.0 or later of the SDK. Older versions use `testInboxId`, which still works but is deprecated.
{% endhint %}

#### SMTP integration

To use Nodemailer's SMTP transport, go to **Sandboxes**, open your sandbox, and copy the credentials from the **Integration** tab. You can also pick your language or framework under **Code Samples** and copy the ready-made configuration:

```javascript
const transport = Nodemailer.createTransport({
  host: "sandbox.smtp.mailtrap.io",
  port: 2525,
  auth: {
    user: "YOUR_SANDBOX_USERNAME",
    pass: "YOUR_SANDBOX_PASSWORD",
  },
});
```

Each sandbox has its own username and password. Read more in the [Sandbox SMTP integration guide](https://docs.mailtrap.io/email-sandbox/setup/sandbox-smtp-integration).

#### Switch from Sandbox to live sending

When you're ready to send to real recipients, update your transport:

* **Mailtrap transport**: remove `sandbox` and `sandboxId`. Add `bulk: true` to send through the Bulk Stream.
* **SMTP**: replace the Sandbox credentials with your Email Live Sending SMTP credentials.

Set these values per environment, so your development and staging servers send to Sandbox and production sends to real recipients.

#### Troubleshooting

* **"Sending from domain is not allowed" error**

The sender address doesn't use a verified sending domain. Make sure the `from` address in `sendMail()` uses your verified domain. See [Domain not allowed](https://docs.mailtrap.io/email-live-sending/troubleshooting/sending-from-domain-not-allowed) for more fixes.

* **401 Unauthorized error**

The API token is wrong, expired, or has no access to your sending domain. Check the token's permissions in your account. See [Unauthorized (401) error](https://docs.mailtrap.io/email-live-sending/troubleshooting/unauthorized-401-error) for more fixes.

* **"sandboxId is missing, sandbox sending will not work." error**

You set `sandbox: true` without a sandbox ID. Add `sandboxId` to the transport options.

* **"Bulk mode is not applicable for sandbox API." error**

You set both `bulk: true` and `sandbox: true`. Remove `bulk` while you send to Sandbox.

* **"Subject is required." error**

The Mailtrap transport needs a `subject` unless you send with `templateUuid`.

* **SMTP connection errors**

If Nodemailer returns `ECONNECTION` or `ETIMEDOUT`, your network or hosting provider may block the port. Try port 2525, or port 465 with `secure: true`. To test the connection without sending an email, call `transport.verify()`. For Sandbox, see [Sandbox troubleshooting](https://docs.mailtrap.io/email-sandbox/troubleshooting).

If you need help with your Nodemailer integration, contact our support team at **support@mailtrap.io**.

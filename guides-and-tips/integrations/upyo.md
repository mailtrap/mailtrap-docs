---
description: >-
  Learn how to integrate Mailtrap with Upyo, a cross-runtime TypeScript email
  library, to send transactional or sandbox emails using the Mailtrap transport.
---

# Upyo

[Upyo](https://upyo.org/) is a TypeScript library for composing and sending email. You build a message once with `createMessage()` and hand it to a transport, which handles delivery.

This guide covers [@upyo/mailtrap](https://github.com/dahlia/upyo/tree/main/packages/mailtrap), the Upyo transport for Mailtrap. It wraps Mailtrap's [Email API](https://mailtrap.io/email-api/) and [Email Sandbox](https://mailtrap.io/email-sandbox/), so you can send production or test emails through Mailtrap using Upyo's message format.

#### Prerequisites

Before you start, make sure you have:

* A [Mailtrap account](https://mailtrap.io/signup)
* A [Mailtrap API Token](https://docs.mailtrap.io/email-api-smtp/setup/api-tokens)
* A [verified sending domain](https://docs.mailtrap.io/email-api-smtp/setup/sending-domain) (required for production sending; not needed if you're only sending to the Email Sandbox)
* Node.js, Deno, or Bun installed, since Upyo runs across all three

### Installation

Install the `@upyo/mailtrap` package with your package manager of choice:

{% tabs %}
{% tab title="npm" %}
```shellscript
npm add @upyo/mailtrap
```
{% endtab %}

{% tab title="pnpm" %}
```shellscript
pnpm add @upyo/mailtrap
```
{% endtab %}

{% tab title="Yarn" %}
```shellscript
yarn add @upyo/mailtrap
```
{% endtab %}

{% tab title="Deno" %}
```shellscript
deno add jsr:@upyo/mailtrap
```
{% endtab %}

{% tab title="Bun" %}
```shellscript
bun add @upyo/mailtrap
```
{% endtab %}
{% endtabs %}

### Send emails using Upyo and Mailtrap

Create a `MailtrapTransport` with your API token, then build a message with `createMessage()` and send it:

```typescript
import { createMessage } from "@upyo/core";
import { MailtrapTransport } from "@upyo/mailtrap";

const transport = new MailtrapTransport({
  apiToken: "your-mailtrap-api-token",
  sandbox: true,
  inboxId: 12345,
});

const message = createMessage({
  from: "support@example.com",
  to: "customer@example.com",
  subject: "Welcome to our service",
  content: { text: "Thank you for signing up!" },
});

const receipt = await transport.send(message);
if (receipt.successful) {
  console.log("Message sent with ID:", receipt.messageId);
} else {
  console.error("Send failed:", receipt.errorMessages.join(", "));
}
```

Once you copy the script, make sure to:

* Replace `YOUR-MAILTRAP-API-KEY-HERE` with your actual Mailtrap API token
* Replace `YOUR-EMAIL-HERE` with your verified sender address
* Replace `RECIPIENT-EMAIL-HERE` with the recipient's email address

The transport handles the conversion to Mailtrap's JSON format automatically, including HTML/text alternatives, CC, BCC, reply-to, custom headers, priority, attachments, and inline Content-ID attachments so you don't need to build the request payload by hand.

### Email API and Email Sandbox

A single Mailtrap API token works for both Email API and Email Sandbox environments. To choose where your messages go, toggle the `sandbox` option:

* `sandbox: false` (default) – Sends through the production Email API
* `sandbox: true` with an `inboxId` – Captures messages in an Email Sandbox inbox instead of delivering them, so you can test without reaching real recipients

For example:

```typescript
import { createMessage } from "@upyo/core";
import { MailtrapTransport } from "@upyo/mailtrap";

const sandboxTransport = new MailtrapTransport({
  apiToken: "your-mailtrap-api-token",
  sandbox: true,
  inboxId: 12345,
});

const productionTransport = new MailtrapTransport({
  apiToken: "your-mailtrap-api-token",
});

const message = createMessage({
  from: "onboarding@example.com",
  to: "newuser@example.com",
  subject: "Welcome",
  content: { text: "Welcome to our platform." },
});
```

**Note**: You can find your sandbox inbox ID in the URL of the sandbox in your Mailtrap account, e.g. [mailtrap.io/sandboxes/{id](http://mailtrap.io/sandboxes/%7Bid)}.

### Categories, tags, and metadata

Mailtrap classifies messages with a `category` field, which is what powers filtering in Email Categories. Upyo bridges its own generic tagging system to this:

* The first entry in a message's `tags` array becomes the Mailtrap `category`
* If no tags are set, the transport falls back to `defaultCategory` (default: `transactional`)
* Any additional tags are sent as custom variables, prefixed with `tag_`

Set transport-level `metadata` when every message sent through that transport should carry the same tracking fields:

```shellscript
import { createMessage } from "@upyo/core";
import { MailtrapTransport } from "@upyo/mailtrap";

const transport = new MailtrapTransport({
  apiToken: "your-mailtrap-api-token",
  defaultCategory: "transactional",
  metadata: {
    environment: "production",
    service: "accounts",
  },
});

const message = createMessage({
  from: "billing@example.com",
  to: "customer@example.com",
  subject: "Your invoice",
  content: { text: "Your invoice is ready." },
  tags: ["billing", "invoice"],
});
```

In this example, the message is categorized as billing in `Mailtrap`, and `invoice` is attached as a `tag_invoice` custom variable.

### Batch sending

To send multiple messages in one pass, use `sendMany()`. The transport automatically batches up to 500 messages per Mailtrap API call:

```shellscript
import { createMessage } from "@upyo/core";
import { MailtrapTransport } from "@upyo/mailtrap";

const transport = new MailtrapTransport({
  apiToken: "your-mailtrap-api-token",
  sandbox: true,
  inboxId: 12345,
});

const messages = [
  createMessage({
    from: "sender@example.com",
    to: "user1@example.com",
    subject: "Hello 1",
    content: { text: "Message 1" },
  }),
  createMessage({
    from: "sender@example.com",
    to: "user2@example.com",
    subject: "Hello 2",
    content: { text: "Message 2" },
  }),
];

for await (const receipt of transport.sendMany(messages)) {
  if (receipt.successful) {
    console.log("Sent:", receipt.messageId);
  } else {
    console.error("Failed:", receipt.errorMessages.join(", "));
  }
}
```

### Configuration options

| `apiToken`        | Your Mailtrap API token. **Required**.                                                                  |
| ----------------- | ------------------------------------------------------------------------------------------------------- |
| `sandbox`         | Use the Email Sandbox instead of the Email API. Default: `false`.                                       |
| `inboxId`         | Sandbox inbox ID. Required when `sandbox` is `true`.                                                    |
| `sendBaseUrl`     | Email API base URL. Default: `https://send.api.mailtrap.io`                                             |
| `sandboxBaseUrl`  | Sandbox API base URL. Default: `https://sandbox.api.mailtrap.io`                                        |
| `defaultCategory` | Category applied when a message has no tags. Default: `transactional`                                   |
| `metadata`        | Key-value pairs merged into Mailtrap's `custom_variables` for every message sent through the transport. |
| `userAgent`       | `User-Agent` header sent with requests. Default: `@upyo/mailtrap`                                       |
| `timeout`         | Request timeout, in milliseconds. Default: `30000`                                                      |
| `retries`         | Number of retry attempts for transient failures. Default: `3`                                           |
| `headers`         | Additional HTTP headers included on every request.                                                      |

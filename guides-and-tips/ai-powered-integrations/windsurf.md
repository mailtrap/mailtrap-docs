---
title: <i class="fa-wind">:wind:</i> Windsurf and Mailtrap Integration
description: >-
  Learn how to integrate Mailtrap with Windsurf to send emails directly from the
  editor using Cascade and the Mailtrap MCP server.
---

# Windsurf

[Windsurf](https://windsurf.com/) is an AI coding assistant for developers and enterprises that understands your entire codebase and can plan, execute, and iterate on complex multi-file tasks autonomously.

In this guide, you’ll learn how to integrate it with the Mailtrap MCP, which allows you to, amongst other things, perform the following actions:

* [Connect Mailtrap to your project](windsurf.md#connect-mailtrap-to-your-project)
* [Perform Sandbox operations](windsurf.md#sandbox-operations-during-debugging)&#x20;
* [Validate email templates](windsurf.md#template-validation)
* [Forward email templates to your teammates](windsurf.md#sending-emails-to-your-teammate)

#### Prerequisites

Before you start, make sure to:

* Set up your [sending domain](https://docs.mailtrap.io/email-api-smtp/setup/sending-domain) (this takes approximately 5 minutes).
* Install the [latest Node.js version](https://nodejs.org/en) since [Mailtrap MCP](https://www.npmjs.com/package/mcp-mailtrap) is implemented as a Node.js command line utility.

### Step 1. Add Mailtrap MCP config to Windsurf

Open Windsurf, then navigate to **Settings** → **Windsurf** **Settings**.

<figure><img src="../.gitbook/assets/Screenshot 2026-03-17 at 10.18.42.png" alt=""><figcaption></figcaption></figure>

Under **Cascade**, you will see the **Open MCP Marketplace** button. Click on it, and you’ll be taken to the MCP Marketplace page.

<figure><img src="../.gitbook/assets/windsurf 1.png" alt=""><figcaption></figcaption></figure>

On the MCP Marketplace page, click on the **Cogwheel** button, which will open the **mcp.config.json** file.

<figure><img src="../.gitbook/assets/windsurf 2.png" alt=""><figcaption></figcaption></figure>

Then, in the **mcp.config.json** file, copy/paste the following code snippet:

```json
{
  "mcpServers": {
    "mailtrap": {
      "command": "npx",
      "args": ["-y", "mcp-mailtrap"],
      "env": {
        "MAILTRAP_API_TOKEN": "your_mailtrap_api_token",
        "DEFAULT_FROM_EMAIL": "your_sender@example.com",
        "MAILTRAP_ACCOUNT_ID": "your_account_id",
        "MAILTRAP_TEST_INBOX_ID": "your_test_inbox_id"
      }
    }
  }
}
```

### Step 2. Insert Mailtrap credentials

Next, all you need to do is replace the following values in the **mcp\_config.json** file:

* `MAILTRAP_API_TOKEN` – Required for all functionality, used to authenticate API requests, which you can copy/paste from the credentials tab.
* `DEFAULT_FROM_EMAIL` – Required for email sending. Make sure the email’s domain matches your own domain from the **Sending Domains** tab in Mailtrap.

You can find these credentials in your Mailtrap account by navigating to **Sending Domains** → **Integration** → **API**.

<figure><img src="../.gitbook/assets/1.png" alt=""><figcaption></figcaption></figure>

* `MAILTRAP_ACCOUNT_ID` – This is required for template management purposes. You can find the account ID under **Settings** → **Account** **Settings**.&#x20;

<figure><img src="../.gitbook/assets/2.png" alt=""><figcaption></figcaption></figure>

* `MAILTRAP_TEST_INBOX_ID` – If you need sandbox email functionality, you can find this ID in your Sandbox.

<figure><img src="../.gitbook/assets/3.png" alt=""><figcaption></figcaption></figure>

Once you insert your Mailtrap credentials, hit save, and you should see the Mailtrap MCP on the MCP Marketplace page.

<figure><img src="../.gitbook/assets/windsurf 3.png" alt=""><figcaption></figcaption></figure>

If you click on the newly-installed Mailtrap MCP, you’ll see the list of available tools it comes with.

<figure><img src="../.gitbook/assets/windsurf 4.png" alt=""><figcaption></figcaption></figure>

### Windsurf + Mailtrap MCP server use cases

#### Connect Mailtrap to your project

To integrate Mailtrap without manual coding, simply prompt the Windsurf AI to connect Mailtrap to your project with a prompt like this one:

> Integrate Mailtrap into my project so that it can send emails through the Mailtrap email API. Additionally, safely store the Mailtrap credentials from the MCP configuration into an .env file

Windsurf AI will then go through the Mailtrap documentation, integrate the email API, and safely store your credentials in a **.env** file. Then, you can proceed to test the configuration. For instance, here’s our contact form email in our Gmail inbox we used as our `to` address:

<figure><img src="../.gitbook/assets/Screenshot 2026-03-17 at 09.48.11.png" alt=""><figcaption></figcaption></figure>

And here is the same email in the [Mailtrap Email Logs](https://docs.mailtrap.io/email-api-smtp/analytics/logs):

<figure><img src="../.gitbook/assets/Screenshot 2026-03-17 at 09.48.32.png" alt=""><figcaption></figcaption></figure>

#### Sandbox operations during debugging

Reviewing code for sending emails or emails themselves in a staging environment using [Sandbox](https://mailtrap.io/email-sandbox/)?&#x20;

With Windsurf connected to Mailtrap MCP, you can complete the following actions by prompting the agent:

* Verify what the code actually does without switching to the Mailtrap UI and back to the IDE
* Inspect basic message metadata
* Use the returned message ID to request full message details (content, headers, etc.), and more.

<figure><img src="../.gitbook/assets/uc 1.png" alt=""><figcaption></figcaption></figure>

#### Template validation&#x20;

If you want to edit your email templates without switching to the Mailtrap UI, you can prompt the Windsurf AI to list them and fetch a specific template ID:

<figure><img src="../.gitbook/assets/uc 2.png" alt=""><figcaption></figcaption></figure>

Then, if you’re not satisfied with a subject line or two, you can also change them with a simple prompt, just like so:

<figure><img src="../.gitbook/assets/uc 3 (1).png" alt=""><figcaption></figcaption></figure>

#### Sending emails to your teammate

Done revising your emails in Sandbox? If so, you can ask the Windsurf AI to send them to a teammate for a quick review:

<figure><img src="../.gitbook/assets/uc 4.png" alt=""><figcaption></figcaption></figure>

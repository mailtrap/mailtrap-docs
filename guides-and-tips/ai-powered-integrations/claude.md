---
title: <i class="fa-robot">:robot:</i> Claude and Mailtrap Integration
description: >-
  Integrate Mailtrap with Claude Desktop to send transactional and promotional
  emails directly from Claude using Model Context Protocol.
---

# Claude

[Claude](https://claude.ai/) is Anthropic’s AI agent built to help you tackle complex challenges, analyze data, write code, and think through your work.

In this guide, you’ll learn how to integrate it with the Mailtrap MCP, which allows you to, amongst other things, perform the following actions:

* [Connect Mailtrap to your project](claude.md#sandbox-operations)
* [Perform Sandbox operations](claude.md#sandbox-operations)
* [Fetch, validate, and edit email templates](claude.md#template-validation)
* [Forward email templates to your teammates](claude.md#integrating-mailtrap-into-your-project)

**Prerequisites**:&#x20;

* If you haven’t set up your sending domain already, you’ll need to do it before we start — it takes \~5 minutes, and you can use our [step-by-step article](https://help.mailtrap.io/article/69-sending-domain-setup) as a guide.
* Install the [latest Node.js version](https://nodejs.org/en) since [Mailtrap MCP](https://www.npmjs.com/package/mcp-mailtrap) is implemented as a Node.js command line utility.

### How to add Mailtrap MCP to Claude

To add Mailtrap MCP to Claude, simply go to **Connectors** → **Manage Connectors**, click on the **+ (plus)** sign and then **Browse connectors**.

<figure><img src="../.gitbook/assets/Screenshot 2026-03-18 at 11.41.18.png" alt=""><figcaption></figcaption></figure>

Then, search for Mailtrap and select it from the **Connectors**:

<figure><img src="../.gitbook/assets/Screenshot 2026-03-18 at 11.38.52.png" alt=""><figcaption></figcaption></figure>

Click on **Install** on the following page:

<figure><img src="../.gitbook/assets/Screenshot 2026-03-18 at 11.54.32.png" alt=""><figcaption></figcaption></figure>

Next, all you need to do is insert the following Mailtrap credentials:

<figure><img src="../.gitbook/assets/Screenshot 2026-03-18 at 11.55.51.png" alt=""><figcaption></figcaption></figure>

* `MAILTRAP_API_TOKEN` – Required for all functionality, used to authenticate API requests, which you can copy/paste from the credentials tab.
* `DEFAULT_FROM_EMAIL` – Required for email sending. Make sure the email’s domain matches your own domain from the **Sending Domains** tab in Mailtrap.

You can find these credentials in your Mailtrap account by navigating to **Sending Domains** → **Integration** → **API**.

<figure><img src="../.gitbook/assets/1 (3).png" alt=""><figcaption></figcaption></figure>

* `MAILTRAP_ACCOUNT_ID` – This is required for template management purposes. You can find the account ID under **Settings** → **Account Settings**.&#x20;

<figure><img src="../.gitbook/assets/2 (2).png" alt=""><figcaption></figcaption></figure>

* `MAILTRAP_TEST_INBOX_ID` – If you need sandbox email functionality, you can find this ID in your Sandbox.

<figure><img src="../.gitbook/assets/3 (2).png" alt=""><figcaption></figcaption></figure>

After you insert your Mailtrap credentials, make sure to enable the MCP on the following window, and you’re all set!

<figure><img src="../.gitbook/assets/Screenshot 2026-03-18 at 11.56.53.png" alt=""><figcaption></figcaption></figure>

### Claude + Mailtrap MCP server use cases

#### Sandbox operations&#x20;

Reviewing code for sending emails or emails themselves in a staging environment using [Sandbox](https://mailtrap.io/email-sandbox/)

With Claude connected to Mailtrap MCP, you can complete the following actions by prompting the agent:

* Verify what the code actually does without switching to the Mailtrap UI and back to the IDE
* Inspect basic message metadata
* Use the returned message ID to request full message details (content, headers, etc.), and more.

<figure><img src="../.gitbook/assets/use case 1.png" alt=""><figcaption></figcaption></figure>

#### Template validation&#x20;

To edit your email templates without switching to the Mailtrap UI, you can prompt Claude to list them and fetch a specific template ID:

<figure><img src="../.gitbook/assets/use case 2.png" alt=""><figcaption></figcaption></figure>

Then, if you’re not satisfied with a subject line or two, you can also change them with a simple prompt, just like so:

<figure><img src="../.gitbook/assets/use case 3.png" alt=""><figcaption></figcaption></figure>

#### Sending emails to your teammate

Done revising your emails in Sandbox? If so, you can ask Claude to send them to a teammate for a quick review:

<figure><img src="../.gitbook/assets/use case 4.png" alt=""><figcaption></figcaption></figure>

#### Integrating Mailtrap into your project

If you’re using [Claude Code](https://claude.com/product/claude-code) to work on your project, you can ask the AI to integrate Mailtrap into your project or even migrate from another service provider by changing the configuration.

All you need to do is use a prompt like this one:

> Integrate Mailtrap into my project so that it can send emails through the Mailtrap email API. Additionally, safely store the Mailtrap credentials from the MCP configuration into an .env file

Claude Code will then go through the Mailtrap documentation, integrate the email API, and safely store your credentials in a .env file. Then, you can proceed to test the configuration. For instance, here’s our contact form email in our Gmail inbox we used as our `to` address:

<figure><img src="../.gitbook/assets/Screenshot 2026-03-17 at 09.48.11 (2).png" alt=""><figcaption></figcaption></figure>

And here is the same email in the [Mailtrap Email Logs](https://docs.mailtrap.io/email-api-smtp/analytics/logs):

<figure><img src="../.gitbook/assets/Screenshot 2026-03-17 at 09.48.32 (2).png" alt=""><figcaption></figcaption></figure>

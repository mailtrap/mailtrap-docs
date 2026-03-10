# Qodo

[Qodo](https://qodo.ai/) is an AI code review platform that gives engineering teams deep codebase context to move faster without sacrificing code quality. In this guide, you’ll learn how to integrate it with Mailtrap MCP.&#x20;

**Note**: You can use your AI agent to help you integrate Mailtrap or even migrate from another email service provider.

### Prerequisites

Before you start, make sure to:

* Set up your [sending domain](https://docs.mailtrap.io/email-api-smtp/setup/sending-domain) (this takes approximately 5 minutes).
* Install the [latest Node.js version](https://nodejs.org/en) since [Mailtrap MCP](https://www.npmjs.com/package/mcp-mailtrap) is implemented as a Node.js command line utility.
* Install or update the IDE you’re using for Qodo.ai to the latest version.

### Step 1. Add Mailtrap MCP to Qodo.ai

First, open Qodo.ai from your preferred IDE. This can be VS Code, JetBrains IDEs, etc. For the purposes of this guide, we’ll use VSC.

Next, click on the **Tools** button right above the Qodo AI chatbox.

<figure><img src="../.gitbook/assets/Screenshot 2026-03-10 at 19.50.30.png" alt=""><figcaption></figcaption></figure>

Then, click on + **Add new MCP**.

<figure><img src="../.gitbook/assets/Screenshot 2026-03-10 at 19.50.52.png" alt=""><figcaption></figcaption></figure>

Once the following window appears after you click on **Add new MCP**, copy/paste the following code snippet:

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

### Step 2. Insert Mailtrap API credentials

Next, all you need to do is replace the following values in the **settings.json** file:

* `MAILTRAP_API_TOKEN` – Required for all functionality, used to authenticate API requests, which you can copy/paste from the credentials tab.
* `DEFAULT_FROM_EMAIL` – Required for email sending. Make sure the email’s domain matches your own domain from the **Sending Domains** tab in Mailtrap.

You can find these credentials in your Mailtrap account by navigating to **Sending Domains** → **Integration** → **API**.

<figure><img src="../.gitbook/assets/Screenshot 2026-03-10 at 17.06.42.png" alt=""><figcaption></figcaption></figure>

* `MAILTRAP_ACCOUNT_ID` – This is required for template management purposes. You can find the account ID under **Settings** → **Account Settings**.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2026-03-10 at 17.07.13.png" alt=""><figcaption></figcaption></figure>

* `MAILTRAP_TEST_INBOX_ID` – If you need sandbox email functionality, you can find this ID in your Sandbox.

<figure><img src="../.gitbook/assets/Screenshot 2026-03-10 at 17.07.34.png" alt=""><figcaption></figcaption></figure>

### Qodo.AI + Mailtrap MCP server possible use cases

#### Sandbox operations during code review

Imagine that you’re reviewing a part of the code responsible for sending emails and that you’re working in a staging environment using [Sandbox](https://mailtrap.io/email-sandbox/).

While reviewing your code, you want to trigger email-sending logic to better understand or verify behavior, test emails, etc.

This is possible from the Qodo agent, which lets you use simple prompts to, among other things:&#x20;

* Verify what the code actually does without switching to the Mailtrap UI and back to the IDE
* Inspect basic message metadata
* Use the returned message ID to request full message details (content, headers, etc.), and more.

<figure><img src="../.gitbook/assets/Screenshot 2026-03-10 at 19.51.12.png" alt=""><figcaption></figcaption></figure>

#### Template validation during code review

Let’s say that while reviewing code, you notice a Mailtrap template ID being used and you’re unsure whether it’s the correct template.

From the Qodo agent, you can request the list of available templates in the Mailtrap account.

<figure><img src="../.gitbook/assets/Screenshot 2026-03-10 at 19.51.36.png" alt=""><figcaption></figcaption></figure>

This allows you to quickly confirm that the referenced template is correct, directly within the review flow.

Don’t like the subject line of your template? Tweak it with a simple prompt, just like so:

<figure><img src="../.gitbook/assets/Screenshot 2026-03-10 at 19.51.46.png" alt=""><figcaption></figcaption></figure>

#### Sending emails to your teammate

You’re working on designing an email or a template, and you want your teammate’s opinion.

For this, you can prompt Qodo something like this:

<figure><img src="../.gitbook/assets/Screenshot 2026-03-10 at 19.52.12.png" alt=""><figcaption></figcaption></figure>

#### Migrating from another email service provider

If you’re migrating from another email service provider or just starting out with Mailtrap, you can ask the Qodo agent to update your credentials so you can start sending emails in no time.

Simply copy/paste the credentials or one of the ready-made code snippets into the chatbox and prompt the AI, like so:

<figure><img src="../.gitbook/assets/Screenshot 2026-03-10 at 19.52.45.png" alt=""><figcaption></figcaption></figure>

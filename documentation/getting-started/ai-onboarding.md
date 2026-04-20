---
description: Easy-to-follow documentation to onboard your AI agent to Mailtrap.
---

# AI Onboarding

Building with AI? Mailtrap provides several resources to make your life easier:

* [Mailtrap MCP server](ai-onboarding.md#mailtrap-mcp-server)
* [Mailtrap docs for agents](ai-onboarding.md#mailtrap-docs-for-agents)
* [Mailtrap CLI app](ai-onboarding.md#mailtrap-cli-app)
* [Mailtrap skills](ai-onboarding.md#mailtrap-skills)

{% content-ref url="email-api-smtp.md" %}
[email-api-smtp.md](email-api-smtp.md)
{% endcontent-ref %}

{% content-ref url="/broken/pages/kUZPOczjlPDqtc17WDgZ" %}
[Broken link](/broken/pages/kUZPOczjlPDqtc17WDgZ)
{% endcontent-ref %}

{% content-ref url="/broken/pages/V3u4qiAblbvKfyv8G2fn" %}
[Broken link](/broken/pages/V3u4qiAblbvKfyv8G2fn)
{% endcontent-ref %}

### Getting started

Before you start, keep in mind that we require a human to:

* Sign up for a [free Mailtrap account](https://mailtrap.io/register/signup)
* Create an [API Token](https://docs.mailtrap.io/email-api-smtp/setup/api-tokens)

### Mailtrap MCP server

With the[ Mailtrap MCP server](https://github.com/mailtrap/mailtrap-mcp), you can perform various email operations through your favorite AI IDE (e.g., VS Code, Cursor, etc.) or your AI assistant (e.g., Claude). Some of the use cases include sending transactional emails, testing emails in your sandbox, managing templates, getting sending statistics, and more.

The Mailtrap MCP server is implemented as a Node.js command line utility and comes with quick-install buttons and pre-made code snippets for easy installation:

{% tabs %}
{% tab title="Claude or Cursor" %}
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
{% endtab %}

{% tab title="VS Code" %}
```json
{
  "mcp": {
    "servers": {
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
}
```
{% endtab %}

{% tab title="Claude (asdf)" %}
```json
{
  "mcpServers": {
    "mailtrap": {
      "command": "/Users/<username>/.asdf/shims/npx",
      "args": ["-y", "mcp-mailtrap"],
      "env": {
        "PATH": "/Users/<username>/.asdf/shims:/usr/bin:/bin",
        "ASDF_DIR": "/opt/homebrew/opt/asdf/libexec",
        "ASDF_DATA_DIR": "/Users/<username>/.asdf",
        "ASDF_NODEJS_VERSION": "20.6.1",
        "MAILTRAP_API_TOKEN": "your_mailtrap_api_token",
        "DEFAULT_FROM_EMAIL": "your_sender@example.com",
        "MAILTRAP_ACCOUNT_ID": "your_account_id",
        "MAILTRAP_TEST_INBOX_ID": "your_test_inbox_id"
      }
    }
  }
}
```
{% endtab %}

{% tab title="MCP Bundle (MCPB)" %}
```json
# Build TypeScript and pack the MCPB bundle
npm run mcpb:pack

# Inspect bundle metadata
npm run mcpb:info

# Sign the bundle for distribution (optional)
npm run mcpb:sign
```
{% endtab %}
{% endtabs %}

{% content-ref url="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/mcp-server" %}
[Mailtrap MCP Server](https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/mcp-server)
{% endcontent-ref %}

### Mailtrap docs for agents

To give your agent more context regarding Mailtrap you can share the following docs:

<details>

<summary>Markdown</summary>

To fetch a markdown version of any page from Mailtrap documentation, simply add `.md` to the end of the page URL. For instance:

> AI onboarding documentation https://docs.mailtrap.io/getting-started/ai-onboarding.md

</details>

<details>

<summary>Full llms.txt</summary>

Or, you can also give your agent to all of our docs in a single llms.txt file:

> Full Mailtrap documentation https://docs.mailtrap.io/llms-full.txt

</details>

### Mailtrap CLI app

With [Mailtrap’s CLI app](https://github.com/mailtrap/mailtrap-cli), you can send emails, inspect sandbox, monitor deliverability stats, and administer domains, templates, contacts, and more – all from your terminal.&#x20;

To install, you can download the latest release from [GitHub Releases](https://github.com/mailtrap/mailtrap-cli/releases) and add it to your PATH, or use either Homebrew:

```
brew install mailtrap/cli/mailtrap
```

or Go:

```
go install github.com/mailtrap/mailtrap-cli@latest
```

Here’s some examples:

```json
# Send a transactional email
mailtrap send transactional \
  --from "app@yourdomain.com" \
  --to "user@example.com" \
  --subject "Order confirmed" \
  --html "<h1>Thanks for your order</h1>"

# Check spam score on a sandbox message
mailtrap messages spam-score --sandbox-id 12345 --id 67890

# Pull sending stats by mailbox provider
mailtrap stats by-esp --domain-id 111 --period 30

# Bulk import contacts from JSON
mailtrap contacts import --file contacts.json
```

### Mailtrap skills

Mailtrap skills allow you to give your AI coding assistant accurate Mailtrap context for tasks such as sending emails, testing with sandbox, using email templates, setting up a sending domain, and managing contacts.

To install, simply copy the [skills folders](https://github.com/mailtrap/mailtrap-skills) into the directory your agent reads. For example, for Cursor, that’s `.cursor/skills/`. Or, you can install via npx:

```
npx skills add mailtrap/mailtrap-skills
```

And here's a table with each skill and a brief description&#x20;

| Skill                                                                                                                 | Description                                                                                                                                |
| --------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| [`sending-emails`](https://github.com/mailtrap/mailtrap-skills/tree/main/skills/sending-emails)                       | Use when integrating, configuring, or troubleshooting Mailtrap (Email API or SMTP).                                                        |
| [`testing-with-sandbox`](https://github.com/mailtrap/mailtrap-skills/tree/main/skills/testing-with-sandbox)           | Use when capturing outbound email in development or staging in a fake inbox.                                                               |
| [`using-email-templates`](https://github.com/mailtrap/mailtrap-skills/tree/main/skills/using-email-templates)         | Use when creating, managing, and sending Mailtrap-hosted email templates.                                                                  |
| [`setting-up-sending-domain`](https://github.com/mailtrap/mailtrap-skills/tree/main/skills/setting-up-sending-domain) | Use when adding or verifying a Mailtrap sending domain.                                                                                    |
| [`managing-contacts`](https://github.com/mailtrap/mailtrap-skills/tree/main/skills/managing-contacts)                 | Use when using Mailtrap Contacts API or UI to add, update, bulk import, list, segment marketing contacts, custom fields, or custom events. |

---
description: Easy-to-follow documentation to onboard your AI agent to Mailtrap.
---

# AI Onboarding

Building with AI? Mailtrap provides several resources to make your life easier:

* [Mailtrap MCP server](ai-onboarding.md#mailtrap-mcp-server)
* [Mailtrap docs for agents](ai-onboarding.md#mailtrap-docs-for-agents)
* [Mailtrap CLI app](ai-onboarding.md#mailtrap-cli-app)
* [Mailtrap skills](ai-onboarding.md#mailtrap-skills)
* [AI prompts to set up sending](https://docs.mailtrap.io/for-ai-agents/ai-prompts-to-set-up-sending)
* [AI inbox](https://docs.mailtrap.io/for-ai-agents/ai-inbox)

{% hint style="info" %}
**Useful links**:

* [Mailtrap LLMS.txt](https://mailtrap.io/llms.txt)
* [Mailtrap docs LLMS.txt](https://docs.mailtrap.io/llms.txt)
{% endhint %}

{% content-ref url="../getting-started/email-api-smtp.md" %}
[email-api-smtp.md](../getting-started/email-api-smtp.md)
{% endcontent-ref %}

{% content-ref url="https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-sandbox" %}
[Email Sandbox](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-sandbox)
{% endcontent-ref %}

{% content-ref url="https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-marketing" %}
[Email Marketing](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-marketing)
{% endcontent-ref %}

### Getting started

Before you start, keep in mind that we require a human to:

* Sign up for a [free Mailtrap account](https://mailtrap.io/register/signup)
* Create an [API Token](https://docs.mailtrap.io/email-api-smtp/setup/api-tokens)

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><i class="fa-money-check-pen">:money-check-pen:</i> <strong>Mailtrap Pricing Plans</strong></td><td><em>Discover Mailtrap's flexible plans to cover the needs of your business.</em></td><td><a href="../account-and-organization/billing/plans.md">plans.md</a></td></tr><tr><td><i class="fa-shield-check">:shield-check:</i> <strong>Mailtrap's Trust Center</strong></td><td><em>A detailed overview of Mailtrap's security and privacy practices</em></td><td><a href="https://trust.mailtrap.io/">https://trust.mailtrap.io/</a></td></tr></tbody></table>

### AI integrations

Get started quickly with our official AI integrations.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td>Claude</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/claude">Claude</a></td></tr><tr><td>Codex</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/codex">Codex</a></td></tr><tr><td>Cursor</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/cursor">Cursor</a></td></tr><tr><td>Antigravity</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/antigravity">Antigravity</a></td></tr><tr><td>Anything</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/anything">Anything</a></td></tr><tr><td>Augment Code</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/augment-code">Augment Code</a></td></tr><tr><td>Base44</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/base44">Base44</a></td></tr><tr><td>BuildAI</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/buildai">BuildAI</a></td></tr><tr><td>Bolt.new</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/bolt-new">Bolt.new</a></td></tr><tr><td>GitHub Copilot</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/github-copilot">GitHub Copilot</a></td></tr><tr><td>Leap.new</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/leap-new">Leap.new</a></td></tr><tr><td>Lovable</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/lovable">Lovable</a></td></tr><tr><td>OpenClaw</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/openclaw">OpenClaw</a></td></tr><tr><td>Qodo</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/qodo">Qodo</a></td></tr><tr><td>OpenCode</td><td></td></tr><tr><td>Replit</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/replit">Replit</a></td></tr><tr><td>Reflex Build</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/reflex-build">Reflex Build</a></td></tr><tr><td>V0</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/v0">V0</a></td></tr><tr><td>Visual Studio Code (VS Code)</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/vs-code">Visual Studio Code (VS Code)</a></td></tr><tr><td>Devin AI (ex Windsurf)</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/ai-powered-integrations/windsurf">Devin AI (ex Windsurf)</a></td></tr></tbody></table>

### Ready to get started?

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><i class="fa-brain-circuit">:brain-circuit:</i> AI Onboarding</td><td><a href="ai-onboarding.md">ai-onboarding.md</a></td></tr><tr><td><i class="fa-rectangle-terminal">:rectangle-terminal:</i> Mailtrap CLI app</td><td><a href="mailtrap-cli-app.md">mailtrap-cli-app.md</a></td></tr><tr><td><i class="fa-gears">:gears:</i> Mailtrap Skills</td><td><a href="skills.md">skills.md</a></td></tr><tr><td><i class="fa-rectangle-terminal">:rectangle-terminal:</i> Mailtrap MCP Server</td><td><a href="mcp-server.md">mcp-server.md</a></td></tr><tr><td><i class="fa-robot">:robot:</i> AI prompts to set up sending</td><td><a href="ai-prompts-to-set-up-sending.md">ai-prompts-to-set-up-sending.md</a></td></tr><tr><td><i class="fa-inbox-in">:inbox-in:</i> AI inbox</td><td><a href="ai-inbox.md">ai-inbox.md</a></td></tr></tbody></table>

### Mailtrap MCP server

With the [Mailtrap MCP server](https://github.com/mailtrap/mailtrap-mcp), you can perform various email operations through your favorite AI IDE (e.g., VS Code, Cursor, etc.) or your AI assistant (e.g., Claude). Some of the use cases include sending transactional emails, testing emails in your sandbox, managing templates, getting sending statistics, and more.

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

{% content-ref url="/broken/spaces/gkNigAKiqQtQub1GOdjY/pages/Zc2hzutZptTaPF3PE9rx" %}
[Broken link](/broken/spaces/gkNigAKiqQtQub1GOdjY/pages/Zc2hzutZptTaPF3PE9rx)
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

With [Mailtrap’s CLI app](https://github.com/mailtrap/mailtrap-cli), you can send emails, inspect sandbox, monitor deliverability stats, and administer domains, templates, contacts, and more – all from your terminal.

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

And here's a table with each skill and a brief description

| Skill                                                                                                                 | Description                                                                                                                                |
| --------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| [`sending-emails`](https://github.com/mailtrap/mailtrap-skills/tree/main/skills/sending-emails)                       | Use when integrating, configuring, or troubleshooting Mailtrap (Email API or SMTP).                                                        |
| [`testing-with-sandbox`](https://github.com/mailtrap/mailtrap-skills/tree/main/skills/testing-with-sandbox)           | Use when capturing outbound email in development or staging in a fake inbox.                                                               |
| [`using-email-templates`](https://github.com/mailtrap/mailtrap-skills/tree/main/skills/using-email-templates)         | Use when creating, managing, and sending Mailtrap-hosted email templates.                                                                  |
| [`setting-up-sending-domain`](https://github.com/mailtrap/mailtrap-skills/tree/main/skills/setting-up-sending-domain) | Use when adding or verifying a Mailtrap sending domain.                                                                                    |
| [`managing-contacts`](https://github.com/mailtrap/mailtrap-skills/tree/main/skills/managing-contacts)                 | Use when using Mailtrap Contacts API or UI to add, update, bulk import, list, segment marketing contacts, custom fields, or custom events. |

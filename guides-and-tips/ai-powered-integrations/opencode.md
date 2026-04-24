# OpenCode

OpenCode Integration with Mailtrap

[OpenCode](https://opencode.ai) is an open-source AI coding agent that runs in the terminal, as a desktop app, or inside IDE extensions.&#x20;

This guide shows how to connect it to Mailtrap using the [Mailtrap MCP server](https://docs.mailtrap.io/guides/ai-powered-integrations/mcp-server), giving your agent the ability to add email sending to your project, inspect sandbox inboxes, manage templates, and check delivery stats; all from natural-language prompts.

### Prerequisites

* A [Mailtrap account](https://mailtrap.io/register/signup) with a [configured sending domain](https://docs.mailtrap.io/email-api-smtp/setup/sending-domain) (takes \~5 minutes)
* [Node.js](https://nodejs.org/en) installed on your machine (mcp-mailtrap runs as a Node.js command-line utility)
* OpenCode installed — via brew install `anomalyco/tap/opencode, npm i -g opencode-ai@latest`, or the [install script](https://opencode.ai/install)

### Step 1: Set up Mailtrap

In your Mailtrap account, you just need to generate the API token. Go to Settings → API Tokens → Add Token and copy your token. The rest is handled by the MCP.&#x20;

### Step 2: Add the Mailtrap MCP server to OpenCode

Open or create an opencode.json file in your project root. Add the Mailtrap MCP server under the mcp key:

```bash
{
  "mcp": {
    "mailtrap": {
      "type": "local",
      "command": ["npx", "-y", "mcp-mailtrap"],
      "environment": {
        "MAILTRAP_API_TOKEN": "your_mailtrap_api_token",
        "DEFAULT_FROM_EMAIL": "your_sender@example.com",
        "MAILTRAP_ACCOUNT_ID": "your_account_id",
        "MAILTRAP_TEST_INBOX_ID": "your_test_inbox_id"
      },
      "enabled": true
    }
  }
}
```

For a global setup (available across all projects), place the same file at `~/.config/opencode/opencode.json` instead.

### Step 3: Insert your Mailtrap credentials

Replace the placeholder values in `opencode.json`:

| MAILTRAP\_API\_TOKEN      | Required for all operations; copy from Sending Domains → Integration → API |
| ------------------------- | -------------------------------------------------------------------------- |
| DEFAULT\_FROM\_EMAIL      | Required for sending; must be an address on your verified sending domain   |
| MAILTRAP\_ACCOUNT\_ID     | Required for template management; find under Settings → Account Settings   |
| MAILTRAP\_TEST\_INBOX\_ID | Required for sandbox operations; visible in your sandbox inbox URL         |

OpenCode also supports environment variable substitution via `{env:VAR_NAME}` syntax. If you’d rather keep credentials out of the config file, set them as environment variables and reference them like this:

```bash
{
  "mcp": {
    "mailtrap": {
      "type": "local",
      "command": ["npx", "-y", "mcp-mailtrap"],
      "environment": {
        "MAILTRAP_API_TOKEN": "{env:MAILTRAP_API_TOKEN}",
        "DEFAULT_FROM_EMAIL": "{env:DEFAULT_FROM_EMAIL}",
        "MAILTRAP_ACCOUNT_ID": "{env:MAILTRAP_ACCOUNT_ID}",
        "MAILTRAP_TEST_INBOX_ID": "{env:MAILTRAP_TEST_INBOX_ID}"
      },
      "enabled": true
    }
  }
}
```

Note that the most common approach to setting environment variables is `~/.zshrc` for API keys you use across multiple tools. If you’re working with different projects and credentials, the better approach is `.env` + `direnv`.\
\
For instance, if you’re on macOS with zsh, check the options below:

* **For current terminal sessions only**:

```bash
 export OPENAI_API_KEY="sk-..."
```

Run this before starting OpenCode. It’s gone when the terminal closes.

* **Persistent (accross all sessions)**:

Add the export line to `~/.zshrc`:

```bash
export OPENAI_API_KEY="sk-..."
```

* **Per-project (without polluting your shell)**:

Put vars in a `.env` file at the project root and load them with a tool like `direnv`, or source the file manually:

```bash
# .env
OPENAI_API_KEY="sk-..."
# then in terminal
source .env
```

* **Verify a variable is set**:&#x20;

```bash
echo $OPENAI_API_KEY
```

### Step 4: Verify the MCP server is active

Launch OpenCode in your project directory:

```bash
opencode
```

Once the TUI loads, the Mailtrap MCP server starts automatically. OpenCode discovers all tools exposed by mcp-mailtrap and makes them available to the agent. You can confirm by asking:

```bash
What Mailtrap tools do you have access to?
```

The agent should list the available tools — send email, list sandbox messages, manage templates, and others.

### Step 5: Add Mailtrap to your project through OpenCode

Type a natural-language prompt directly in the OpenCode TUI. For example:

```bash
Add Mailtrap email sending to this Node.js project using their API.
Use the API token from my environment variables.
```

<figure><img src="../.gitbook/assets/OpenCode add MT to project.png" alt=""><figcaption></figcaption></figure>

OpenCode runs the action, makes the necessary updates, and confirms the addition/update.

#### More prompt examples

**Inspect sandbox messages**:

```bash
Show me the last 5 emails in my Mailtrap sandbox inbox.
```

<figure><img src="../.gitbook/assets/OpenCode get sandbox messages.png" alt=""><figcaption></figcaption></figure>

**Manage templates**:

```bash
List all my email templates and show me the subject line of each.
```

<figure><img src="../.gitbook/assets/OpenCode list email templates.png" alt=""><figcaption></figcaption></figure>

**Get sending stats**:

```bash
Pull delivery stats for yourdomain.example
```

<figure><img src="../.gitbook/assets/OpenCode get email stats.png" alt=""><figcaption></figcaption></figure>

### Step 6: Use OpenCode in headless mode for CI/CD

OpenCode’s `run` command lets you execute prompts non-interactively, which is useful for automated email testing in CI/CD pipelines:

```bash
opencode run "Send a test email to qa@example.com with subject 'CI build
#$BUILD_NUMBER complete' and check the sandbox inbox for delivery confirmation."
```

This runs the prompt, executes the MCP tool calls, and exits; no interactive session required.

<figure><img src="../.gitbook/assets/OpenCode CLI test.png" alt=""><figcaption></figcaption></figure>

Confirmed in the sandbox.&#x20;

<figure><img src="../.gitbook/assets/OpenCode CLI test positive.png" alt=""><figcaption></figcaption></figure>

### Use cases

* **Bulk template actions** - List all templates, review them for consistency or branding issues, then batch-update subjects, categories, or markup across templates.
* **Delivery forensics** - "Why didn't user X get their email?" → query `list-email-logs` filtered by recipient, check status/bounce/rejection events, pull the raw EML via `get-email-log-message`, diagnose the root cause.
* **Domain setup assistant** - `create-sending-domain`, then `get-sending-domain` with `include_setup_instructions` to get DNS records, and have AI explain exactly what to add in your DNS provider (Cloudflare, Route53, etc.).&#x20;
* **Incident triage** - "Are emails going out?" → check `get-sending-stats` for the last hour, filter `list-email-logs` by `status: not_delivered`, and surface any spike in bounces or rejections.
* **Opt-out audit** - Filter email logs by `status: opted_out` to understand unsubscribe patterns and correlate with specific categories or time periods.
* **Weekly email health report** - Pull `get-sending-stats` broken down by date for the past week, have the AI summarize trends in delivery rates, opens, clicks, bounces, and flag anomalies.

### Supported functionality

* Email sending operations
* Email logs (debug delivery)
* Sending statistics&#x20;
* Sandbox operations
* Template operations&#x20;
* Sending domains management

### Technical notes

* OpenCode applies a 30-second timeout when initializing MCP servers at startup. If your network is slow and `npx` needs to download `mcp-mailtrap` for the first time, the server may time out silently. Run `npx -y mcp-mailtrap` once manually to cache the package before launching OpenCode.
* The `{env:VAR_NAME}` syntax in `opencode.json` resolves at startup, not at tool-call time. If you change an environment variable, restart OpenCode to pick up the new value.
* Project-level config (`opencode.json` in the project root) takes precedence over global config (`~/.config/opencode/opencode.json`). If you define the Mailtrap MCP server in both, the project-level definition wins.

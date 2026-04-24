# Codex

Codex is OpenAI’s open-source AI coding agent, available as a CLI tool, desktop app, IDE extension, and cloud agent at chatgpt.com/codex. This guide shows how to connect it to Mailtrap using the [Mailtrap MCP server](https://docs.mailtrap.io/guides/ai-powered-integrations/mcp-server).&#x20;

Once configured, Codex can help you with email sending operations, including email logs, statistics, email templates, and sending domain management. Also, you can use sandbox operations - all through natural language prompts.&#x20;

### Prerequisites

* Node.js 16+ installed on your machine (20 LTS recommended; mcp-mailtrap runs as a Node.js command-line utility)
* Codex CLI installed via `npm i -g @openai/codex` or `brew install --cask codex`
* An OpenAI account (sign in with your ChatGPT account, or set `OPENAI_API_KEY`)

### Step 1: Set up Mailtrap

In your Mailtrap account, you just need to generate the API token. Go to Settings → API Tokens → Add Token and copy your token. The rest is handled by the MCP.&#x20;

### Step 2: Add the Mailtrap MCP server to Codex

The fastest way is the Codex CLI’s built-in mcp add command:

`codex mcp add mailtrap -- npx -y mcp-mailtrap`

This registers the Mailtrap MCP server in your Codex config. To add it manually instead, open `~/.codex/config.toml` and add:

```bash
[mcp_servers.mailtrap]
command = "npx"
args = ["-y", "mcp-mailtrap"]
[mcp_servers.mailtrap.env]
MAILTRAP_API_TOKEN = "your_mailtrap_api_token"
DEFAULT_FROM_EMAIL = "your_sender@example.com"
MAILTRAP_ACCOUNT_ID = "your_account_id"
MAILTRAP_TEST_INBOX_ID = "your_test_inbox_id"ome code
```

For a project-scoped setup, place a `codex.toml` file with the same MCP block in your project root instead.

### Step 3: Insert your Mailtrap credentials

If you used `codex mcp add`, open `~/.codex/config.toml` and add the `env` block under `[mcp_servers.mailtrap]`. Replace the placeholder values:

| MAILTRAP\_API\_TOKEN      | Required for all operations; copy from Sending Settings → API Tokens → Add Token |
| ------------------------- | -------------------------------------------------------------------------------- |
| DEFAULT\_FROM\_EMAIL      | Required for sending; must be on your verified sending domain                    |
| MAILTRAP\_ACCOUNT\_ID     | Required for template management; find under Settings → Account Settings         |
| MAILTRAP\_TEST\_INBOX\_ID | Required for sandbox operations; visible in your sandbox inbox URL               |

Codex reads standard env vars, so exporting `MAILTRAP_API_TOKEN` in your shell profile works as expected.

### Step 4: Configure tool approval modes

Codex lets you control how much autonomy the agent has per MCP tool. By default, Codex asks for confirmation before executing any MCP tool call. You can adjust this per tool:

```bash
[mcp_servers.mailtrap.tools.send_email]
approval_mode = "approve"
[mcp_servers.mailtrap.tools.list_sandbox_messages]
approval_mode = "auto"
```

<figure><img src="../.gitbook/assets/Codex function approval.png" alt=""><figcaption></figcaption></figure>

Available modes:

| approve | Codex shows the parameters and waits for your confirmation (default, safest for sending)               |
| ------- | ------------------------------------------------------------------------------------------------------ |
| auto    | Codex executes the tool without asking (useful for read-only operations like listing sandbox messages) |

This gives you fine-grained control: let the agent freely inspect your sandbox inbox, but require explicit approval before sending any email.

### Step 5: Add Mailtrap to your project through Codex

Launch Codex and type a natural-language prompt:

```bash
Add Mailtrap email sending to this Node.js project using their API. Use the API token from my environment variables.
```

Codex runs the action, makes the necessary updates, verifies the server file, and confirms the acitons.

<figure><img src="../.gitbook/assets/Codex add Mailtrap to project.png" alt=""><figcaption></figcaption></figure>

#### More prompt examples

Inspect sandbox messages:

```bash
Show me the last 5 emails in my Mailtrap sandbox.
```

<figure><img src="../.gitbook/assets/Codex list inbox messages.png" alt=""><figcaption></figcaption></figure>

Manage templates:

```bash
List all my email templates and show me the subject line of each.
```

<figure><img src="../.gitbook/assets/Codex list all my templates.png" alt=""><figcaption></figcaption></figure>

Get sending stats:

```bash
Pull delivery stats for yourdomain.example
```

<figure><img src="../.gitbook/assets/Codex get sending stats.png" alt=""><figcaption></figcaption></figure>

Codex gives you the stats, including a quick overview and commentary. You can dig deeper for email performance within an email category or provider or check the email logs.&#x20;

### Step 6: Use Codex in headless mode for CI/CD

Codex’s quiet mode runs prompts non-interactively, which is useful for automated email testing in CI/CD pipelines:

```bash
codex -q --json "Send a test email to qa@example.com with subject
  'CI build #${BUILD_NUMBER} complete' and check the sandbox
  inbox for delivery confirmation."
```

The `--json` flag returns structured output, making it easy to parse results in your pipeline scripts.

### Use Cases

* Trigger a test email to Mailtrap’s Email Sandbox while reviewing email-sending code and inspect message content, headers, and metadata without leaving the terminal
* Ask Codex to scaffold Mailtrap into a new project: it installs the SDK, writes API calls, and sets up environment variables based on your MCP config
* Iterate on email templates mid-session by fetching the current template list, editing subject lines or body copy, and pushing updates; all through prompts
* Verify that a transactional trigger (password reset, order confirmation) sends the correct content by prompting Codex to fire the email and inspect the result in sandbox

### Supported Functionality

* Email sending operations
* Email logs (debug delivery)
* Sending statistics&#x20;
* Sandbox operations
* Template operations&#x20;
* Sending domains management

### Technical notes

* Codex applies a 10-second default startup timeout for MCP servers (configurable via startup\_timeout\_sec in the TOML config). If npx needs to download mcp-mailtrap for the first time, run npx -y mcp-mailtrap once manually to cache the package.
* Tool-call timeout defaults to 60 seconds (tool\_timeout\_sec). This is more than enough for Mailtrap API operations but worth knowing if you’re chaining multiple calls.
* In Full Auto mode, Codex disables network access in the sandbox for security. MCP tool calls still work because they run through the MCP protocol outside the sandbox. However, any code Codex writes and executes that tries to call Mailtrap’s API directly will be blocked. Use Suggest or Auto Edit mode for live API testing.
* Project-level config (codex.toml in the project root) merges with global config (\~/.codex/config.toml). If both define the Mailtrap MCP server, the project-level definition takes precedence.

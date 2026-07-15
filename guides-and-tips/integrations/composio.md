---
description: Learn how to integrate Mailtrap with Composio.
---

# Composio

This article shows you how to connect your Mailtrap account to Composio and use its 49 pre-built Mailtrap actions inside AI agent workflows.&#x20;

The integration gives agents direct access to Mailtrap’s sandbox inspection, template management, contact operations, deliverability analytics, and domain configuration. It's available across every framework Composio supports: Python, TypeScript, LangChain, CrewAI, AutoGen, Google ADK, LlamaIndex, Vercel AI SDK, and Mastra.&#x20;

By the end of this guide, your agents will be able to query sandbox results, manage email templates, and monitor sending stats through natural language without you ever opening the Mailtrap account.

**Prerequisties:**

* Composio account - sign up at [composio.dev](https://composio.dev) (free tier includes 20,000 tool calls/month, no credit card required)
* Composio API key from your Composio dashboard
* Mailtrap account with an [API token](https://mailtrap.io/settings/api-tokens) (generate one with Send access enabled)
* Verified sending domain in your Mailtrap account - required for production sending workflows; not needed for Sandbox-only use
* An AI agent project using any framework Composio supports (we assume you have a working agent and need Mailtrap tools to extend it)
* Node.js 18+ installed - required for the TypeScript SDK and MCP paths

#### Step 1. Collect your credentials

You need two sets of credentials before configuring the integration.

<details>

<summary><strong>From Mailtrap</strong></summary>

* **API token** – Go to [API Tokens](https://mailtrap.io/api-tokens) and create a token with Send access.
* **Account ID** – Found in [Account Management](https://mailtrap.io/account-management).
* **Sandbox inbox ID** – In your Mailtrap account, open your Email Sandbox project, select a sandbox, and copy the inbox ID from the URL.

<figure><img src="../.gitbook/assets/composio 1.png" alt=""><figcaption></figcaption></figure>

</details>

<details>

<summary><strong>From Composio</strong></summary>

1. Sign in to your [Composio dashboard](http://dashboard.composio.dev)&#x20;
2. Navigate to **API Keys** and copy your Composio API key (if you haven't already, create one by clicking the **Create API Key** button).

<figure><img src="../.gitbook/assets/composio 2.png" alt=""><figcaption></figcaption></figure>

</details>

#### Step 2. Connect Mailtrap to Composio

Composio manages authentication through its Connect Link system; a secure hosted page where users authorize each integration. For Bearer Token integrations like Mailtrap, this means providing your Mailtrap API token once; Composio stores it against your user\_id and makes all 49 Mailtrap actions available to agents running under that ID.

<details>

<summary>Via the Composio dashboard</summary>

* Go to [app.composio.dev/integrations](https://app.composio.dev/integrations), search for Mailtrap, and click Connect&#x20;

<figure><img src="../.gitbook/assets/composio 3 (1).png" alt=""><figcaption></figcaption></figure>

* Enter 'bearer' for authentication and paste your Mailtrap API token.

<figure><img src="../.gitbook/assets/composio 4.png" alt="" width="375"><figcaption></figcaption></figure>

If the connection is successful, Composio will mark Mailtrap as active and you'll see your account in **Connected Apps**.

<figure><img src="../.gitbook/assets/composio 5 (1).png" alt=""><figcaption></figcaption></figure>

</details>

<details>

<summary>Via the Composio CLI</summary>

```
npm install -g @composio/cli
composio add mailtrap
```

When prompted, paste your Mailtrap API token. The CLI confirms the connection and lists the available Mailtrap actions.

</details>

#### Step 3. Install the Composio SDK

**TypeScript / Node.js**:

```
npm install @composio/core
```

**Python**:

```
pip install composio
```

#### Connect via MCP (alternative path)

If you’re using an MCP-compatible client - Claude Desktop, Cursor, or a custom MCP agent - Composio exposes all Mailtrap tools through a URL-based MCP endpoint. No additional packages are needed beyond @composio/core.

```
import { Composio } from '@composio/core';

const composio = new Composio({ apiKey: process.env.COMPOSIO_API_KEY });
const session = await composio.create('your-user-id');

// Pass these to any MCP client
console.log('MCP endpoint:', session.mcp.url);
console.log('Headers:', session.mcp.headers);
```

Connect your MCP client to `session.mcp.url` using the headers from `session.mcp.headers`. All 49 Mailtrap actions appear as tools in the MCP client automatically - no per-tool configuration required.

### Use cases&#x20;

Some of the potential use cases of Composio and Mailtrap integration include:

* **Sandbox QA loop** – After your agent sends a test email through Mailtrap SMTP, have it call `MAILTRAP_LIST_MESSAGES` and `MAILTRAP_GET_MESSAGE_HTML_BODY` to inspect the sandbox result and validate subject, rendering, and links — without opening the Mailtrap account.
* **Email template audit** – Let an agent update your email templates directly from plain-language instructions: “Update the password-reset template to shorten the body copy and replace the footer logo” triggers `MAILTRAP_UPDATE_EMAIL_TEMPLATE` with the changes applied automatically.
* **Deliverability check** – Run a daily deliverability check with a scheduled agent: it calls `MAILTRAP_GET_SENDING_STATS_BY_DATE`, compares bounce and open rates against your thresholds, and alerts your team via another Composio toolkit if something looks off.
* **CRM contact sync** – When a new user signs up, trigger an agent to call `MAILTRAP_CREATE_CONTACT` and assign them to the right list, with custom fields populated directly from your CRM data.
* **Suppression hygiene** – Have a scheduled agent review your bounces, complaints, and unsubscribes, calling `MAILTRAP_LIST_SUPPRESSIONS` to pull list health data and report back on which segments need cleanup before your next send.

For the full list of 49 tools that come with Composio and Mailtrap integration, [click here](https://docs.composio.dev/toolkits/mailtrap).

### Technical notes

* **No send action in the Composio toolkit** – The 49 Mailtrap actions cover management and testing: inbox inspection, template CRUD, contact operations, domain configuration, and deliverability analytics. There is no `MAILTRAP_SEND_EMAIL` action. To send production emails, call Mailtrap’s Email API or SMTP directly in your agent code. Composio handles everything around the sending lifecycle.
* **Composio MCP uses HTTP transport, not stdio** – This is a different architecture from mcp-mailtrap, which uses stdio. The two are independent products: use Composio MCP when you need multi-toolkit agents (Mailtrap alongside Slack, GitHub, HubSpot, etc.); use mcp-mailtrap for a lightweight Mailtrap-only MCP server.
* **`user_id` isolates credentials** – For single-developer setups, any consistent string works. For multi-tenant applications, pass each user’s unique identifier so their Mailtrap credentials stay separate.
* **Tool call billing** – Each Mailtrap action call counts as one Composio tool call. The free tier includes 20,000/month. A sandbox inspection loop calling three actions per test run uses three tool calls per cycle.
* **Toolkit version** – The Mailtrap toolkit in Composio is versioned at 20260506\_00 as of this writing.

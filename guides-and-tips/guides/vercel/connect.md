---
description: >-
  Step-by-step guide on how to connect Mailtrap to your application hosted on
  Vercel through Vercel Connect.
---

# Vercel Connect

Vercel Connect lets your Vercel apps and AI agents request Mailtrap credentials at runtime instead of storing an API key in environment variables.

{% hint style="info" %}
If you'd rather have Mailtrap credentials added to your project as environment variables, use the [native Vercel integration](https://docs.mailtrap.io/guides/integrations/vercel) instead.
{% endhint %}

#### **Prerequisites**

* Admin rights for your Mailtrap account.
* A [verified sending domain](https://docs.mailtrap.io/email-api-smtp/setup/sending-domain) set up within Mailtrap (for sending emails).
* An existing Vercel account with one or more projects.

### Step-by-step integration guide

{% stepper %}
{% step %}
### Create a Mailtrap API token

* Log in to your Mailtrap account.
* Navigate to **Settings** → [**API Tokens**](https://mailtrap.io/settings/api-tokens).
* Click **Add Token** and give it permissions for the domains, sandboxes, and inboxes your app uses.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/Pasted image 2026-11-18 06.15.38.png" alt=""></div>

* Copy the token since you'll need it in the next step.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/Pasted image 2026-11-18 06.16.41.png" alt="" height="256" width="624"></div>
{% endstep %}

{% step %}
### Create the Mailtrap connector

* Open the [Mailtrap connector](https://vercel.com/connect/mailtrap) page or search for it on the Browse Connectors page.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/Pasted image 2026-11-18 06.17.56.png" alt="" height="243" width="624"></div>

{% hint style="info" %}
Using an AI coding agent? On the Mailtrap connector page, click **Copy Prompt** and paste it into Claude Code, Cursor, or a similar agent to have it set up the connector for you. Keep in mind that you’ll still need a Mailtrap API token from the first step.
{% endhint %}

* In the **Configure** window, fill in the following:
  * **Name** – A name for the connector, for example `acme-mailtrap`.
  * **UID (optional)** – The ID you'll use in your code, for example `mailtrap/acme-mailtrap`. If left empty, Vercel generates it from the name.
  * Select **Shared API Keys** to store one Mailtrap token on the connector for all users of your app.
  * **Key** – Paste the Mailtrap API token you created in the previous step.
  * **Expiration (optional)** – Leave as _No expiration_, or set a date to match your token rotation policy.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/Pasted image 2026-11-18 06.18.45.png" alt="" width="563"></div>

* Click **Create Connector**, then **Continue** on the following window.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/unnamed (1) (1).png" alt="" width="375"><figcaption></figcaption></figure></div>

When your Mailtrap API token expires, Mailtrap API requests stop until you add a new token. To replace it, open the connector in Vercel and update the key under **Settings**.
{% endstep %}

{% step %}
#### Verify the integration in Vercel

Once you create the connector, confirm that the Mailtrap credential is configured and the connector is active on the connector page:

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/Screenshot 2026-11-17 at 16.45.43.png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Connect your Vercel project

* On the connector page, click **Connect Project**.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/Screenshot 2026-11-17 at 17.08.21.png" alt=""><figcaption></figcaption></figure></div>

* Select the project and the environments that should have access.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/Screenshot 2026-11-17 at 17.08.51.png" alt=""><figcaption></figcaption></figure></div>

And that's it! Your project can now request Mailtrap credentials from its builds and runtime.

To use the connector during local development, run `vercel link` and `vercel env pull` in your project folder.
{% endstep %}
{% endstepper %}

### How to test the integration

To confirm the connector works before building it into your app, you can run a quick check from your project folder.

{% hint style="info" %}
For this test to work, you'll need to

* Install Vercel CLI (`npm i -g vercel`)
* Log in (`vercel login`)
* Have Node.js 20.6 or later installed
* Have your project connected to the connector with the Development environment selected
{% endhint %}

* **Open a terminal and go to your project’s root folder:**

```bash
cd <path-to-your-project>
```

If you don’t have your project’s code locally (for example, if you built the app with v0), create an empty folder for the test instead:

```bash
mkdir mailtrap-test && cd mailtrap-test
```

The test doesn’t need your project’s code. In step 3, you’ll link this folder to your existing Vercel project.

**Important**: Run all of the following commands from this folder, not from your home directory.

* **Install the Vercel Connect SDK, if you haven’t already:**

```
npm install @vercel/connect
```

* **Link the folder to your Vercel project and pull its credentials:**

```
vercel link
vercel env pull
```

When prompted, select the project you connected to the connector.

* **Create a file named `test.mjs` in the same folder by running the following command (it writes the test code into the file):**

Replace `<CONNECTOR_NAME>` with the part of the UID after `mailtrap/` shown on your connector page.

```bash
cat > test.mjs << 'EOF'
import { getToken } from '@vercel/connect';

const token = await getToken('mailtrap/<CONNECTOR_NAME>', { subject: { type: 'app' } });

const res = await fetch('https://mailtrap.io/api/accounts', {
  headers: { Authorization: `Bearer ${token}` },
});
console.log(res.status, await res.json());
EOF
```

* **Run the file:**

```bash
node --env-file=.env.local test.mjs
```

If you see status 200 and your Mailtrap account details, the integration works. Feel free to delete test.mjs, or the whole test folder, afterward.

{% hint style="danger" %}
If you used an empty test folder, don’t run `vercel deploy` from it. That would replace your live app with the test file.
{% endhint %}

### How to use the Mailtrap connector in your application

* Install the Vercel Connect SDK:

```bash
npm install @vercel/connect
```

* Then request the Mailtrap credential from server-side code using your connector UID:

```bash
import { getToken } from '@vercel/connect';

const token = await getToken('mailtrap/<CONNECTOR_NAME>', { subject: { type: 'app' } });
```

* Use the returned token to authenticate Mailtrap API requests:

```bash
const headers = {
  Authorization: `Bearer ${token}`,
  'Content-Type': 'application/json',
};
```

{% hint style="info" %}
Replace `<CONNECTOR_NAME>` with the part of the UID after mailtrap/ shown on your connector page.
{% endhint %}

### Use cases

Some of the most common use cases include:

* **An AI-built app that sends email** – You’ve built an app with[ v0](https://v0.app) or the[ AI SDK](https://vercel.com/ai-sdk), Vercel’s toolkit for adding AI to apps, and want it to send signup confirmations, password resets, or receipts through the[ Mailtrap Email API](https://mailtrap.io/email-api/). The connector supplies the API key, so it never appears in your app’s code.
* **An AI agent with an email tool** – Your agent can send emails or look things up in Mailtrap, while the model itself never sees the API key.
* **Inbound agents** – Your agent gets its own email address and reads incoming messages through the[ Inbound Email API](https://docs.mailtrap.io/inbound-email/overview), for example to handle support requests or process replies.
* **Test email workflows** – Send messages to [Email Sandbox](https://mailtrap.io/email-sandbox/) and inspect them without delivering anything to real recipients.

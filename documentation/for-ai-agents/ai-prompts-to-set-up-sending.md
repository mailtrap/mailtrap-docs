# AI prompts to set up sending

Mailtrap provides its users with ready-to-copy prompts that include the context AI agents like Cursor or Copilot need to integrate sending into your app/project. You can use AI prompts when you want to:

* **Start sending emails in minutes** without having to manually copy/paste sending configurations.
* **Avoid typos and mistakes** that commonly come when handling code.
* **Learn how the actual code works** by following what AI is doing.

{% hint style="info" %}
In case you have an AI agent that you want to onboard to Mailtrap, please use [this page](https://docs.mailtrap.io/getting-started/ai-onboarding.md). We also offer the following official skills for AI agents:

* [Sending emails](https://github.com/mailtrap/mailtrap-skills/tree/main/skills/sending-emails)
* [Using email templates](https://github.com/mailtrap/mailtrap-skills/tree/main/skills/using-email-templates)
* [Setting up a sending domain](https://github.com/mailtrap/mailtrap-skills/tree/main/skills/setting-up-sending-domain)
{% endhint %}

### How to use AI prompts&#x20;

First, navigate to the [**Sending Setup**](https://mailtrap.io/api-smtp/sending-setup) page under **API/SMTP** and choose one of the three available prompt types:

1. **API** – Focuses on integrating via the Mailtrap Email API
2. **SMTP** – Focuses on configuring SMTP sending
3. **AI** – Generates a prompt that covers the complete Mailtrap sending setup

<figure><img src="../.gitbook/assets/Screenshot 2026-08-13 at 11.45.49.png" alt=""><figcaption></figcaption></figure>

Keep in mind that the generated prompt depends on several selections, so make sure you choose the right options before copying it. These include the following:

* **Domain** – The sending domain being configured
* **Stream** – Transactional or [Bulk](https://docs.mailtrap.io/email-api-smtp/setup/bulk-stream)
* **Prompt type** – AI, API, or SMTP
* **Technology stack** – Choose the stack that matches your project. For example, cURL, PHP, Node.js, etc.&#x20;

Once you're done selecting the desired parameters, simply click **Copy for AI** and get your prompt.

<figure><img src="../.gitbook/assets/Screenshot 2026-08-13 at 12.06.41.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Since AI is prone to hallucination and errors, make sure to verify the output before sending any emails to real users.
{% endhint %}

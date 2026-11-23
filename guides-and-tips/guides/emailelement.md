---
cover: ../.gitbook/assets/emailelement-cover (1).png
coverY: 0
---

# EmailElement

Use Mailtrap as an email service provider in EmailElement to send your campaigns.

<a href="https://docs.emailelement.com/en/SendIntegrations/Mailtrap" class="button primary">EmailElement documentation</a>

### Overview

Set up Mailtrap as a sending provider in EmailElement to get reliable delivery and detailed analytics, while you manage your campaigns in EmailElement. You can use Mailtrap on its own or alongside other providers.

#### Prerequisites

Before we start, you'll need to:

* [Verify your sending domain](https://docs.mailtrap.io/general/sending-domain) in Mailtrap. The same domain must also be verified in EmailElement.
* Have at least one sender address on that domain.

### Create a webhook in Mailtrap

The webhook sends delivery events back to EmailElement.

1. In Mailtrap, go to **Settings** → **Webhooks** and create a new webhook.
2. Enter `https://deliverywebhook.emailelement.com/api/event/mailtrap` as the webhook URL.
3. Select the stream you send through, and select only the domain you use in EmailElement.

### Create an API token

1. In Mailtrap, go to **Settings** → **API Tokens** and click **Add Token**.
2. Under **Permissions** → **API/SMTP**, select **Admin** for the domain you use in EmailElement.
3. Click **Save** and copy the token.

### Add Mailtrap to EmailElement

1. In EmailElement, go to **Send Integrations** and click **Create Send Integration**.
2. Choose the integration type, pick **Mailtrap**, and click **Next**.
3. Enter a name for the integration and select one or more sender domains.
4. Paste your API token. Custom headers are optional and are added to every email the integration sends.
5. Click **Create**.

### Test the integration

Click **Run Test** on the integration. EmailElement shows the result for each sender domain, and the integration goes active when at least one domain succeeds.

### Troubleshooting

* **Authentication failed**: check that the API token is correct and still active in Mailtrap.
* **Domain not verified**: verify the sender domain in both EmailElement and Mailtrap, and check its DNS records.
* **Run Test fails for one domain**: that domain isn't set up in Mailtrap. Check it there, along with its DNS records.
* **Nothing appears in Delivery Events**: the webhook isn't reaching EmailElement. Check the webhook settings in Mailtrap.

If you need help with your EmailElement integration, contact our support team at **support@mailtrap.io**.

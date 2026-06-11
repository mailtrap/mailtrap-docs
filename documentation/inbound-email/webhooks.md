# Webhooks

In this article, you'll learn how to configure Mailtrap webhooks to get notified about every new message you receive in your inbound email inbox.

### How it works

When a new email arrives, Mailtrap POSTs a JSON payload to your webhook URL. The payload includes an `events` array where each object contains the event (`inbound.message_received`), a unique event ID, a Unix timestamp, the inbox ID, the Mailtrap message ID, and the sender name.

Payloads are signed with HMAC-SHA256 via the `mailtrap-signature` header so you can verify they came from Mailtrap. Failed deliveries retry with exponential backoff — up to 10 attempts over 24 hours.

#### Step 1. Either [create your webhook via API](https://docs.mailtrap.io/developers/email-sending/webhooks) or go to [Mailtrap webhooks](https://mailtrap.io/webhooks), click on Create New Webhook

#### Step 2. Add your Webhook URL, select Inbound Inboxes, and select your Inbox

<figure><img src="../.gitbook/assets/webhook 1.png" alt=""><figcaption></figcaption></figure>

#### Step 3. Once you receive a message in your Inbound Inbox, you should see the following output from your webhook:

<figure><img src="../.gitbook/assets/webhook 2.png" alt=""><figcaption></figcaption></figure>

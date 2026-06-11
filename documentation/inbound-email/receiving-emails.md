# Receiving Emails

In this article, you'll learn how to create an inbound inbox and start receiving emails.

#### Step 1. Create a folder via the API

First, you need to create a folder for categorizing and storing your inboxes. To **create a folder**, use the following command:

```
curl -X POST https://mailtrap.io/api/inbound/folders \
  -H 'Authorization: Bearer YOUR_API_KEY' \
  -H 'Content-Type: application/json' \
  -d '{ "name": "Support" }'
```

**Note**: Make sure to replace `YOUR_API_KEY` with your actual [Mailtrap API token](https://docs.mailtrap.io/email-api-smtp/setup/api-tokens).

The command should give you the following output: `{"id":10,"name":"Support"}%`

#### Step 2. Create an inbox via the API

Insert your folder ID, enter the desired inbox name, and create an inbox with the following command:

```
curl -X POST https://mailtrap.io/api/inbound/folders/{folder_id}/inboxes \
  -H 'Authorization: Bearer YOUR_API_KEY' \
  -H 'Content-Type: application/json' \
  -d '{ "name": "Support tickets" }'
```

The terminal should send you a following message: `{"id":15,"name":"Support tickets","address":"demo-inbox-62fedace@inbound-mailtrap.io"}%`

Your inbound inbox in this case would be: **demo-inbox-62fedace@inbound-mailtrap.io** and you could start sending emails to this address.

#### Step 3. List messages from your inbound inbox

Mailtrap returns a fully parsed email object, including envelope fields (sender, recipients, subjects), metadata (Message-ID, references) and raw headers, all in a single JSON.

To **list messages** from your inbound inbox, use the following command:

```
curl -X GET 'https://mailtrap.io/api/inbound/inboxes/{inbox_id}/messages' \
  -H 'Authorization: Bearer YOUR_API_KEY'
```

**Note**: Make sure to replace `{inbox_id}` with your actual inbox ID (i.e., 15).

You should get the following output:&#x20;

`{"id":"1866872391602282496","inbox_id":15,"from":"Ivan Djuric` [`demo.eth@gmail.com`](mailto:demo.eth@gmail.com)`","to":["demo-inbox-62fedace@inbound-mailtrap.io"],"cc":[],"bcc":[],"reply_to":null,"subject":"Hello from the other side","message_id":"`[`2C613DD4-6E5E-429C-B430-60325BA31E25@gmail.com`](mailto:2C613DD4-6E5E-429C-B430-60325BA31E25@gmail.com)`","in_reply_to":null,"references":[],"headers":{"mime-version":"1.0 (Mac OS X Mail 16.0 \(3864.600.51.1.1\))","return-path":"`[`demo.eth@gmail.com`](mailto:demo.eth@gmail.com)`"},"size":3665,"html_size":null,"text_size":24,"received_at":"2026-06-02T08:17:31.878Z","attachments":[]}`

You can use the message ID, the `id` field, to **get a message**:

```
curl -X GET https://mailtrap.io/api/inbound/inboxes/{inbox_id}/messages/{id} \
  -H 'Authorization: Bearer YOUR_API_KEY'
```

Or, **delete a message** if you wish:

```
curl -X DELETE https://mailtrap.io/api/inbound/inboxes/{inbox_id}/messages/{id} \
  -H 'Authorization: Bearer YOUR_API_KEY'
```

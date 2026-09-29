# viaSocket

This article walks you through connecting Mailtrap to [viaSocket](https://viasocket.com/) and building two working flows:

1. One that sends an order confirmation through Email API/SMTP, tested first against Email Sandbox.
2. One that turns a customer reply into a CRM record.

By the end, you will have a published flow that receives a real email, extracts the sender, finds or creates the matching contact in your CRM, and files the message against it, within seconds of the message arriving and without writing a service to receive mail.

The flows below are the ones we built and ran. Every payload, field name and response in this article came out of those runs.

{% hint style="info" %}
The Mailtrap integration in viaSocket is in beta and its action list changes. Check the actions available in your workspace before you start.
{% endhint %}

### Prerequisites

* A Mailtrap account with Email API/SMTP enabled. Inbound Email is included with Email API/SMTP and is not a separate purchase.
* An account-level Mailtrap API token from [API Tokens](https://mailtrap.io/api-tokens). A token scoped to a single sending domain can read inbound data but cannot create folders or inboxes.
* A [verified sending domain](https://mailtrap.io/sending/domains) if you want to send to real recipients. Sending from an unverified domain fails. Sends to an Email Sandbox inbox do not need one.
* A [viaSocket workspace](https://viasocket.com/) on any plan. Everything here runs on the free tier.
* A destination application for the received data, such as a CRM. Our example uses Pipedrive.

You do not need a domain or DNS access to receive email. This guide uses a hosted **@inbound-mailtrap.io** address that Mailtrap provisions for you. Receiving on your own domain works through an MX record, but it is not required.

### What you are building

Two flows, which together form a loop.

**The sending flow** has two steps. Something happens in another system, and Mailtrap sends the customer an email through Email API/SMTP.

**The receiving flow** has four steps and a branch:

1. **New Email Received**. The Mailtrap trigger, bound to one Inbound Email inbox.
2. **JS Code**. Pulls the bare address out of the From header.
3. **Search Person**. Looks the contact up in the CRM.
4. **Multiple Paths**. Branches on what the search returned:
   1. **No contact found**. Create Person, then Create Note against the new contact.
   2. **Contact found**. Create Note against the existing contact.

The branch matters. Without it the flow either fails on unknown senders or creates duplicate contacts for known ones.

### Step 1. Create a Mailtrap API token

1. In Mailtrap, go to **Settings** → **API Tokens**.
2. Create a token with account-level access.
3. Copy the token and store it securely. You cannot view it again after you leave the page.

<figure><img src="../.gitbook/assets/Screenshot 2026-09-29 at 09.23.11.png" alt=""><figcaption></figcaption></figure>

You need this token twice: once to create the inbound address in **Step 4**, and once to create the viaSocket connection in **Step 2**. The flows themselves never handle it.

### Step 2. Connect Mailtrap in viaSocket

1. In viaSocket, open **Connections**.
2. Choose **Connect New App** and select Mailtrap.
3. Paste the API token from Step 1.
4. Give the connection a name you will recognise later.

<figure><img src="../.gitbook/assets/viaSocket 2.png" alt=""><figcaption></figcaption></figure>

A workspace can hold several Mailtrap connections, so the name is worth setting properly. Every Mailtrap step in every flow asks which connection to use.

{% hint style="info" %}
viaSocket stores a copy of the token rather than refreshing it. When you rotate the token in Mailtrap, update the connection too, or the flows start failing.
{% endhint %}

### Step 3. Send an email from a flow

Add a step, then search the app picker for **Mailtrap**. Select it, then **Send Transactional Email** under the **SEND** group.&#x20;

<figure><img src="../.gitbook/assets/viaSocket 3.png" alt=""><figcaption></figcaption></figure>

Set **Content Mode** to **Write Content** and fill in the fields:

| **Field**      | **Value**                                                    |
| -------------- | ------------------------------------------------------------ |
| **From Email** | An address on a sending domain you have verified in Mailtrap |
| **To Email**   | The recipient                                                |
| **Subject**    | The subject line                                             |
| **Text Body**  | The plain text body                                          |

**From Name**, **To Name** and **HTML Body** are optional. **Additional Fields** carries the remaining Email API parameters.&#x20;

<figure><img src="../.gitbook/assets/viaSocket 4 (1).png" alt=""><figcaption></figcaption></figure>

Click **TEST**. A successful send returns the Email API response:

```json
{
  "success": true,
  "message_ids": ["your-message-id"]
}
```

This action sends through Email API/SMTP. It has no inbox selector because it does not target an Email Sandbox inbox.&#x20;

<figure><img src="../.gitbook/assets/viaSocket 5.png" alt=""><figcaption></figcaption></figure>

To test the same flow without sending real mail, use **Send Sandbox Email** under the **SANDBOX** group instead. It takes the same From, To, Subject and body fields plus a required **Sandbox** picker, which lists the Email Sandbox inboxes on your account by name and unread count. A successful test returns the Email Sandbox response, with a numeric message id:

```json
{
  "success": true,
  "message_ids": ["5721659288"]
}
```

The message lands in the inbox you picked and nothing leaves Mailtrap. Build and test the flow against **Send Sandbox Email**, then swap the step for **Send Transactional Email** when you are ready to reach real recipients. The From address on the Sandbox action does not need a verified domain.&#x20;

<figure><img src="../.gitbook/assets/viaSocket 6.png" alt=""><figcaption></figcaption></figure>

**Important notes**:

* **TEST** is not **SAVE**. Closing a step after a successful test discards the configuration. Click **SAVE** in the step panel before you leave it.
* Mailtrap returns 401 Unauthorized when the From Email domain is not a verified sending domain on your account, even when the token is valid. The response body is only `{"success": false, "errors": ["Unauthorized"]}`. Check the domain before you check the token. Verified domains are listed under **Sending Domains** in Mailtrap.

### Step 4. Create an inbound email address

Inbound Email organises addresses as folders containing inboxes. You need both. There is no dashboard for this yet, so create them through the API.

Create a folder:

```json
curl -X POST https://mailtrap.io/api/inbound/folders \
  -H "Authorization: Bearer your-api-token" \
  -H "Content-Type: application/json" \
  -d '{"name": "your-folder-name"}'
```

Create an inbox inside it, using the folder id from the previous response:

```json
curl -X POST https://mailtrap.io/api/inbound/folders/your-folder-id/inboxes \
  -H "Authorization: Bearer your-api-token" \
  -H "Content-Type: application/json" \
  -d '{"name": "your-inbox-name"}'
```

Replace `your-api-token`, `your-folder-name`, `your-folder-id` and `your-inbox-name` with your own values. The second response contains the inbox id and the hosted address, which looks like **your-inbox-a1b2c3d4@inbound-mailtrap.io**.

Keep the address handy. You will send to it once the receiving flow is published.&#x20;

### Step 5. Trigger a flow when email arrives

Create a new flow. Under **Connected Triggers**, select **New Email Received** from the Mailtrap group. Pick your connection, then choose the folder, then the inbox. One trigger binds to one inbox, so use separate flows for separate inboxes.

<figure><img src="../.gitbook/assets/viaSocket 7.png" alt=""><figcaption></figcaption></figure>

Click **Test**.&#x20;

The trigger returns a sample message so you can build the later steps against real field names. It is a fixture, not a message from your inbox: the real payload appears in the Log only after you publish the flow and send to the address.&#x20;

Here is what happens on a real delivery. Mailtrap's inbound webhook posts a short event notification: the event type, the inbox id, the message id and the sender address.&#x20;

The viaSocket trigger receives that notification, verifies its signature, fetches the full message from the Inbound Email API through the connection you picked, and hands the message to your flow. Your flow never handles the API token and never calls the API to get the message.\
\
What arrives in the flow looks like this:

```json
{
  "body": {
    "id": "your-message-id",
    "inbox_id": 2007,
    "from": "Customer Name <customer@example.com>",
    "to": ["your-inbox@inbound-mailtrap.io"],
    "cc": [],
    "bcc": [],
    "reply_to": null,
    "subject": "Re: your subject line",
    "headers": { "mime-version": "1.0", "return-path": "" },
    "size": 5393,
    "html_size": 285,
    "text_size": 224,
    "received_at": "2026-09-16T15:53:36.088Z",
    "rfc_message_id": "<your-rfc-message-id>",
    "in_reply_to": null,
    "references": [],
    "thread_id": "your-thread-id",
    "attachments": [],
    "raw_message_url": "https://...",
    "raw_message_expires_at": "2026-09-16T16:53:49.445Z",
    "html_body": "<html>...</html>",
    "text_body": "The message text."
  }
}
```

Two things to read off this payload before you build anything on top of it.

1. `text_body` and `html_body` are both present. The trigger hands you the whole message, so you do not need a second call to fetch the content. `html_body` is null for a plain-text message.
2. The message nests under a top-level body key. Your references are `body.subject`, `body.text_body`, `body.from`, and so on. The request also carries a headers key, but it holds viaSocket's own routing headers, not the Mailtrap signature.&#x20;

The signature is checked before the flow runs; see the Technical notes.

{% hint style="info" %}
If the trigger panel shows **New version of this trigger is available**, click **Update**, then **Save**, then publish the flow again. A published flow keeps running the trigger version it was published with until you do.
{% endhint %}

### Step 6. Parse the sender address

`from` arrives as one unparsed string in the form Customer Name \<customer@example.com>. Passing that whole string to a contact search will not match, and repeated non-matches create duplicate records. Extract the address first.

Add a **JS Code** step and bind its input to `body.from`.

<figure><img src="../.gitbook/assets/viaSocket 8.png" alt=""><figcaption></figcaption></figure>

```java
const raw = String(rawFrom || "").trim();
const m = raw.match(/^(.*)<(.+)>$/);
const out = {};
if (m) { out.email = m[2].trim(); out.displayName = m[1].trim(); }
else { out.email = raw; out.displayName = ""; }
return out;
```

The step returns two fields. Later steps reference them as `JS_Code.email` and `JS_Code.displayName`.&#x20;

The fallback branch matters: a bare address with no display name is common from automated senders, and the regular expression does not match it.

### Step 7. Look up the contact and branch

Add your CRM's contact search step and set its search term to `JS_Code.email`.

To reference an earlier step in any field, type the dotted path. A picker appears below the field. Select the matching entry from it. The picker shows the group, the field name and its current value, so you can confirm you are pointing at the right step.

Then add a **Multiple Paths** step to branch on the result.

<figure><img src="../.gitbook/assets/viaSocket 9.png" alt=""><figcaption></figcaption></figure>

**Notes**:

* The condition needs care. In Pipedrive, Search Person returns an array of matches on a hit, and an object containing a message key on a miss.&#x20;
* A condition that tests the result length never fires on a miss, because there is no array to measure. Test for the field that appears on a miss instead.&#x20;
* An error response from the CRM also carries a message key, so a flow that only checks for it will treat every failed lookup as "no match" and try to create the contact. Check status as well if your CRM returns one.
* Put the contact creation step on the not-found path, binding its name to `JS_Code.displayName` and its email to `JS_Code.email`.

### Step 8. Write the message to the CRM

Add a note step to each path. Both take the same content:

```
Inbound reply. Subject: body.subject Message: body.text_body
```

The two paths differ only in which contact they attach to. On the not-found path, bind the contact id to the output of the step that just created it. On the found path, bind it to the first element of the search result.

This binding is the easiest thing in the whole build to get wrong, so check it before you publish. See the Technical notes below.

<figure><img src="../.gitbook/assets/viaSocket 10.png" alt=""><figcaption></figcaption></figure>

### Step 9. Publish and test

Click **Publish**, then send a message to your inbound address.

Open **Log** and inspect each step. Expect the flow to run within seconds of the message arriving. In our runs it was usually under fifteen seconds, and once a little over a minute.&#x20;

<figure><img src="../.gitbook/assets/viaSocket 11.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The trigger does not process mail that arrived before the flow was published. Send a new message after you click **Publish**, not before.
{% endhint %}

<figure><img src="../.gitbook/assets/viaSocket 12.png" alt=""><figcaption></figcaption></figure>

Run the test twice, from two different senders. The first exercises the not-found path, the second exercises the found path. A flow that only ever runs one branch is a flow with an untested half.

### Technical notes

* **A working reference and a hardcoded value look identical in the run log.** If you type a value into a field instead of selecting a reference from the picker, viaSocket stores the literal. It tests green, and the run log shows the correct value because the value really was correct at the time. Every later message then goes to the same place. Verify bindings by opening the step and reading its configuration, not by reading a successful run.
* **A step containing references does not run from TEST alone.** It opens a **Confirm Test** dialog listing each reference with a value box. Skip it and the step returns `{"request": {}}`, which looks like a failed request but means no values were supplied.
* **The log panel renders only the lines currently in view.** Long payloads appear complete when they are not, because scrolling replaces the rendered lines rather than adding to them. Check the line numbers in the gutter for gaps before concluding a field is missing.
* **Mailtrap signs every inbound webhook delivery with HMAC-SHA256** and sends the signature in a mailtrap-signature header. viaSocket verifies that header against the signing secret it received when it registered the webhook, before your flow runs. A delivery that fails verification is dropped and never reaches the flow. The signature itself is not passed into the flow, so there is nothing for your steps to check.
* **Cost.** These flows consume tasks, not premium credits. Our two-flow loop used fewer than thirty of the 10,000 tasks included on the free plan across all of our test runs.
* **Attachments.** The payload carries an attachments array. In the sample, each entry has id, filename, size, `content_type`, `download_url` and `download_url_expires_at`. We have not run a message with a real attachment through the flow, so treat that shape as documented rather than measured, and read `download_url_expires_at` before fetching.
* **Raw MIME.** To read the original message, use `raw_message_url`. That link expires. Read `raw_message_expires_at` rather than assuming it stays valid, and fetch during processing.
* **Parsing the message list yourself.** The list endpoint returns an envelope, not an array: `{ "data": [...], "total_count": 2, "last_id": "..." }`. Read data.
* **Tokens in logs.** The flows in this guide never carry your Mailtrap token; it lives in the connection. If you add an **API Call** step that sends a token in an Authorization header, treat the run log as sensitive and redact it before sharing it.

### Next steps

* [Inbound Email documentation](https://help.mailtrap.io/)
* [Email API/SMTP documentation](https://help.mailtrap.io/)
* [Email Sandbox documentation](https://help.mailtrap.io/)

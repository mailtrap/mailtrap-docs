# Firebase

[Firebase](https://firebase.google.com/) is Google’s open-source mobile and web app development platform that provides a suite of tools and services for building, managing, and scaling web and mobile applications.

In this article, you’ll learn how to install the Mailtrap Firebase Extension, which allows you to send transactional emails from your Firebase project via Mailtrap without building or maintaining your own cloud functions.

**Prerequisites**:

* A [Mailtrap account](https://mailtrap.io/signup) with a [verified sending domain](https://docs.mailtrap.io/email-api-smtp/setup/sending-domain)
* A [Mailtrap API token](https://docs.mailtrap.io/email-api-smtp/setup/api-tokens) from the [API Tokens page](https://mailtrap.io/api-tokens)
* A Firebase project on the Blaze (pay-as-you-go) plan

### Step 1. Install the Firebase extension

To install the Firebase extension, you have two options. Namely:

<details>

<summary>Option 1: Firebase console</summary>

Use the [quick install](https://console.firebase.google.com/project/_/extensions/install?ref=mailtrap/mailtrap-email) or visit the official Firebase Extension Marketplace page and click **Install**.

</details>

<details>

<summary>Option 2: Firebase CLI</summary>

With the [Firebase CLI](https://firebase.google.com/docs/cli) installed, run the following command in your terminal:

```
firebase ext:install mailtrap/mailtrap-email --project=YOUR_PROJECT_ID
```

</details>

### Step 2. Configure Firebase

During installation, you'll be prompted to configure the following parameters:

| `MAILTRAP_API_TOKEN` | Your Mailtrap API token. It will be stored securely in Google Secret Manager. |
| -------------------- | ----------------------------------------------------------------------------- |
| `MAIL_COLLECTION`    | The Firestore collection to watch for new documents. Default: `mail`          |
| `DEFAULT_FROM_EMAIL` | The default sender email address.                                             |
| `DEFAULT_FROM_NAME`  | The default sender name (optional).                                           |

### Step 3. How to trigger an email

To trigger an email, add a document to your configured Firestore collection. The extension will pick it up and send it through Mailtrap automatically. Here are some code snippets you can use:

{% tabs %}
{% tab title="Basic email" %}
```javascript
import { addDoc, collection, getFirestore } from "firebase/firestore";

const db = getFirestore();

await addDoc(collection(db, "mail"), {
  to: [{ email: "recipient@example.com" }],
  subject: "Hello!",
  html: "<p>Welcome to our app!</p>",
});
```
{% endtab %}

{% tab title="CC and BCC" %}
```javascript
await addDoc(collection(db, "mail"), {
  to: [{ email: "recipient@example.com" }],
  cc: [{ email: "cc@example.com" }],
  bcc: [{ email: "bcc@example.com" }],
  subject: "Hello!",
  text: "Welcome to our app!",
});
```
{% endtab %}

{% tab title="Mailtrap template" %}
```javascript
await addDoc(collection(db, "mail"), {
  to: [{ email: "recipient@example.com" }],
  template_uuid: "your-template-uuid",
  template_variables: {
    user_name: "John",
    action_url: "https://example.com/verify",
  },
});
```
{% endtab %}

{% tab title="Attachment" %}
```javascript
await addDoc(collection(db, "mail"), {
  to: [{ email: "recipient@example.com" }],
  subject: "Your invoice",
  text: "Please find your invoice attached.",
  attachments: [
    {
      filename: "invoice.pdf",
      content: "base64-encoded-content-here",
      type: "application/pdf",
    },
  ],
});
```
{% endtab %}
{% endtabs %}

Furthermore, you can create and manage templates directly in the Mailtrap UI without any coding required, and they’ll be accessible to your whole team.

<figure><img src="../.gitbook/assets/Screenshot 2026-03-12 at 13.41.21.png" alt=""><figcaption></figcaption></figure>

### Step 4. Check whether the email has been delivered

#### In Firestore

After the extension processes the document, it automatically updates it with a `delivery` field:

```json
{
  "delivery": {
    "state": "SUCCESS",
    "startTime": "...",
    "endTime": "...",
    "attempts": 1,
    "messageIds": ["abc123-def456"]
  }
}
```

Possible states of the `delivery` field:&#x20;

* `delivery.state` – PENDING, PROCESSING, SUCCESS, ERROR
* `delivery.error` – Error message if failed
* `delivery.messageIds` – Mailtrap message IDs on success

#### In Mailtrap

Go to **Email Logs** in your Mailtrap account to see full delivery details, open and click tracking, and the complete event history for each message.

<div align="left"><figure><img src="../.gitbook/assets/Screenshot 2026-03-12 at 13.44.50.png" alt="" width="563"><figcaption></figcaption></figure></div>

### Configuring Firestore Security Rules

To control who can add documents to your mail collection, you can set up Firestore Security Rules by copying the following code snippet into the **firestore.rules** file or directly in the console under **Firestore Database** → **Rules**:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /${param:MAIL_COLLECTION}/{document} {
      // Only allow authenticated users to create emails
      allow create: if request.auth != null;
      // Only allow the extension to update (for delivery status)
      allow update: if false;
      // Allow users to read their own emails (optional)
      allow read: if request.auth != null;
    }
  }
}
```

### Billing

This extension uses the following Firebase services which may have associated charges:

* Cloud Firestore
* Cloud Functions (2nd gen)
* Secret Manager

This extension also uses Mailtrap's email sending service, which has its own [pricing](https://mailtrap.io/pricing/).

\
\
<br>



<br>




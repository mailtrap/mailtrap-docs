# Base44

Base44 is an AI-powered platform that lets you turn any idea into a fully-functional custom app, without the need for any coding experience. In this guide, you’ll learn how to integrate it with Mailtrap and add email-sending capabilities to your Base44 projects.<br>

**Prerequisites**:&#x20;

* A Base44 account and a project.
* A Mailtrap account for sending emails.

### Step 1. Add your Mailtrap credentials

To insert your Mailtrap credentials, open **App Settings** and activate **Backend Functions**.

<figure><img src="../.gitbook/assets/base 44 1.png" alt=""><figcaption></figcaption></figure>

**Important**: This feature is only available to users subscribed to Base44 _Builder_ plans and higher.

Next, click on the **Secrets** tab, which should show up after you activate **Backend Functions**.&#x20;

<figure><img src="../.gitbook/assets/base44 2.png" alt=""><figcaption></figcaption></figure>

In the **Secrets** tab, as in the screenshot above, add the following two variables:

* `MAILTRAP_API_TOKEN` – The [Mailtrap API token](https://docs.mailtrap.io/email-api-smtp/setup/api-tokens), which you can create at any time in your account.
* `MAILTRAP_FROM_EMAIL` – The email address with the verified Mailtrap sending domain you’ve added after creating an account.

Once you’re done, go back to the dashboard and tell the Base 44 AI you’ve added secrets with the Mailtrap credentials. For this, you can use a prompt such as, for example, this one:

> Please use Mailtrap email api for sending, I've added the required environment variables

### Step 2. Start sending emails

Finally, to test your configuration, trigger an action and send an email from your project. If you followed everything thus far, you should receive the email in your inbox in a few seconds. Here it is in a Gmail inbox I used as my `to` address:

<figure><img src="../.gitbook/assets/base44 3.png" alt=""><figcaption></figcaption></figure>

And here it is in the Mailtrap [Email Logs](https://docs.mailtrap.io/email-api-smtp/analytics/logs).

<figure><img src="../.gitbook/assets/base44 4.png" alt=""><figcaption></figcaption></figure>

**Before you go**: If you plan on collecting email addresses for a list, you can connect your Base44 project with [Mailtrap Contacts](https://docs.mailtrap.io/email-marketing/contacts/overview) and store your addresses in the Mailtrap dashboard automatically. For reference, check out the official [Mailtrap Contacts API documentation](https://docs.mailtrap.io/developers/email-marketing/overview).

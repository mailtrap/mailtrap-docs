---
title: Email Sandbox
description: Learn how to inspect and debug emails with Mailtrap Email Sandbox
---

# Email Sandbox

Learn how to inspect and debug emails with sandbox functionality.

**What you can do:**
1. Catch testing emails from staging.
2. Preview and analyze content for spam.
3. Validate HTML/CSS before sending emails.

## Good to know

* Your emails won't reach your users as you use our Sandbox SMTP.
* You don't need to verify a domain to use sandbox.

## Overview

### Step 1: Navigate to Email Sandbox

Go to [your first Sandbox](https://mailtrap.io/inboxes) by clicking Sandboxes, then My Sandbox. 

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68b16cd14a14f74312312f04/file-qMNm0UX5sm.png)

**Tip:** By default, we created an sandbox for you and called it "My Sandbox". The Edit button on the far right allows you to rename either a project or an sandbox.

Once inside “My Sandbox”, copy the credentials from the "Integration" tab to your clipboard.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68b16d7c0d5a6676085238a4/file-p8axQ7xFyA.png)

Or, use one of the pre-made code snippets for major programming languages and frameworks:

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68b16df44a14f74312312f0a/file-T3tSYwnf3r.png)

### Step 2: Send your first test email

After sending the first test email, you can immediately find it in your Mailtrap sandbox.

<figure><img src="../.gitbook/assets/getting-started-test-email-received.png" alt="Test email displayed in Mailtrap sandbox inbox"><figcaption><p>Test email in sandbox inbox</p></figcaption></figure>

Click on the email, and proceed to inspect and debug it by selecting the HTML Check tab.

<figure><img src="../.gitbook/assets/getting-started-html-check-results.png" alt="HTML Check tab showing email validation results"><figcaption><p>HTML Check results</p></figcaption></figure>

Lastly, you can automate the QA flow with [API](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/a2041e813d169-email-testing-api) if you need it.

### Bonus: Invite your colleagues

Mailtrap is a collaborative tool. Starting from the [Team Plan](https://mailtrap.io/billing/plans/testing), you can create different sandboxes and projects and share them with your colleagues.

That allows you to organize all testing-related workflows among different people - from user management with different permissions to SSO.

## What else you can do with Email Sandbox

* [Enable email per sandbox feature](../email-sandbox/email-address-per-sandbox.md)
* [HTML or RAW format preview](../email-sandbox/inspect-your-email-template.md)
* [HTML Check](../email-sandbox/html-check.md)
* [Automatic Forwarding](../email-sandbox/automatic-email-forwarding.md) and [Manual Forwarding](../email-sandbox/manual-email-forwarding.md) to view emails in real sandboxes
* [Test Bcc and email headers](../email-sandbox/checking-email-headers-and-bcc.md)

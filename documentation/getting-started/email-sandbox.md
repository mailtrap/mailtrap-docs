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

### Good to know

* Your emails won't reach your users as you use our Sandbox SMTP.
* You don't need to verify a domain to use sandbox.

### Overview

{% @arcade/embed flowId="GOawR3yCP4Qi9CT9nkM6" url="https://app.arcade.software/share/GOawR3yCP4Qi9CT9nkM6" %}

{% stepper %}
{% step %}
**Navigate to Email Sandbox**

Go to [your first Sandbox](https://mailtrap.io/inboxes) by clicking **Sandboxes**, then My **Sandbox**.

{% hint style="info" %}
By default, we created a sandbox for you and called it "My Sandbox". The Edit button on the far right allows you to rename either a project or a sandbox.
{% endhint %}

Once inside My **Sandbox**, copy the credentials from the **Integration** tab to your clipboard.

Or, use one of the pre-made code snippets for major programming languages and frameworks:
{% endstep %}

{% step %}
**Send your first test email**

After sending the first test email, you can immediately find it in your Mailtrap sandbox.

Click on the email, and proceed to inspect and debug it by selecting the HTML Check tab.

Lastly, you can automate the QA flow with [API](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/a2041e813d169-email-testing-api) if you need it.
{% endstep %}

{% step %}
**Bonus: Invite your colleagues**

Mailtrap is a collaborative tool. Starting from the [Team Plan](https://mailtrap.io/billing/plans/testing), you can create different sandboxes and projects and share them with your colleagues.

This allows you to organize all testing-related workflows among different people, from user management with different permissions to SSO.
{% endstep %}
{% endstepper %}

### What else you can do with Email Sandbox

* [Enable email per sandbox feature](../email-sandbox/email-address-per-sandbox.md)
* [HTML or RAW format preview](../email-sandbox/testing/email-template.md)
* [HTML Check](../email-sandbox/testing/email-html.md)
* [Automatic Forwarding](../email-sandbox/automatic-email-forwarding.md) and [Manual Forwarding](../email-sandbox/manual-email-forwarding.md) to view emails in real sandboxes
* [Test Bcc and email headers](../email-sandbox/testing/email-headers-and-bcc.md)

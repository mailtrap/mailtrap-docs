---
title: Email Sandbox - FAQs
description: Frequently asked questions about Mailtrap Email Sandbox
icon: question
---

# FAQs

This page covers frequently asked questions about Mailtrap Email Sandbox. For technical issues and error troubleshooting, see the [Troubleshooting section](troubleshooting.md).

### Integration & Setup

<details>

<summary>How do I integrate Email Sandbox with my application?</summary>

The integration is very simple and takes just a couple of minutes. You can integrate using SMTP credentials or code samples for over 20 frameworks.

See our step-by-step guide: [How to integrate Email Sandbox with your application](how-to-integrate-email-sandbox-with-your-application.md).

</details>

<details>

<summary>Do you need to view Sandbox emails only through its interface?</summary>

No, you don't have to stick to Mailtrap web interface. You can forward every single email to your or a teammate's mailbox.

You can even enable automatic forwarding, and Mailtrap will act as a proxy between your application and your email client. In this case, you won't miss important messages from the QA environment, such as exception notifications.

Learn more:

* [Automatic Email Forwarding](automatic-email-forwarding.md)
* [Manual Email Forwarding](manual-email-forwarding.md)

</details>

### Technical Specifications

<details>

<summary>How does Email Sandbox render emails?</summary>

Sandbox renders emails in the same way browsers do, which means no additional stylesheet or CSS presets are applied by default.

</details>

<details>

<summary>Can Email Sandbox show what emails look like in various email clients?</summary>

Mailtrap is compatible with web email clients and renders HTML as-is, without external CSS styles.

Mailtrap provides HTML checks and demonstrates potential errors that different email clients may experience when rendering an HTML email. You can also get a preview of test emails for different devices - mobile, tablet, desktop.

Learn more: [HTML Check](html-check.md)

You can also forward emails to Outlook, Thunderbird, etc., and use these desktop clients to view them.

</details>

<details>

<summary>What does Sandbox do with the &#x3C;style> tag?</summary>

Sandbox doesn't remove the `<style>` tag from email templates.

</details>

<details>

<summary>What does Sandbox do with the &#x3C;script> tag?</summary>

For enhanced security, Sandbox removes all `<script>` tags from HTML.

</details>

<details>

<summary>Can I use Email Sandbox as a /dev/null SMTP server?</summary>

The main goal of Sandbox is to help you test emails, and /dev/null is not part of it.

Should you need a /dev/null SMTP server, please use the following built-in Python SMTP server:

```bash
python -m smtpd -nc DebuggingServer localhost:2525 > /dev/null
```

</details>

<details>

<summary>What is the email size limit for Sandbox?</summary>

The maximum size of an email including attachments ranges from 5 MB to 25 MB, depending on your subscription plan.

If your message exceeds this limit, you will get the following error: `552 5.3.4 Error: message too big`.

See [Features and Limits](features-and-limits.md#email-size-mb) for complete details.

</details>

<details>

<summary>What is the testing rate limit for the sandbox?</summary>

It's the number of emails you can send to each of your sandboxes every 10 seconds. The rate limit depends on the subscription plan.

For more details, check out the [Features and Limits](features-and-limits.md#rate-limits-per-10-sec) and [Pricing page](https://mailtrap.io/pricing/).

</details>

<details>

<summary>What is the monthly messages limit for Email Sandbox?</summary>

It's the maximum number of emails you can test and get in all your sandboxes per month. The total emails per month limit depends on the subscription plan.

If you reach your monthly limit, you'll receive the SMTP protocol error: "535 5.7.0 Monthly messages limit reached". We also send out notifications for having used 80%, 90%, and 100% of the monthly limit.

To continue testing when you're over the limit, please upgrade your subscription plan. Alternatively, you can wait until the next billing period starts, when the limit is reset.

For more details, check the [Features and Limits](features-and-limits.md#total-test-emails-per-month) and [Pricing page](https://mailtrap.io/pricing/).

</details>

### Pricing

<details>

<summary>How much does Email Sandbox cost?</summary>

Email Sandbox provides a free subscription plan for new users who want to evaluate it.

For larger teams, we offer sets of features within several paid subscription plans, starting from $17/month.

To choose one that best fits your needs, check our pricing plans at [mailtrap.io/pricing](https://mailtrap.io/pricing/?tab=sandbox).

</details>

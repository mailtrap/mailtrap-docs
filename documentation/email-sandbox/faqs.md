---
title: Email Sandbox - FAQs
description: Frequently asked questions about Mailtrap Email Sandbox
icon: exclamation
---

# Email Sandbox - FAQs

## Integration & Setup

{% expand title="How do I integrate Email Sandbox with my application?" %}
The integration is very simple and takes just a couple of minutes. You can integrate using SMTP credentials or code samples for over 20 frameworks.

See our step-by-step guide: [How to integrate Email Sandbox with your application](how-to-integrate-email-sandbox-with-your-application.md).
{% endexpand %}

{% expand title="Do you need to view Sandbox emails only through its interface?" %}
No, you don't have to stick to Mailtrap web interface. You can forward every single email to your or a teammate's mailbox.

You can even enable automatic forwarding, and Mailtrap will act as a proxy between your application and your email client. In this case, you won't miss important messages from the QA environment, such as exception notifications.

Learn more:
- [Automatic Email Forwarding](automatic-email-forwarding.md)
- [Manual Email Forwarding](manual-email-forwarding.md)
{% endexpand %}

## Technical Specifications

{% expand title="How does Email Sandbox render emails?" %}
Sandbox renders emails in the same way browsers do, which means no additional stylesheet or CSS presets are applied by default.
{% endexpand %}

{% expand title="Can Email Sandbox show what emails look like in various email clients?" %}
Mailtrap is compatible with web email clients and renders HTML as-is, without external CSS styles.

Mailtrap provides HTML checks and demonstrates potential errors that different email clients may experience when rendering an HTML email. You can also get a preview of test emails for different devices - mobile, tablet, desktop.

Learn more: [HTML Check](html-check.md)

You can also forward emails to Outlook, Thunderbird, etc., and use these desktop clients to view them.
{% endexpand %}

{% expand title="What does Sandbox do with the <style> tag?" %}
Sandbox doesn't remove the `<style>` tag from email templates.
{% endexpand %}

{% expand title="What does Sandbox do with the <script> tag?" %}
For enhanced security, Sandbox removes all `<script>` tags from HTML.
{% endexpand %}

{% expand title="Can I use Email Sandbox as a /dev/null SMTP server?" %}
The main goal of Sandbox is to help you test emails, and /dev/null is not part of it.

Should you need a /dev/null SMTP server, please use the following built-in Python SMTP server:

```bash
python -m smtpd -nc DebuggingServer localhost:2525 > /dev/null
```
{% endexpand %}

{% expand title="What is the email size limit for Sandbox?" %}
The maximum size of an email including attachments ranges from 5 MB to 25 MB, depending on your subscription plan.

If your message exceeds this limit, you will get the following error: `552 5.3.4 Error: message too big`.

See [Features and Limits](features-and-limits.md#email-size-mb) for complete details.
{% endexpand %}

{% expand title="What is the testing rate limit for the sandbox?" %}
It's the number of emails you can send to each of your sandboxes every 10 seconds. The rate limit depends on the subscription plan.

For more details, check out the [Features and Limits](features-and-limits.md#rate-limits-per-10-sec) and [Pricing page](https://mailtrap.io/pricing/).
{% endexpand %}

{% expand title="What is the monthly messages limit for Email Sandbox?" %}
It's the maximum number of emails you can test and get in all your sandboxes per month. The total emails per month limit depends on the subscription plan.

If you reach your monthly limit, you'll receive the SMTP protocol error: "535 5.7.0 Monthly messages limit reached". We also send out notifications for having used 80%, 90%, and 100% of the monthly limit.

To continue testing when you're over the limit, please upgrade your subscription plan. Alternatively, you can wait until the next billing period starts, when the limit is reset.

For more details, check the [Features and Limits](features-and-limits.md#total-test-emails-per-month) and [Pricing page](https://mailtrap.io/pricing/).
{% endexpand %}

## Pricing

{% expand title="How much does Email Sandbox cost?" %}
Email Sandbox provides a free subscription plan for new users who want to evaluate it.

For larger teams, we offer sets of features within several paid subscription plans, starting from $17/month.

To choose one that best fits your needs, check our pricing plans at [mailtrap.io/pricing](https://mailtrap.io/pricing/?tab=sandbox).
{% endexpand %}

## Troubleshooting

{% expand title="My sandboxes disappeared" %}
Sandboxes that are shared with you are moved to the top right menu. Switch to the shared account by clicking on its name.
{% endexpand %}

{% expand title="I have a problem integrating Sandbox with my app, what should I do?" %}
Visit the [Troubleshooting section](troubleshooting.md) for answers to the most common problems, or contact our support at [support@mailtrap.io](mailto:support@mailtrap.io).
{% endexpand %}

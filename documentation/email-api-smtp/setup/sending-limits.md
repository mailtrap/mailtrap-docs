---
description: >-
  Learn Mailtrap email sending limits: hourly, daily, connection, and email
  size. Understand what happens when limits are reached and how to upgrade.
icon: triangle-exclamation
---

# Sending Limits

When you first sign up for Mailtrap, we limit your throughput to 150 emails an hour. This is a security measure to prevent abusing our system for spam.

You can raise the hourly limit by upgrading to a one of our [paid plans](https://mailtrap.io/pricing/), which starts at 600 or even 800 emails per hour. Later on, our automation will proactively raise your limit if you're nearing it. For an even higher limit, you can submit a request to our support team.

{% hint style="warning" %}
Mailtrap Support team can set hourly limit depending on your needs.

It's a soft limit we are ready to adjust for your depending on your needs and usage.
{% endhint %}

If you try to send more emails than your hourly limit allows, the extra emails will be queued and sent in the next hours.

{% hint style="info" %}
Note: There are no hourly limits for Email Campaigns.
{% endhint %}

## Daily Limits

We have a daily limit of 150 emails/day only for our Free plan, which lets you send up to 4,000 emails per month. Emails sent over this limit will be rejected and won't be sent. There are no daily limits on paid plans.

Need to send more? Upgrade to a paid plan!

## Connection Limits

The maximum number of concurrent SMTP connections **per account** is 10.

If you exceed this limit, you'll get the following error:

```
535 5.7.8 Too many connections per account
```

The maximum number of concurrent SMTP connections **per IP** is 10.

The maximum number of messages per 1 SMTP connection is 100.

{% hint style="success" %}
If those limits are not enough, please let us know by contacting our Support Team. Limits can be adjusted only for paid plans.
{% endhint %}

## Email Size

The maximum allowed size of each email message, including attachments, is 10 MB in all plans by default. In Business and higher plans it's possible to increase size up to 30 MB by contacting our Support team.

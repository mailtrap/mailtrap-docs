---
title: Email API/SMTP - FAQs
description: Frequently asked questions about Mailtrap Email API/SMTP
icon: exclamation
---

This page covers frequently asked questions about Mailtrap Email API/SMTP. For technical issues and error troubleshooting, see the [Troubleshooting section](troubleshooting/).

## Getting Started

{% expand title="What is Mailtrap?" %}
Mailtrap is an email delivery service to send transactional and promotional emails. Popular among developer and product teams for its Email API and SMTP solutions.
{% endexpand %}

{% expand title="How do I integrate Mailtrap with my application?" %}
1. [Sign up](https://mailtrap.io/register/signup/) by creating a free account.
2. Go to Email Sending and select [Sending Domains](https://mailtrap.io/sending/domains).
3. After you've added and verified all the DNS records, wait for the Compliance Check to be completed.
4. Proceed to integrate Mailtrap with your application via SMTP or API.

Learn more:
- [API Integration](api-integration.md)
- [SMTP Integration](smtp-integration.md)
- [Sending Domain Setup](sending-domain-setup.md)

If you have any questions, contact us at [support@mailtrap.io](mailto:support@mailtrap.io).
{% endexpand %}

{% expand title="Can I send emails without my domain?" %}
No, you can't.

To send emails, Mailtrap requires you to add a sending domain, authenticated and verified using the DNS records Mailtrap provides.
{% endexpand %}

{% expand title="Can I send emails on behalf of other domains?" %}
No, you can't.

If you verified mydomain.com, you can send emails only on behalf of your domain.
{% endexpand %}

## Domain Setup

{% expand title="Should I use my domain name with www. ?" %}
No, you should use your domain without it.

Please check our [Sending Domain Setup Guide](sending-domain-setup.md) for detailed instructions on adding and verifying your domain.
{% endexpand %}

{% expand title="When I add a domain to Mailtrap, does that include subdomains?" %}
No, you need to add and verify each subdomain/domain separately.
{% endexpand %}

## Features & Capabilities

{% expand title="Can I receive emails with Mailtrap?" %}
Right now, Mailtrap doesn't provide MX records to catch inbound emails, so they'll bounce.

Another option is to use a real email address in the "reply-to" field if a recipient replies to your email.
{% endexpand %}

{% expand title="Can I send emails to end-users with Mailtrap?" %}
Yes, you can. Mailtrap is an email delivery service to send transactional and promotional emails. Popular among developer and product teams for its Email API and SMTP solutions.
{% endexpand %}

{% expand title="Can I force an encrypted connection?" %}
Yes, you can enforce encrypted connections. Mailtrap SMTP server uses STARTTLS, which works for all SMTP ports. We support only TLS connections because of the POODLE vulnerability (SSLv2 and SSLv3 are disabled).
{% endexpand %}

{% expand title="I would like to whitelist live.smtp.mailtrap.io on my firewall. What is Mailtrap's IP range?" %}
We use AWS with auto-balancing, so our IP ranges are the following: [https://ip-ranges.amazonaws.com/ip-ranges.json](https://ip-ranges.amazonaws.com/ip-ranges.json)
{% endexpand %}

## Billing & Limits

{% expand title="How does Mailtrap billing work?" %}
We bill each email. For example, if an email has 3 recipients - we bill 3 of them. If it has + 3 in CC, we bill 6 together. The same goes for recipients in BCC.
{% endexpand %}

{% expand title="What is the email size limit?" %}
The maximum size of an email with attachments for Mailtrap is 10 MB. Upon request, we can extend the limit in some cases to 30 MB.
{% endexpand %}

{% expand title="What is the monthly message limit for email sending?" %}
It's the maximum number of emails you can send with Mailtrap per month. The total number of emails per month depends on the subscription plan.

If you reach your monthly limit, you'll receive the SMTP protocol error: "535 5.7.0 Monthly messages limit reached". We also send out notifications for having used 80%, 90%, and 100% of the monthly limit.

To continue sending when you're over the limit, please upgrade your subscription plan. Alternatively, you can wait until the next billing period starts, when the limit is reset.

For more details, check the [Sending Limits](sending-limits.md) and [Pricing page](https://mailtrap.io/pricing/?tab=api).
{% endexpand %}

{% expand title="How much does Mailtrap cost?" %}
Mailtrap plans start from $15 for 10,000 emails/month. We offer plans for businesses from $85/month for 100,000 emails, and for enterprises, there are plans from $750/month for 1,500,000 emails.

To choose one that best fits your needs, check out our [pricing plans](https://mailtrap.io/pricing/?tab=api).
{% endexpand %}

## Data & Privacy

{% expand title="Is it possible to export Email logs?" %}
Right now, it's not possible, but there's a workaround.

You can set up [Webhooks](sending-domain-setup.md#optional-webhooks-4hmes) to automatically collect logs. And you can use a tool like Zapier, for example, to create a spreadsheet from your webhooks.
{% endexpand %}

{% expand title="Does Mailtrap comply with the GDPR?" %}
The General Data Protection Regulation (GDPR) came into effect on May 25, 2018. We have implemented appropriate technical and security processes to ensure Mailtrap's full compliance with this regulation.

For more details, refer to our:
- [Privacy Policy](https://mailtrap.io/privacy/)
- [Navigational Information](https://mailtrap.io/navigational-info/)
- [Data Protection Agreement](https://mailtrap.io/dpa/)
{% endexpand %}

{% expand title="Do you have a bug bounty program?" %}
We do not. In case you have found a vulnerability on our website that you are eager to report to us, you are welcome to do so at [support@mailtrap.io](mailto:support@mailtrap.io). All issue reporters will be mentioned on our [changelog page](https://mailtrap.io/changelog/).
{% endexpand %}

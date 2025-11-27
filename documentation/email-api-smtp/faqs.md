---
title: Email API/SMTP - FAQs
description: Frequently asked questions about Mailtrap Email API/SMTP.
icon: question
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# FAQs

This page covers frequently asked questions about Mailtrap Email API/SMTP. For technical issues and error troubleshooting, see the [Troubleshooting section](troubleshooting/).

#### Getting Started

<details>

<summary>What is Mailtrap?</summary>

Mailtrap is an email delivery service to send transactional and promotional emails. Popular among developer and product teams for its Email API and SMTP solutions.

</details>

<details>

<summary>How do I integrate Mailtrap with my application?</summary>

1. [Sign up](https://mailtrap.io/register/signup/) for an account.
2. Go to Email Sending and select [Sending Domains](https://mailtrap.io/sending/domains).
3. After you've added and verified all the DNS records, wait for the Compliance Check to be completed.
4. Proceed to integrate Mailtrap with your application via SMTP or API.

Learn more:

* [API Integration](api-integration.md)
* [SMTP Integration](smtp-integration.md)
* [Sending Domain Setup](sending-domain-setup.md)

If you have any questions, contact us at [support@mailtrap.io](mailto:support@mailtrap.io).

</details>

<details>

<summary>Can I send emails without my domain?</summary>

No, you can't.

To send emails, Mailtrap requires you to add a sending domain, authenticated and verified using the DNS records Mailtrap provides.

</details>

<details>

<summary>Can I send emails on behalf of other domains?</summary>

No, you can't.

If you verified mydomain.com, you can send emails only on behalf of your domain.

</details>

#### Domain Setup

<details>

<summary>Should I use my domain name with www. ?</summary>

No, you should use your domain without it.

Please check our [Sending Domain Setup Guide](sending-domain-setup.md) for detailed instructions on adding and verifying your domain.

</details>

<details>

<summary>When I add a domain to Mailtrap, does that include subdomains?</summary>

No, you need to add and verify each subdomain/domain separately.

</details>

#### Features & Capabilities

<details>

<summary>Can I receive emails with Mailtrap?</summary>

Right now, Mailtrap doesn't provide MX records to catch inbound emails, so they'll bounce.

Another option is to use a real email address in the "reply-to" field if a recipient replies to your email.

</details>

<details>

<summary>Can I send emails to end-users with Mailtrap?</summary>

Yes, you can. Mailtrap is an email delivery service to send transactional and promotional emails. Popular among developer and product teams for its Email API and SMTP solutions.

</details>

<details>

<summary>Can I force an encrypted connection?</summary>

Yes, you can enforce encrypted connections. Mailtrap SMTP server uses STARTTLS, which works for all SMTP ports. We support only TLS connections because of the POODLE vulnerability (SSLv2 and SSLv3 are disabled).

</details>

<details>

<summary>I would like to whitelist live.smtp.mailtrap.io on my firewall. What is Mailtrap's IP range?</summary>

We use AWS with auto-balancing, so our IP ranges are the following: [https://ip-ranges.amazonaws.com/ip-ranges.json](https://ip-ranges.amazonaws.com/ip-ranges.json)

</details>

#### Billing & Limits

<details>

<summary>How does Mailtrap billing work?</summary>

We bill each email. For example, if an email has 3 recipients - we bill 3 of them. If it has + 3 in CC, we bill 6 together. The same goes for recipients in BCC.

</details>

<details>

<summary>What is the email size limit?</summary>

The maximum size of an email with attachments for Mailtrap is 10 MB. Upon request, we can extend the limit in some cases to 30 MB.

</details>

<details>

<summary>What is the monthly message limit for email sending?</summary>

It's the maximum number of emails you can send with Mailtrap per month. The total number of emails per month depends on the subscription plan.

If you reach your monthly limit, you'll receive the SMTP protocol error: "535 5.7.0 Monthly messages limit reached". We also send out notifications for having used 80%, 90%, and 100% of the monthly limit.

To continue sending when you're over the limit, please upgrade your subscription plan. Alternatively, you can wait until the next billing period starts, when the limit is reset.

For more details, check the [Sending Limits](setup/sending-limits.md) and [Pricing page](https://mailtrap.io/pricing/?tab=api).

</details>

<details>

<summary>How much does Mailtrap cost?</summary>

Mailtrap offers flexible pricing plans that scale with your email volume, from starter plans for small projects to enterprise solutions for high-volume senders.

For current pricing and to choose a plan that best fits your needs, visit our [pricing page](https://mailtrap.io/pricing/?tab=api).

</details>

#### Data & Privacy

<details>

<summary>Is it possible to export Email logs?</summary>

Right now, it's not possible, but there's a workaround.

You can set up [Webhooks](webhooks.md) to automatically collect logs. And you can use a tool like [Zapier](https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/integrations/mailtrap-integration-with-zapier), for example, to create a spreadsheet from your webhooks.

</details>

<details>

<summary>Does Mailtrap comply with the GDPR?</summary>

The General Data Protection Regulation (GDPR) came into effect on May 25, 2018. We have implemented appropriate technical and security processes to ensure Mailtrap's full compliance with this regulation.

For more details, refer to our:

* [Privacy Policy](https://mailtrap.io/privacy/)
* [Navigational Information](https://mailtrap.io/navigational-info/)
* [Data Protection Agreement](https://mailtrap.io/dpa/)

</details>

<details>

<summary>Do you have a bug bounty program?</summary>

We do not. In case you have found a vulnerability on our website that you are eager to report to us, you are welcome to do so at [support@mailtrap.io](mailto:support@mailtrap.io). All issue reporters will be mentioned on our [changelog page](https://mailtrap.io/changelog/).

</details>

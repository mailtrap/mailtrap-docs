---
icon: question
---

# FAQ

This page covers frequently asked questions about Mailtrap's products. For technical issues and error troubleshooting, see the [Troubleshooting section](email-api-smtp/troubleshooting/).

### Live Sending

#### Getting started

<details>

<summary>What is Mailtrap?</summary>

Mailtrap is an email delivery service to send transactional and promotional emails. Popular among developer and product teams for its Email API and SMTP solutions.

</details>

<details>

<summary>How do I integrate Mailtrap with my application?</summary>

1. [Sign up](https://mailtrap.io/register/signup/) for an account.
2. Go to Email Sending and select [Sending Domains](https://mailtrap.io/domains).
3. After you've added and verified all the DNS records, wait for the Compliance Check to be completed.
4. Navigate to the [**Sending Setup**](https://mailtrap.io/api-smtp/sending-setup) page and integrate Mailtrap with your application via API, SMTP, or your AI agent.

Learn more:

* [API Integration](email-api-smtp/api-integration.md)
* [SMTP Integration](email-api-smtp/smtp-integration.md)
* [Sending Domain Setup](sending-domain/)

If you have any questions, contact us at [support@mailtrap.io](mailto:support@mailtrap.io).

**Important**: Make sure the address of the account owner is actively monitored. If we detect suspicious sending activity or need to clarify any important account details, we may contact you at this email address to ask additional questions, which helps avoid unnecessary account restrictions.

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

#### Domain setup

<details>

<summary>Should I use my domain name with www. ?</summary>

No, you should use your domain without it.

Please check our [Sending Domain Setup Guide](sending-domain/) for detailed instructions on adding and verifying your domain.

</details>

<details>

<summary>When I add a domain to Mailtrap, does that include subdomains?</summary>

No, you need to add and verify each subdomain/domain separately.

</details>

<details>

<summary>Do I need to verify all domains mentioned in my emails?</summary>

If your emails mention, promote, or link to another domain that belongs to you, your company, or your client, then you need to add that domain to Sending Domains and verify it as well.

This helps us verify that the domains are connected to the same legitimate sender and prevents your emails from being mistaken for phishing. If you cannot add it due to the domains limit in your sending plan, please contact the support team for assistance.

</details>

#### Features & capabilities

<details>

<summary>Can I receive emails with Mailtrap?</summary>

Yes, you can. Mailtrap offers the Inbound Email API, which allows you to create inboxes on demand, receive emails via API or webhooks, and process attachments securely. You can also receive mail at your own domain: verify it in Mailtrap, add the MX record we provide, then create a catch-all inbox that collects every address at that domain.

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

<details>

<summary>Can I send emails via JavaMailSender?</summary>

Yes, Mailtrap works with Spring’s JavaMailSender through SMTP. Simply add `spring-boot-starter-mail` to your project, then copy the SMTP credentials from your sending domain’s Integration tab into the `spring.mail`.

```java
spring.mail.host=live.smtp.mailtrap.io
spring.mail.port=587
spring.mail.username=api
spring.mail.password=YOUR_SMTP_PASSWORD
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
```

</details>

#### Billing & limits

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

For more details, check the [Sending Limits](email-api-smtp/setup/sending-limits.md) and [Pricing page](https://mailtrap.io/pricing/?tab=api).

</details>

<details>

<summary>How much does Mailtrap cost?</summary>

Mailtrap offers flexible pricing plans that scale with your email volume, from starter plans for small projects to enterprise solutions for high-volume senders.

For current pricing and to choose a plan that best fits your needs, visit our [pricing page](https://mailtrap.io/pricing/?tab=api).

</details>

#### Data & privacy

<details>

<summary>Is it possible to export Email logs?</summary>

Yes, you can export Email Logs by going to **Email API/SMTP** → **Email Logs** and clicking on **Export in CSV**. You will then receive a CSV file containing your Email Logs in your inbox.

<figure><img src=".gitbook/assets/Screenshot 2026-09-23 at 11.23.42.png" alt=""><figcaption></figcaption></figure>

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

### Email Sandbox

#### Integration & setup

<details>

<summary>How do I integrate Email Sandbox with my application?</summary>

The integration is very simple and you can complete it in just a couple of minutes using SMTP credentials or code samples for over 20 frameworks.

**See our step-by-step guide**: [How to integrate Email Sandbox with your application](email-sandbox/setup/sandbox-smtp-integration.md).

</details>

<details>

<summary>Do you need to view Sandbox emails only through its interface?</summary>

No, you don't have to stick to Email Sandbox web interface. You can forward every single email to your or a teammate's mailbox.

You can even enable automatic forwarding, and Email Sandbox will act as a proxy between your application and your email client. In this case, you won't miss important messages from the QA environment, such as exception notifications.

**Learn more**:

* [Automatic Email Forwarding](email-sandbox/automatic-email-forwarding.md)
* [Manual Email Forwarding](email-sandbox/manual-email-forwarding.md)

</details>

<details>

<summary>How can I add a sandbox if the button is disabled?</summary>

If the button for adding a sandbox is disabled, you have likely reached the maximum allowed sandboxes you are allowed to have for your pricing plan. To add a new sandbox, either delete an existing one or upgrade your plan.

</details>

#### Technical specifications

<details>

<summary>How does Email Sandbox render emails?</summary>

Sandbox renders emails in the same way browsers do, which means no additional stylesheet or CSS presets are applied by default.

</details>

<details>

<summary>Can Email Sandbox show what emails look like in various email clients?</summary>

Email Sandbox is compatible with web email clients and renders HTML as-is, without external CSS styles.

Sandbox provides [HTML checks](email-sandbox/testing/email-html.md) and demonstrates potential errors that different email clients may experience when rendering an HTML email. You can also get a preview of test emails for different devices (e.g., mobile, tablet, desktop).

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

The main goal of Sandbox is to help you test emails, and `/dev/null` is not a part of it.

Should you need a `/dev/null` SMTP server, please use the following built-in Python SMTP server:

```bash
python -m smtpd -nc DebuggingServer localhost:2525 > /dev/null
```

</details>

<details>

<summary>What is the email size limit for Sandbox?</summary>

The maximum size of an email including attachments ranges from 5 MB to 25 MB, depending on your subscription plan.

If your message exceeds this limit, you will get the following error: `552 5.3.4 Error: message too big`.

For complete details, see [Features and Limits](email-sandbox/features-and-limits.md#email-size-mb).

</details>

<details>

<summary>What is the testing rate limit for the sandbox?</summary>

It's the number of emails you can send to each of your sandboxes every 10 seconds. The rate limit depends on the subscription plan.

For more details, check out the [Features and Limits](email-sandbox/features-and-limits.md#rate-limits-per-10-sec) article and our [pricing page](https://mailtrap.io/pricing/).

</details>

<details>

<summary>What is the monthly messages limit for Email Sandbox?</summary>

It's the maximum number of emails you can test and get in all your sandboxes per month. The total emails per month limit depends on the subscription plan.

If you reach your monthly limit, you'll receive the SMTP protocol error: `535 5.7.0 Monthly messages limit reached`. We also send out notifications for having used 80%, 90%, and 100% of the monthly limit.

To continue testing when you're over the limit, please upgrade your subscription plan. Alternatively, you can wait until the next billing period starts, when the limit is reset.

For more details, check out the [Features and Limits](email-sandbox/features-and-limits.md#total-test-emails-per-month) article or our [pricing page](https://mailtrap.io/pricing/).

</details>

#### Pricing

<details>

<summary>How much does Email Sandbox cost?</summary>

Email Sandbox provides a free subscription plan for new users who want to evaluate it.

For larger teams, we offer sets of features within several paid subscription plans, starting from $17/month.

To choose one that best fits your needs, check our [pricing plans](https://mailtrap.io/pricing/?tab=sandbox).

</details>

### Email Marketing

#### General questions

<details>

<summary>What is Mailtrap Email Marketing?</summary>

Mailtrap Email Marketing is a complete solution for creating, sending, and tracking email campaigns. It includes a drag-and-drop editor, contact management, automation tools, and detailed analytics.

</details>

<details>

<summary>How is Email Marketing different from Email API/SMTP?</summary>

Email Marketing is designed for bulk promotional emails with built-in campaign tools, while Email API/SMTP is for transactional emails like password resets. Email Marketing includes visual editors, contact management, and campaign analytics.

</details>

#### Campaign creation

<details>

<summary>Do I need coding skills to create campaigns?</summary>

No! Our drag-and-drop editor requires no coding. However, we also offer an HTML editor for those who prefer to code their emails.

</details>

<details>

<summary>Can I use my own HTML templates?</summary>

Yes, you can import your own HTML templates or create them from scratch using our HTML editor. Templates can be saved and reused across campaigns.

</details>

<details>

<summary>How do I personalize emails?</summary>

Use merge tags in your content:

```
Hi {{first_name}},

Thank you for being a {{customer_type}} customer for {{years_active}} years!
```

These will be replaced with actual contact data when sent.

</details>

#### Contact management

<details>

<summary>How do I import contacts?</summary>

You can import contacts via:

1. **CSV Upload**: Upload a CSV file with contact data
2. **Copy/Paste**: Paste contact list directly
3. **API**: Import programmatically
4. **Integrations**: Sync from CRM or e-commerce platforms using our Zapier, Make.com, n8n integrations.

</details>

<details>

<summary>Can I export my contacts?</summary>

Yes, you can export contacts anytime as CSV including all custom fields and engagement data. This ensures data portability and GDPR compliance.

</details>

<details>

<summary>What happens to unsubscribed contacts?</summary>

Unsubscribed contacts:

* Remain in your account for record-keeping
* Cannot receive campaigns
* Count toward your plan limits

</details>

#### Sending & delivery

<details>

<summary>Why do I need to verify my domain?</summary>

Domain verification:

* Proves you own the domain
* Improves deliverability
* Required for sending campaigns
* Enables DKIM and SPF authentication
* Reduces spam classification

</details>

<details>

<summary>What are typical open rates?</summary>

Industry averages:

* B2B: 21-23%
* E-commerce: 15-18%
* Non-profit: 25-28%
* Media: 20-22%

Your rates depend on list quality, content relevance, and sending practices.

</details>

<details>

<summary>How can I improve deliverability?</summary>

Best practices:

1. Verify your domain properly
2. Use double opt-in
3. Clean your list regularly
4. Maintain consistent sending
5. Avoid spam trigger words
6. Include unsubscribe links
7. Monitor engagement metrics

Check our [Deliverability Guide](https://mailtrap.io/email-deliverability-guide/) for more info.

</details>

<details>

<summary>Can I send to purchased lists?</summary>

No. Sending to purchased lists:

* Violates our Terms of Service
* Results in high bounce/spam rates
* Can lead to account suspension
* Damages sender reputation

Only send to contacts who explicitly opted in.

</details>

#### Analytics & Reporting

<details>

<summary>When will I see campaign statistics?</summary>

* **Delivery stats**: Within 5 minutes
* **Opens**: Real-time as they happen
* **Clicks**: Real-time tracking
* **Unsubscribes**: Immediate
* **Full report**: 24-48 hours for completion

</details>

<details>

<summary>How is open rate tracked?</summary>

Open tracking works via a tiny, invisible image (pixel) in the email. When the image loads, we record an open. Note that:

* Some clients block images (undercounts opens)
* Privacy features may affect accuracy

</details>

#### Compliance & legal

<details>

<summary>Is Mailtrap GDPR compliant?</summary>

Yes, we are fully GDPR compliant:

* Data processing agreements available
* Data portability features
* Right to deletion support

</details>

<details>

<summary>What's required in email footers?</summary>

Legal requirements:

* Physical mailing address
* Unsubscribe link
* Company identification
* Clear sender information

We automatically add these if missing.

</details>

<details>

<summary>How are unsubscribes handled?</summary>

Unsubscribe process:

1. One-click unsubscribe link in every email
2. Immediate processing (within seconds)
3. Confirmation page shown
4. Contact moved to suppression list

</details>

#### Billing & account

<details>

<summary>Can I change plans anytime?</summary>

Yes, you can:

* Upgrade instantly
* Downgrade at end of billing cycle
* Switch between monthly/annual
* Cancel anytime
* No long-term contracts required

</details>

<details>

<summary>Do unused emails roll over?</summary>

No, monthly email quotas don't roll over. However:

* Additional emails counted as overage
* Upgrade anytime for more capacity

</details>

{% hint style="info" %}
Haven't found what you're looking for? Feel free to ask over at [Mailtrap Community](https://community.mailtrap.io/). We're happy to help!
{% endhint %}

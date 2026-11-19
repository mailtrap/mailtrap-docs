---
title: Before you start sending
description: 7 things to get right before you start sending with Mailtrap
---

# Before you start sending

These recommendations will help you avoid some of the most common setup mistakes, protect your sender reputation and build a healthier sending setup from day one.

### 1. Test your email flow in Email Sandbox first

Before sending to real recipients, connect your development and staging environments to **Email Sandbox**.

Sandbox captures your emails in a safe testing environment instead of delivering them to real inboxes. This lets you test templates, links, variables, headers, and complete email workflows without generating unnecessary bounces or affecting your production sending statistics.

This is especially important if you're using placeholder or automatically generated recipient addresses during development. Testing with production credentials can result in emails being sent to invalid addresses and generating real bounces.

This is one of the most common onboarding mistakes we see: users start testing with production credentials instead of Sandbox, resulting in avoidable bounces.

**Learn more:** [Email Sandbox overview](../email-sandbox/overview.md)

### 2. Keep your API and SMTP credentials secure

Treat your Mailtrap credentials the same way you would treat a password.

Never commit API tokens, SMTP credentials, or .env files containing them to public repositories. Don't expose credentials in client-side code or publicly accessible configuration files.

Store secrets securely in environment variables or your preferred secrets-management solution. If you suspect that credentials have been exposed, rotate them immediately.

**Learn more:** [Mailtrap API documentation](https://docs.mailtrap.io/developers)

### 3. Keep your sending domain aligned with your business

Whenever possible, send from your company's primary domain or a related subdomain. Keeping a consistent domain identity helps you build domain reputation over time and makes your sending easier for recipients and mailbox providers to recognize.

Using a dedicated subdomain, such as notifications.example.com or marketing.example.com, is also a good option and can help separate the reputation of different types of email.

If your sending domain is **not obviously connected to your company's website or brand**, make sure this relationship is clear when completing Mailtrap's compliance check. Providing this information from the start helps us verify that the domain is legitimately associated with your business and can prevent additional verification requests later.

### 4. Protect forms that trigger emails

Does your website send an email when someone submits a registration, contact, password-reset, or another public form?

Make sure those forms are protected against automated abuse.

Bots can repeatedly submit public forms using invalid or random email addresses. If every submission triggers an email, this can quickly generate a large number of bounces and negatively affect your sending statistics and reputation.

Consider implementing **CAPTCHA or another bot-protection mechanism**, along with appropriate validation and rate limiting.

**Learn more:** [How to diagnose and prevent email deliverability issues](https://mailtrap.io/blog/email-deliverability-issues/)

### 5. Send emails only to recipients who expect them

A healthy sender reputation starts with the people you're sending to.

Make sure recipients have provided appropriate consent to receive your emails. Avoid purchased, scraped, or third-party lists, and don't use Mailtrap for unsolicited cold outreach.

For subscription-based communication, consider using confirmed or double opt-in. It helps verify that an address is valid and that the person behind it actually intended to subscribe.

This is worth checking before importing your first list rather than after a campaign has already been sent. A permission-based recipient list is an important part of healthy email sending. Unsolicited emails are more likely to generate bounces and spam complaints, which can negatively affect your sender reputation and future deliverability.

**Learn more:** [Email Deliverability Guide](https://mailtrap.io/blog/email-deliverability/)

### 6. Keep your recipient list clean

Your list changes over time. Addresses become invalid, people unsubscribe, and some recipients may no longer want your emails.

Make sure your application handles these signals rather than continuing to send to the same addresses.

In particular, monitor bounces and remove permanently invalid addresses from your own contact database. Repeatedly sending to addresses that hard bounce can hurt your sending reputation.

Mailtrap also maintains **Suppression Lists** to prevent sending to recipients who shouldn't receive additional emails. Suppressions can result from events such as bounces and unsubscribes.

Think of the Suppression List as a safety mechanism, not a replacement for maintaining a clean recipient database on your side.

**Learn more:** [Suppressions List](../general/suppressions-list/)

### 7. Choose the right stream for your emails

Mailtrap offers different options depending on what you're sending.

If you're sending **application-generated emails** through SMTP or API, use **Email Live Sending**. Within Email Live Sending, choose the **Transactional Stream** for messages triggered by a user's action or an application event, such as password resets, verification emails, receipts, and account notifications. Use the **Bulk Stream** for marketing and promotional communication, such as newsletters, product announcements and promotions.

If you're planning to create and manage marketing campaigns directly in Mailtrap, check out **Email Marketing**, which provides tools for managing contacts and building and sending campaigns without implementing the entire campaign flow through SMTP or API.

**Learn more:** [Email Live Sending](../email-api-smtp/overview.md) · [Email Marketing](../email-marketing/overview.md)

### One last thing: stay in touch

If we notice something that requires your attention or could affect your sending, our team may reach out with additional recommendations.

Make sure you have access to the **account owner email address** and keep an eye on **in-app notifications** so you don't miss important updates from Mailtrap.

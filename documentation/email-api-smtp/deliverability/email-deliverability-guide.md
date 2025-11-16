---
title: Email Deliverability Guide
description: >-
  Complete guide to achieving optimal email deliverability with best practices
  and technical recommendations
---

# 📚 Email Deliverability Guide

{% hint style="info" %}
👋 New to Mailtrap? Check our 5 minute 🎥 [overview of our Email API/SMTP](https://railsware.wistia.com/medias/n037p9z9ac).
{% endhint %}

## Highlights: The Golden Rules of Email Deliverability

### Send Expected Content at Expected Times

* Only send emails recipients explicitly signed up for
* Maintain consistent sending schedules
* Match content to subscriber expectations

### Less is More

* Focus on engaged subscribers
* Remove inactive subscribers
* **Prioritize email list quality over email list size**

### No Cold Outreach

* Avoid cold email campaigns, as they are considered SPAM
* Follow Mailtrap's [guidelines](https://mailtrap.io/terms/), which prohibit cold outreach
* Only send to verified opted-in subscribers

### Protect All Web Forms

* Implement CAPTCHA on every form
* Prevent bot-generated sign-ups
* Validate web form entries

{% hint style="success" %}
Following these key guidelines will help you prevent common deliverability issues. For in-depth guidance, explore the rest of this guide.
{% endhint %}

## Foundation: Technical Setup

### Domain Authentication

Configure your domain properly for optimal deliverability:

* **SPF and DMARC Records**: Configure correctly, ensuring no conflicting entries (with Mailtrap, this is already covered)
* **A and MX Records**: Set up proper records for your domain (via Cloudflare, Google Workspace, or other services)
* **Subdomain Strategy**: Consider using separate subdomains for different email types:
  * `email.yourdomain.com` for marketing
  * `notifications.yourdomain.com` for transactional
* **Google Postmaster Tools**: Verify domain ownership for enhanced deliverability monitoring

{% hint style="info" %}
**Pro Tip**: Provide view access to your Google Postmaster Tools dashboard to Mailtrap's support team for additional deliverability monitoring (applies to Business and higher plans).
{% endhint %}

### Form Security

Protect all forms to prevent bot sign-ups:

#### Implement CAPTCHA on All Forms

* Newsletter subscription forms
* User registration forms
* Contact forms
* Password reset forms

#### Trusted CAPTCHA Solutions

* [Google reCAPTCHA](https://www.google.com/recaptcha/about/)
* [hCAPTCHA](https://www.hcaptcha.com/)
* [Cloudflare Turnstile](https://www.cloudflare.com/products/turnstile/)

#### Additional Security Measures

* Implement honeypot fields (invisible fields designed to trap bots)
* Add timing checks (block submissions completed in under 1 second)
* Limit requests by IP address

## Email List Management

### List Cleaning

Remove problematic addresses:

* **Role-based emails**: admin@, info@, sales@, support@
* **Disposable email domains**
* **Misspelled domains**: example@gmal.com
* **Invalid email addresses**

### Email Validation Services

Use these services before sending campaigns:

* [ZeroBounce](https://zerobounce.net/)
* [Bouncer](https://www.usebouncer.com/)
* Similar alternatives

### Sunset Policy

Implement a systematic approach to inactive subscribers:

1. Define inactivity thresholds (e.g., no opens for 6 months)
2. Send re-engagement campaigns
3. Remove consistently inactive subscribers

## Sender Identity Shaping

### Engaging Sender Addresses

Instead of generic addresses, use personalized ones:

* ✅ `newsletter@company.com`
* ✅ `updates@company.com`
* ✅ `team@company.com`
* ❌ `no-reply@company.com` (avoid if possible)

### Professional "From" Names

Format your sender names appropriately:

* ✅ "John from Company" [john@company.com](mailto:john@company.com)
* ✅ "Company Newsletter" [newsletter@company.com](mailto:newsletter@company.com)
* ❌ "DO NOT REPLY" [no-reply@company.com](mailto:no-reply@company.com)

### Reply Address Management

* Set up auto-responses for marketing emails
* Route subscriber replies to support team
* Track reply engagement for deliverability metrics

## Content Creation

### Message Structure

#### Subject Line

* Include company name for recognition
* Keep under 50 characters
* Use formats like: "Your Company: November Product Updates"
* Avoid spam triggers: "AMAZING OFFER!!! DON'T MISS OUT!!!"

#### Pre-header Text

* Length: 40-130 characters
* Complement the subject line
* Example: "See what's new in our latest release, including highly-requested features"

#### Email Copy

* Keep paragraphs short and scannable
* Focus on one key message per email (if possible)
* Include clear and compelling CTAs
* Avoid spam trigger words and excessive punctuation
* Optimize for mobile readability

## Email Sending

### Gradual Scaling

Build your sending reputation carefully:

{% stepper %}
{% step %}
#### Start Small

Begin with 200 emails per day
{% endstep %}

{% step %}
#### Target Engaged Users

Focus on subscribers who interacted in the last 30 days
{% endstep %}

{% step %}
#### Gradual Increase

Increase volume by 25-30% every few days
{% endstep %}

{% step %}
#### Monitor Metrics

Ensure bounce rates stay below 2%
{% endstep %}
{% endstepper %}

{% hint style="info" %}
**Note:** If you have questions, the Mailtrap deliverability team is ready to help. Assistance is included in the Business and higher plans.
{% endhint %}

### Engagement-Based Communication

#### Segment Your Lists by Engagement

| Segment              | Definition                     | Action                 |
| -------------------- | ------------------------------ | ---------------------- |
| **Highly Engaged**   | Opened/clicked in last 30 days | Send regularly         |
| **Somewhat Engaged** | Opened/clicked in last 90 days | Send less frequently   |
| **At Risk**          | No activity in 90-180 days     | Re-engagement campaign |
| **Inactive**         | No activity in 180+ days       | Consider removing      |

{% hint style="warning" %}
**Tip**: Avoid sending any communication to the Inactive segment if your case allows it.
{% endhint %}

#### Implement Double Opt-In

* Follow up with immediate confirmation email
* Include clear confirmation instructions
* Set expiration timeframe for confirmation links (24-48 hours)

#### Enable Easy Unsubscribing

* Include one-click unsubscribe in every email
* Link to preference center for frequency adjustment
* Provide clear unsubscribe confirmation

## Prohibited Practices

{% hint style="danger" %}
**Maintain good standing with Mailtrap by avoiding:**

* Cold outreach campaigns
* Purchased or rented email lists
* Deceptive subject lines or content
* Attempts to bypass spam filters through content manipulation
{% endhint %}

## Monitoring and Audits

### Google Postmaster Tools Setup

1. Visit [Google Postmaster Tools](https://postmaster.google.com/)
2. Add and verify your domain
3. Monitor key metrics:
   * Spam rate
   * Domain reputation
   * IP reputation
   * Delivery errors
   * Authentication results

### Key Metrics to Monitor

| Metric              | Target        | Action if Exceeded         |
| ------------------- | ------------- | -------------------------- |
| **Bounce Rate**     | < 5%          | Clean your list            |
| **Spam Complaints** | < 0.1%        | Review content & frequency |
| **Open Rate**       | 15-25% (bulk) | Improve subject lines      |
| **Click Rate**      | 2.5% (bulk)   | Enhance content relevance  |

### Regular Audits

* Verify SPF, DKIM, and DMARC settings
* Test email formatting across clients/devices
* Ensure compliance with [Google sender guidelines](https://support.google.com/a/answer/81126?hl=en)
* Check CAN-SPAM, GDPR compliance

{% hint style="success" %}
**Remember:** View email deliverability as an ongoing process that requires regular attention and adjustment. Keep testing, monitoring, and optimizing based on your metrics and recipient engagement.
{% endhint %}

## Useful Mailtrap Information

### Migration Guides

* [How To Migrate To Mailtrap](https://mailtrap.io/mailtrap-migration-guide/)
* [Mailtrap vs SendGrid](https://mailtrap.io/mailtrap-sendgrid-alternative/)
* [Mailtrap vs Mailgun](https://mailtrap.io/mailtrap-mailgun-alternative/)
* [Mailtrap vs Mailchimp Transactional](https://mailtrap.io/mailtrap-mandrill-alternative/)
* [Mailtrap vs Amazon SES](https://mailtrap.io/mailtrap-amazon-ses-alternative/)
* [Mailtrap vs HubSpot Transactional](https://mailtrap.io/hubspot-transactional-emails-alternative/)

## Additional Resources

### Official Guidelines

* [Gmail Bulk Sender Guidelines](https://support.google.com/mail/answer/81126)
* [Email Authentication Documentation](https://support.google.com/a/answer/33786)
* [Google Postmaster Tools Documentation](https://support.google.com/mail/answer/6227174)

### Security Solutions

* [reCAPTCHA Documentation](https://developers.google.com/recaptcha)
* [hCAPTCHA Documentation](https://docs.hcaptcha.com/)
* [Cloudflare Turnstile Documentation](https://developers.cloudflare.com/turnstile)

### Email Setup Guides

* [Google Workspace Email Setup](https://support.google.com/a/topic/2683828)
* [Cloudflare Email Setup](https://developers.cloudflare.com/email-routing/get-started)

## Related Documentation

* [Sending Domain Setup](../sending-domain-setup.md)
* [IP Warmup](../ip-warmup.md)
* [Suppressions List](../suppressions-list.md)
* [Bounce Categorization](../bounce-categorization.md)
* [Feedback Loops](../feedback-loops.md)

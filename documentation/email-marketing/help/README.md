---
title: Help & Support
description: Get help with Email Marketing issues and find answers to common questions
---

# Help & Support

Find answers to common questions and troubleshoot issues with Email Marketing. Get help with campaign creation, contact management, analytics, and more.

### Campaign Creation Issues

#### Domain not verified

**Problem**: Can't send campaigns without verified domain **Solution**:

1. Go to Sending Domains
2. Add your domain
3. Add DNS records to your provider
4. Wait for verification (usually < 1 hour)
5. Check verification status

#### Template not saving

**Problem**: Changes to email template lost **Solution**:

* Click "Save" before navigating away
* Check for HTML validation errors
* Ensure template size < 100KB
* Clear browser cache if persistent

#### Images not displaying

**Problem**: Images broken in preview/sent emails **Solution**:

* Use absolute URLs for images
* Host images on reliable CDN
* Check image file size (< 1MB recommended)
* Verify image format (JPG, PNG, GIF)

### Contact Management Issues

#### Import failures

**Problem**: CSV import not working **Solution**:

```csv
email,first_name,last_name,custom_field
john@example.com,John,Doe,Value1
jane@example.com,Jane,Smith,Value2
```

* Use UTF-8 encoding
* Include email header
* Remove special characters
* Check for duplicate emails

#### Contacts not receiving emails

**Possible causes**:

1. **Suppressed**: Check suppression list
2. **Bounced**: Review bounce status
3. **Unsubscribed**: Verify subscription status
4. **Invalid email**: Check email format
5. **Segment exclusion**: Review segment criteria

### Delivery Issues

#### Low open rates

**Troubleshooting checklist**:

* ✓ Subject line optimization
* ✓ Sender name recognition
* ✓ Send time optimization
* ✓ List quality check
* ✓ Spam score review

#### High bounce rate

**Common causes & fixes**:

| Bounce Type | Cause         | Solution         |
| ----------- | ------------- | ---------------- |
| Hard bounce | Invalid email | Remove from list |
| Soft bounce | Mailbox full  | Retry later      |
| Block       | Spam filters  | Improve content  |
| Technical   | Server issue  | Contact support  |

#### Spam complaints

**Prevention strategies**:

* Use double opt-in
* Clear unsubscribe link
* Relevant content only
* Consistent sending frequency
* Honor preferences immediately

## Getting Help

### Self-Service Options

1. **Documentation Search**: Use search bar above
2. **Video Tutorials**: [YouTube Channel](https://www.youtube.com/@mailtrap-official)
3. **Blog Resources**: [mailtrap.io/blog](https://mailtrap.io/blog)
4. **API Reference**: [API Docs](https://api-docs.mailtrap.io)

### <i class="fa-comments-question-check">:comments-question-check:</i>Contact Support

If you can’t find the answer you need in our documentation and would like to contact support and speak with an agent, we’re here to help.

You can get in touch with the Mailtrap Support team using one of the following ways:

* **From your Mailtrap account**&#x20;

1. Log in to your account [here](https://mailtrap.io/signin).
2. Go to the <i class="fa-circle-question">:circle-question:</i>[<mark style="color:$primary;">**Help Center**</mark>](https://mailtrap.io/help-center) > <i class="fa-message-dots">:message-dots:</i> Get Help
3. Click <mark style="color:$primary;">**Start conversation.**</mark>&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2026-02-19 at 17.12.57.png" alt=""><figcaption></figcaption></figure>

* **Email us at** 📧 support@mailtrap.io

Whether you need technical assistance, help troubleshooting an issue, or simply want to talk to customer support, our team will be happy to assist you.

## Quick Solutions

### Campaign Issues

#### Schedule campaign not sending

```javascript
// Check schedule settings
{
  "scheduled_for": "2024-01-15T10:00:00Z",
  "timezone": "America/New_York",
  "status": "scheduled"
}
```

* Verify time zone settings
* Check for past dates
* Confirm campaign approved
* Review sending limits

#### A/B test not working

Requirements for A/B testing:

* Minimum 1,000 recipients
* Test percentage 10-50%
* Single variable change
* Sufficient test duration

### Analytics Problems

#### Stats not updating

* **Wait time**: Allow 5-10 minutes
* **Cache**: Clear browser cache
* **Filters**: Check date range
* **Timezone**: Verify settings

#### Click tracking not working

```html
<!-- Ensure links are properly formatted -->
<a href="https://example.com/page">Click here</a>

<!-- Not tracked -->
<a href="javascript:void(0)">Click</a>
<a href="mailto:email@example.com">Email</a>
```

## Best Practices

### Campaign Optimization

* **Subject Lines**: 30-50 characters
* **Preview Text**: 35-90 characters
* **Send Time**: Tuesday-Thursday, 10 AM
* **Frequency**: 1-4 emails/month
* **Segmentation**: Target < 1000 per segment

### List Management

* Regular list cleaning (quarterly)
* Re-engagement campaigns
* Sunset policy for inactives
* Double opt-in for new subscribers
* Preference center implementation

### Content Guidelines

* Mobile-first design
* Clear CTA above fold
* Alt text for images
* Plain text version
* Accessibility compliance

## Debugging Tools

### Email Testing Checklist

```markdown
- [ ] Preview in major clients
- [ ] Test all links
- [ ] Verify personalization
- [ ] Check spam score
- [ ] Test on mobile devices
- [ ] Verify unsubscribe link
- [ ] Review footer compliance
- [ ] Test dynamic content
```

### Campaign Diagnostics

```sql
-- Check campaign performance
SELECT
  sent_count,
  delivered_count,
  open_count,
  click_count,
  bounce_count,
  unsubscribe_count
FROM campaigns
WHERE campaign_id = 'YOUR_CAMPAIGN_ID';
```

## Feedback & suggestions

_We welcome technical feedback and contributions that help us improve Mailtrap’s functionality and documentation. Please use the appropriate channel depending on the type of request._

#### <i class="fa-bug">:bug:</i>Bug Reports

**If you encounter a product issue or unexpected behavior, please** [#contact-support](./#contact-support "mention")**.**

To help us investigate efficiently, include:

* A detailed description of the issue
* Exact reproduction steps
* Relevant stream, domain, sandbox, or account details
* Timestamps (including timezone)
* Screenshots or logs if available

#### <i class="fa-file-circle-plus">:file-circle-plus:</i>Feature Requests

For product improvements or new feature proposals, use our [Public Roadmap](https://mailtrap.featurebase.app/en) portal.

There you can:

* **Submit a new feature request**

<div align="left"><figure><img src="../../.gitbook/assets/Screenshot 2026-03-02 at 10.32.03.png" alt="" width="375"><figcaption></figcaption></figure></div>

* **Upvote existing requests**

<div align="left"><figure><img src="../../.gitbook/assets/Screenshot 2026-03-02 at 10.33.40.png" alt="" width="375"><figcaption></figcaption></figure></div>

* **Subscribe to updates for specific requests**

<div align="left"><figure><img src="../../.gitbook/assets/Screenshot 2026-03-02 at 10.33.11.png" alt="" width="375"><figcaption></figcaption></figure></div>

:white\_check\_mark:**Recent improvements and major feature updates include:**

* Drag & drop editor v2
* Campaign templates library
* Real-time analytics
* Multi-language support
* GDPR compliance tools

:soon:**The following enhancements are currently planned or in progress:**

* Advanced automation workflows
* Enhanced personalization
* SMS marketing integration
* AI content suggestions
* Advanced segmentation

You can follow updates and release progress directly in Featurebase.

#### <i class="fa-file-doc">:file-doc:</i>Documentation Improvements

If you identify unclear, incomplete, or outdated documentation:

1. Use the **feedback widget** located on the right-hand side of the page to rate the article:\
   ![](<../../.gitbook/assets/Screenshot 2026-03-02 at 10.30.47.png>)
2. **Provide specific feedback** describing what should be corrected, clarified, or expanded\
   ![](<../../.gitbook/assets/Screenshot 2026-03-02 at 10.31.22.png>)

This helps us continuously refine our docs.

#### <i class="fa-square-code">:square-code:</i>GitHub & Technical Collaboration

For open-source projects, SDKs, or public repositories, join us on [GitHub](https://github.com/mailtrap).

## Training Resources

### Getting Started

* [Quick Start Guide](../copy-of-email-marketing.md)
* [Video Walkthrough](https://www.youtube.com/watch?v=example)
* [Best Practices Guide](https://mailtrap.io/blog/email-marketing-best-practices/)

### Advanced Topics

* [Segmentation Strategies](broken-reference/)
* [Automation Workflows](../automations.md)
* [Analytics Deep Dive](broken-reference/)
* [Template Optimization](../email-templates.md)

### Webinars & Training

* Monthly product webinars
* On-demand training videos
* Custom training (Enterprise)
* Certification program

## System Status

### Check Service Status

* **Status Page**: [status.mailtrap.io](https://status.mailtrap.io)
* **Planned Maintenance**: Announced 48 hours ahead
* **API Status**: Separate monitoring
* **Subscribe**: Get status updates via email

### Performance Metrics

* Email delivery: 99.9% uptime
* API availability: 99.95% uptime
* Average send time: < 2 seconds
* Support response: < 24 hours

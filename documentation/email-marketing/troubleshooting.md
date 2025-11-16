---
title: Email Marketing Troubleshooting
description: Solutions to common Email Marketing issues
---

# 🔧 Troubleshooting

Step-by-step solutions to common Email Marketing issues. Find fixes for campaign problems, delivery issues, and technical errors.

## Campaign Issues

### Campaign Won't Send

#### Symptoms

* Send button disabled or grayed out
* Campaign stuck in "Draft" status
* Error messages when attempting to send

#### Solutions

**1. Verify Domain**

```
✓ Go to Sending Domains
✓ Check verification status
✓ Add DNS records if pending
✓ Wait for propagation (up to 48 hours)
```

**2. Check Recipients**

* Ensure at least one valid recipient
* Verify contacts are not suppressed
* Check segment has members
* Review list selection

**3. Complete Required Fields**

* Subject line filled in
* From email address set
* Content added to template
* Company footer information complete

**4. Review Account Status**

* Check sending limits not exceeded
* Verify billing is current
* Ensure account not suspended
* Confirm email credits available

### Template Not Saving

#### Problem

Changes to email template are lost

#### Fix Steps

1. **Check Template Size**
   * Keep under 100KB total
   * Optimize images (use URLs, not embedded)
   * Minimize inline CSS
2.  **Validate HTML**

    ```html
    <!-- Ensure proper structure -->
    <!DOCTYPE html>
    <html>
    <head>
      <meta charset="UTF-8">
    </head>
    <body>
      <!-- Content here -->
    </body>
    </html>
    ```
3. **Clear Browser Cache**
   * Hard refresh: Ctrl+F5 (Windows) or Cmd+Shift+R (Mac)
   * Try incognito/private mode
   * Test in different browser
4. **Check for Conflicts**
   * Disable browser extensions
   * Check for JavaScript errors (F12 console)
   * Ensure stable internet connection

### Images Not Displaying

#### Common Causes & Fixes

| Issue                 | Solution                        |
| --------------------- | ------------------------------- |
| Broken URLs           | Use absolute URLs (https://...) |
| Large files           | Compress images < 1MB           |
| Wrong format          | Use JPG, PNG, or GIF            |
| HTTP instead of HTTPS | Always use HTTPS URLs           |
| Hotlinking blocked    | Host on your own server/CDN     |

#### Best Practice

```html
<!-- Good -->
<img src="https://cdn.example.com/image.jpg"
     alt="Description"
     width="600"
     style="max-width:100%;">

<!-- Bad -->
<img src="/images/image.jpg">
<img src="http://example.com/image.jpg">
```

## Delivery Problems

### Emails Going to Spam

#### Diagnostic Checklist

* [ ] Domain properly authenticated (SPF, DKIM, DMARC)
* [ ] No spam trigger words in subject/content
* [ ] Proper text-to-image ratio
* [ ] Unsubscribe link present and working
* [ ] From address matches authenticated domain
* [ ] Sending to engaged subscribers only

#### Solutions

**1. Improve Authentication**

```dns
; SPF Record
v=spf1 include:mailtrap.io ~all

; DKIM Record
mailtrap._domainkey IN TXT "v=DKIM1; k=rsa; p=..."

; DMARC Record
_dmarc IN TXT "v=DMARC1; p=quarantine; rua=mailto:..."
```

**2. Content Optimization**

* Avoid: FREE, WINNER, URGENT, \$$$
* Maintain 60/40 text-to-image ratio
* Include alt text for images
* Use proper HTML structure
* Test with spam checkers

**3. List Hygiene**

* Remove inactive subscribers (6+ months)
* Use double opt-in
* Honor unsubscribes immediately
* Suppress hard bounces
* Monitor engagement rates

### High Bounce Rate

#### Types of Bounces

**Hard Bounces** (Remove immediately)

* Invalid email addresses
* Non-existent domains
* Blocked recipients

**Soft Bounces** (Retry 2-3 times)

* Mailbox full
* Server temporarily unavailable
* Message too large

#### Reduction Strategies

1.  **Email Validation**

    ```javascript
    // Basic validation
    function validateEmail(email) {
      const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return re.test(email);
    }
    ```
2. **List Cleaning Process**
   * Run through email verification service
   * Remove role-based emails (info@, admin@)
   * Check for typos (gmial.com → gmail.com)
   * Remove duplicates
3. **Import Best Practices**
   * Verify CSV format
   * Check for hidden characters
   * Ensure proper encoding (UTF-8)
   * Map fields correctly

### Low Open Rates

#### Benchmark Comparison

| Industry   | Average Open Rate |
| ---------- | ----------------- |
| B2B        | 21-23%            |
| Retail     | 18-20%            |
| Non-profit | 25-28%            |
| Technology | 20-22%            |

#### Improvement Tactics

**Subject Line Optimization**

* Keep under 50 characters
* Personalize with {first\_name}
* Create urgency without spam words
* A/B test variations
* Use emojis sparingly

**Timing Optimization**

```
Best times to send:
- Tuesday-Thursday
- 10 AM or 2 PM recipient time
- Avoid Mondays and Fridays
- Test your specific audience
```

**Sender Reputation**

* Use consistent "From" name
* Authenticate sending domain
* Maintain low complaint rate
* Regular sending schedule
* Warm up new IPs/domains

## Contact Management Issues

### Import Failures

#### Error: "Invalid CSV Format"

**Solution:**

```csv
email,first_name,last_name,company
john@example.com,John,Doe,ACME Corp
jane@example.com,Jane,Smith,XYZ Inc
```

* First row must be headers
* Use comma separation
* No special characters in headers
* Save as UTF-8 encoding

#### Error: "Duplicate Emails"

**Solution:**

1. Export existing contacts
2. Remove duplicates in spreadsheet
3. Use VLOOKUP or remove duplicates function
4. Re-import cleaned list

#### Error: "Invalid Email Addresses"

**Common Issues:**

* Missing @ symbol
* Spaces in email
* Invalid characters
* Missing domain extension

**Bulk Cleaning Script:**

```python
import re

def clean_email_list(emails):
    cleaned = []
    pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'

    for email in emails:
        email = email.strip().lower()
        if re.match(pattern, email):
            cleaned.append(email)

    return cleaned
```

### Contacts Not Receiving

#### Investigation Steps

1. **Check Contact Status**
   * View contact details
   * Check subscription status
   * Review suppression lists
   * Verify email validity
2. **Review Campaign Targeting**
   * Confirm segment criteria
   * Check include/exclude lists
   * Verify campaign audience
3. **Check Delivery Logs**
   * Search for specific email
   * Review bounce messages
   * Check spam complaints
   * Verify delivery attempts

## Analytics Issues

### Stats Not Updating

#### Troubleshooting

1. **Wait for Processing**
   * Initial stats: 5-10 minutes
   * Full report: 24-48 hours
   * Real-time for opens/clicks
2. **Check Filters**
   * Date range selection
   * Campaign selection
   * Segment filters
3. **Browser Issues**
   * Clear cache
   * Disable ad blockers
   * Try different browser
   * Check JavaScript enabled

### Click Tracking Not Working

#### Requirements

* Links must be absolute URLs
* HTTP/HTTPS protocols only
* No JavaScript links
* No mailto: links

#### Valid Link Examples

```html
<!-- Tracked -->
<a href="https://example.com">Click here</a>
<a href="http://example.com/page">Learn more</a>

<!-- Not tracked -->
<a href="javascript:void(0)">Click</a>
<a href="mailto:info@example.com">Email us</a>
<a href="#section">Anchor link</a>
```

## Automation Issues

### Automation Not Triggering

#### Checklist

* [ ] Automation is activated
* [ ] Trigger conditions met
* [ ] Contacts match criteria
* [ ] No time delays preventing execution
* [ ] Daily limits not exceeded

#### Common Fixes

1. **Check Trigger Settings**
   * Verify event configuration
   * Test with single contact
   * Review condition logic
2. **Validate Contact Data**
   * Required fields present
   * Data types correct
   * No conflicting suppressions
3. **Review Timing**
   * Time zone settings
   * Delay configurations
   * Schedule restrictions

## API & Integration Issues

### API Error Codes

| Code | Meaning      | Solution                 |
| ---- | ------------ | ------------------------ |
| 400  | Bad Request  | Check request format     |
| 401  | Unauthorized | Verify API token         |
| 403  | Forbidden    | Check permissions        |
| 404  | Not Found    | Verify endpoint URL      |
| 429  | Rate Limited | Implement backoff        |
| 500  | Server Error | Retry or contact support |

### Integration Problems

#### Webhook Failures

```javascript
// Webhook endpoint example
app.post('/webhook', (req, res) => {
  // Verify webhook signature
  const signature = req.headers['x-mailtrap-signature'];
  if (!verifySignature(signature, req.body)) {
    return res.status(401).send('Invalid signature');
  }

  // Process webhook
  try {
    processWebhook(req.body);
    res.status(200).send('OK');
  } catch (error) {
    console.error(error);
    res.status(500).send('Processing error');
  }
});
```

## Getting Additional Help

### Before Contacting Support

1. Document the issue
   * Error messages (exact text)
   * Steps to reproduce
   * Screenshots if applicable
   * Time and date of occurrence
2. Check Resources
   * [FAQs](faqs.md)
   * [Help Documentation](help/)
   * [Status Page](https://status.mailtrap.io)
3. Gather Information
   * Account email
   * Campaign/Contact IDs
   * Browser/OS details
   * API request/response logs

### Contact Support

* **Email**: support@mailtrap.io
* **Response Time**: 24-48 hours
* **Priority Support**: Business/Enterprise plans
* **Include**: Clear description, reproduction steps, expected vs. actual behavior

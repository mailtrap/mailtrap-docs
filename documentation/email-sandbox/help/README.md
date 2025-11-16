---
title: Help & Support
description: Get help with Email Sandbox issues and find answers to common questions
---

# ❓ Help & Support

Find answers to common questions and troubleshoot issues with Email Sandbox. Our comprehensive help resources are designed to get you back on track quickly.

## Resources

### [Frequently Asked Questions](../faqs.md)

Browse our comprehensive FAQ section for quick answers to common questions about Email Sandbox setup, integration, testing features, and best practices.

### [Troubleshooting Guide](../troubleshooting.md)

Step-by-step solutions for common issues including connection problems, email capture issues, and configuration errors.

## Common Issues & Solutions

### Connection Issues

#### Can't connect to Sandbox SMTP

1. **Verify credentials**: Check username and password
2. **Confirm port**: Use 2525, 25, 587, or 465
3. **Check firewall**: Ensure ports aren't blocked
4. **Test connection**: Use telnet or nc command

```bash
telnet sandbox.smtp.mailtrap.io 2525
```

#### Emails not appearing in Sandbox

1. **Check sandbox limits**: Free plan has 500 emails/month
2. **Verify credentials**: Ensure using correct sandbox
3. **Check spam folder**: Some emails may be filtered
4. **Review email size**: Maximum 5MB including attachments
5. **API rate limits**: Check if hitting rate limits

### Configuration Problems

#### Framework integration not working

* **Laravel**: Clear config cache with `php artisan config:clear`
* **Rails**: Restart server after config changes
* **Django**: Check `EMAIL_BACKEND` setting
* **Node.js**: Verify environment variables loaded

#### Authentication failures

```
535 5.7.0 Invalid login or password
```

Solution:

* Copy credentials directly from Mailtrap dashboard
* Don't use email address as username
* Regenerate credentials if needed

### Testing Issues

#### HTML not rendering correctly

* Use HTML Check tool to validate code
* Test with different email clients
* Check for missing closing tags
* Validate CSS compatibility

#### Attachments not working

* Verify file size < 5MB total
* Check MIME type configuration
* Ensure proper encoding (base64)
* Test with different file types

## Getting Help

### Self-Service Resources

1. **Search Documentation**: Use the search bar above
2. **Check FAQs**: [Frequently Asked Questions](../faqs.md)
3. **Review Troubleshooting**: [Common issues](../troubleshooting.md)
4. **API Reference**: [API Documentation](https://api-docs.mailtrap.io/)

### Contact Support

If you can't find the answer you need:

* **Email**: support@mailtrap.io
* **Help Center**: [help.mailtrap.io](https://help.mailtrap.io)
* **Status Page**: [status.mailtrap.io](https://status.mailtrap.io)

### Before Contacting Support

Please have the following information ready:

* Account email address
* Sandbox ID or name
* Error messages (exact wording)
* Steps to reproduce the issue
* Framework/language you're using
* Code snippets (if applicable)

## Quick Solutions

### Email Capture Issues

| Problem            | Solution                             |
| ------------------ | ------------------------------------ |
| No emails received | Check credentials and connection     |
| Emails delayed     | Normal processing time is < 1 second |
| Missing emails     | Check inbox limits and filters       |
| Partial content    | Verify email size < 5MB              |

### API Issues

| Error Code | Meaning      | Solution                 |
| ---------- | ------------ | ------------------------ |
| 401        | Unauthorized | Check API token          |
| 403        | Forbidden    | Verify permissions       |
| 404        | Not found    | Check inbox ID           |
| 429        | Rate limited | Implement backoff        |
| 500        | Server error | Retry or contact support |

### SMTP Errors

| Error                 | Cause               | Fix                               |
| --------------------- | ------------------- | --------------------------------- |
| Connection refused    | Wrong port/host     | Use sandbox.smtp.mailtrap.io:2525 |
| Authentication failed | Invalid credentials | Copy from dashboard               |
| Message rejected      | Size limit exceeded | Keep under 5MB                    |
| Timeout               | Network issue       | Check firewall/proxy              |

## Debugging Tools

### Connection Testing

```bash
# Test SMTP connection
openssl s_client -connect sandbox.smtp.mailtrap.io:2525 -starttls smtp

# Test with curl
curl -v telnet://sandbox.smtp.mailtrap.io:2525
```

### Email Testing

```python
# Python test script
import smtplib
from email.mime.text import MIMEText

def test_sandbox():
    msg = MIMEText('Test email body')
    msg['Subject'] = 'Test Subject'
    msg['From'] = 'test@example.com'
    msg['To'] = 'recipient@example.com'

    with smtplib.SMTP('sandbox.smtp.mailtrap.io', 2525) as server:
        server.login('YOUR_USERNAME', 'YOUR_PASSWORD')
        server.send_message(msg)
        print("Email sent successfully!")

test_sandbox()
```

## Best Practices

### Optimal Configuration

* Use port 2525 for best compatibility
* Enable STARTTLS for security
* Set reasonable timeout values
* Implement retry logic
* Use connection pooling

### Testing Strategy

* Create separate sandboxes per environment
* Clear sandboxes regularly
* Use descriptive email subjects
* Tag emails with test IDs
* Automate common tests

### Team Collaboration

* Share sandboxes appropriately
* Document sandbox purposes
* Use consistent naming
* Regular permission audits
* Communicate test schedules

## Frequently Requested Features

### Coming Soon

* GraphQL API
* Advanced search filters
* Email templates library
* Browser extension
* Mobile app

### Recently Added

* Dark mode support
* Webhook events
* Email forwarding
* Load testing support
* API v2 endpoints

## Community Resources

### Tutorials & Guides

* [Getting Started Video](https://www.youtube.com/watch?v=example)
* [Blog Tutorials](https://mailtrap.io/blog/tag/sandbox/)
* [Integration Examples](https://github.com/railsware/mailtrap-examples)

### Developer Resources

* [API Client Libraries](https://github.com/railsware)
* [Postman Collection](https://www.postman.com/mailtrap)
* [Code Snippets](https://mailtrap.io/blog/test-emails-in-dev/)

## Feedback & Suggestions

We value your feedback! Help us improve Email Sandbox:

* **Feature Requests**: Send ideas to feedback@mailtrap.io
* **Bug Reports**: Include reproduction steps
* **Documentation**: Suggest improvements
* **Community**: Join discussions on GitHub

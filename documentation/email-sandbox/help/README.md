---
title: Help & Support
description: Get help with Email Sandbox issues and find answers to common questions
---

# Help & Support

Find answers to common questions and troubleshoot issues with Email Sandbox. Our comprehensive help resources are designed to get you back on track quickly.

## Resources

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Frequently Asked Questions</strong></td><td><em>Browse our comprehensive FAQ section for quick answers to common questions about Email Sandbox setup, integration, testing features, and best practices.</em></td><td><a href="../faqs.md">faqs.md</a></td></tr><tr><td><strong>Troubleshooting</strong></td><td><em>Step-by-step solutions for common issues including connection problems, email capture issues, and configuration errors.</em></td><td><a href="../troubleshooting.md">troubleshooting.md</a></td></tr></tbody></table>

## Common issues & solutions

### Connection issues

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

### Configuration problems

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

### Testing issues

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

## Getting help

### Self-service resources

1. **Search documentation**: Use the search bar above
2. **Check FAQs**: [Frequently Asked Questions](../faqs.md)
3. **Review troubleshooting**: [Common issues](../troubleshooting.md)
4. **API reference**: [API Documentation](https://api-docs.mailtrap.io/)

### 💬Contact Support

If you can’t find the answer you need in our documentation and would like to contact support and speak with an agent, we’re here to help.

You can get in touch with the Mailtrap Support team using one of the following ways:

1. **From your Mailtrap account**&#x20;

* Log in to your account [here](https://mailtrap.io/signin).
* Go to the **Help Center >** <a href="https://mailtrap.io/help-center" class="button primary" data-icon="message-dots">Get Help</a>&#x20;
* Click <mark style="color:$primary;">**Start conversation**</mark> <br>

<figure><img src="../../.gitbook/assets/Screenshot 2026-02-19 at 17.12.57.png" alt=""><figcaption></figcaption></figure>



2. **Email us at** 📧 support@mailtrap.io<br>

Whether you need technical assistance, help troubleshooting an issue, or simply want to talk to customer support, our team will be happy to assist you.

### Before contacting support

Please have the following information ready:

* Account email address
* Sandbox ID or name
* Error messages (exact wording)
* Steps to reproduce the issue
* Framework/language you're using
* Code snippets (if applicable)

## Quick solutions

### Email capture issues

| Problem            | Solution                             |
| ------------------ | ------------------------------------ |
| No emails received | Check credentials and connection     |
| Emails delayed     | Normal processing time is < 1 second |
| Missing emails     | Check inbox limits and filters       |
| Partial content    | Verify email size < 5MB              |

### API issues

| Error Code | Meaning      | Solution                 |
| ---------- | ------------ | ------------------------ |
| 401        | Unauthorized | Check API token          |
| 403        | Forbidden    | Verify permissions       |
| 404        | Not found    | Check inbox ID           |
| 429        | Rate limited | Implement backoff        |
| 500        | Server error | Retry or contact support |

### SMTP errors

| Error                 | Cause               | Fix                               |
| --------------------- | ------------------- | --------------------------------- |
| Connection refused    | Wrong port/host     | Use sandbox.smtp.mailtrap.io:2525 |
| Authentication failed | Invalid credentials | Copy from dashboard               |
| Message rejected      | Size limit exceeded | Keep under 5MB                    |
| Timeout               | Network issue       | Check firewall/proxy              |

## Debugging tools

### Connection testing

```bash
# Test SMTP connection
openssl s_client -connect sandbox.smtp.mailtrap.io:2525 -starttls smtp

# Test with curl
curl -v telnet://sandbox.smtp.mailtrap.io:2525
```

### Email testing

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

## Best practices

### Optimal configuration

* Use port 2525 for best compatibility
* Enable STARTTLS for security
* Set reasonable timeout values
* Implement retry logic
* Use connection pooling

### Testing strategy

* Create separate sandboxes per environment
* Clear sandboxes regularly
* Use descriptive email subjects
* Tag emails with test IDs
* Automate common tests

### Team collaboration

* Share sandboxes appropriately
* Document sandbox purposes
* Use consistent naming
* Regular permission audits
* Communicate test schedules

## Frequently requested features

### Coming soon

* GraphQL API
* Advanced search filters
* Email templates library
* Browser extension
* Mobile app

### Recently added

* Dark mode support
* Webhook events
* Email forwarding
* Load testing support
* API v2 endpoints

## Community resources

### Tutorials & guides

* [Getting started video](https://www.youtube.com/watch?v=example)
* [Blog tutorials](https://mailtrap.io/blog/tag/sandbox/)
* [Integration examples](https://github.com/railsware/mailtrap-examples)

### Developer resources

* [API client libraries](https://github.com/railsware)
* [Postman collection](https://www.postman.com/mailtrap)
* [Code snippets](https://mailtrap.io/blog/test-emails-in-dev/)

## Feedback & suggestions

We value your feedback! Help us improve Email Sandbox:

* **Feature requests**: Send ideas to feedback@mailtrap.io
* **Bug reports**: Include reproduction steps
* **Documentation**: Suggest improvements
* **Community**: Join discussions on GitHub

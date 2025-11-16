---
title: Setup & Configuration
description: Get started with Email API/SMTP setup and configuration
---

# Setup & Configuration

Complete guide to setting up and configuring Mailtrap Email API/SMTP for your application. Follow these steps to start sending emails in production.

## Quick Start Checklist

Get up and running with this essential setup checklist:

- [ ] Create your Mailtrap account
- [ ] Verify your sending domain
- [ ] Choose integration method (API or SMTP)
- [ ] Configure authentication
- [ ] Send test email
- [ ] Set up monitoring

## Configuration Steps

### [Sending Domain Setup](../sending-domain-setup.md)
The foundation of email delivery. Verify your domain ownership and configure authentication records (SPF, DKIM, DMARC) for optimal deliverability.

### [API Integration](../api-integration.md)
Modern RESTful API for programmatic email sending. Best for new applications and microservices architecture.

### [SMTP Integration](../smtp-integration.md)
Traditional SMTP protocol for universal compatibility. Works with any email library or legacy system.

### [IP Warmup](../ip-warmup.md)
Gradually build your sending reputation. Essential for high-volume senders and dedicated IPs.

## Choose Your Integration Method

### When to Use API

**Best for:**
- Modern web applications
- Microservices architecture
- Cloud-native applications
- Real-time sending needs
- Advanced analytics requirements

**Advantages:**
- Faster performance
- Better error handling
- Detailed response data
- Webhook support
- Easier debugging

**Example:**
```bash
curl -X POST "https://send.api.mailtrap.io/api/send" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "from": {"email": "hello@example.com"},
    "to": [{"email": "user@example.com"}],
    "subject": "Test Email",
    "text": "This is a test email"
  }'
```

### When to Use SMTP

**Best for:**
- Legacy applications
- Email clients
- CMS platforms
- Standard libraries
- Minimal code changes

**Advantages:**
- Universal compatibility
- No code changes required
- Works with any language
- Familiar protocol
- Easy migration

**Configuration:**
```
Host: live.smtp.mailtrap.io
Port: 587 (or 25, 465, 2525)
Username: YOUR_USERNAME
Password: YOUR_PASSWORD
Encryption: STARTTLS/TLS
```

## Domain Configuration

### 1. Add Your Domain
Navigate to **Sending Domains** and add your domain:
- Enter your domain name (e.g., example.com)
- Choose verification method
- Add provided DNS records

### 2. DNS Records Setup

**SPF Record:**
```dns
Type: TXT
Name: @ (or your domain)
Value: v=spf1 include:mailtrap.io ~all
```

**DKIM Record:**
```dns
Type: TXT
Name: mailtrap._domainkey
Value: v=DKIM1; k=rsa; p=MIGfMA0GCS...
```

**DMARC Record:**
```dns
Type: TXT
Name: _dmarc
Value: v=DMARC1; p=quarantine; rua=mailto:dmarc@yourdomain.com
```

### 3. Verify Configuration
- DNS propagation: 15 minutes to 48 hours
- Check verification status in dashboard
- Use DNS lookup tools to confirm

## Authentication Setup

### API Authentication

**Get Your API Token:**
1. Go to Settings → API Tokens
2. Click "Create Token"
3. Set permissions (send, read, etc.)
4. Copy and secure token

**Using the Token:**
```javascript
// Node.js example
const headers = {
  'Authorization': `Bearer ${process.env.MAILTRAP_API_TOKEN}`,
  'Content-Type': 'application/json'
};
```

### SMTP Authentication

**Get Credentials:**
1. Navigate to SMTP Settings
2. Copy username and password
3. Note the stream (Transactional/Bulk)

**Configure Your Application:**
```python
# Python example
import smtplib

server = smtplib.SMTP('live.smtp.mailtrap.io', 587)
server.starttls()
server.login('username', 'password')
```

## Environment Configuration

### Development Setup
```env
# .env.development
MAILTRAP_HOST=sandbox.smtp.mailtrap.io
MAILTRAP_PORT=2525
MAILTRAP_USERNAME=sandbox_username
MAILTRAP_PASSWORD=sandbox_password
MAILTRAP_FROM=dev@example.com
```

### Production Setup
```env
# .env.production
MAILTRAP_HOST=live.smtp.mailtrap.io
MAILTRAP_PORT=587
MAILTRAP_USERNAME=production_username
MAILTRAP_PASSWORD=production_password
MAILTRAP_FROM=noreply@yourdomain.com
```

## Framework-Specific Setup

### Laravel
```php
// config/mail.php
'mailers' => [
    'smtp' => [
        'transport' => 'smtp',
        'host' => env('MAILTRAP_HOST'),
        'port' => env('MAILTRAP_PORT'),
        'encryption' => 'tls',
        'username' => env('MAILTRAP_USERNAME'),
        'password' => env('MAILTRAP_PASSWORD'),
    ],
],
```

### Node.js (Nodemailer)
```javascript
const nodemailer = require('nodemailer');

const transporter = nodemailer.createTransport({
  host: process.env.MAILTRAP_HOST,
  port: process.env.MAILTRAP_PORT,
  auth: {
    user: process.env.MAILTRAP_USERNAME,
    pass: process.env.MAILTRAP_PASSWORD
  }
});
```

### Django
```python
# settings.py
EMAIL_HOST = os.environ.get('MAILTRAP_HOST')
EMAIL_PORT = os.environ.get('MAILTRAP_PORT')
EMAIL_HOST_USER = os.environ.get('MAILTRAP_USERNAME')
EMAIL_HOST_PASSWORD = os.environ.get('MAILTRAP_PASSWORD')
EMAIL_USE_TLS = True
```

### Ruby on Rails
```ruby
# config/environments/production.rb
config.action_mailer.smtp_settings = {
  address: ENV['MAILTRAP_HOST'],
  port: ENV['MAILTRAP_PORT'],
  user_name: ENV['MAILTRAP_USERNAME'],
  password: ENV['MAILTRAP_PASSWORD'],
  authentication: :plain,
  enable_starttls_auto: true
}
```

## Testing Your Setup

### 1. Send Test Email

**Via API:**
```bash
curl -X POST "https://send.api.mailtrap.io/api/send" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "from": {"email": "test@yourdomain.com"},
    "to": [{"email": "your-email@example.com"}],
    "subject": "Test Email",
    "text": "If you receive this, your setup is working!"
  }'
```

**Via SMTP:**
```python
import smtplib
from email.mime.text import MIMEText

msg = MIMEText('Test email body')
msg['Subject'] = 'Test Email'
msg['From'] = 'test@yourdomain.com'
msg['To'] = 'recipient@example.com'

server = smtplib.SMTP('live.smtp.mailtrap.io', 587)
server.starttls()
server.login('username', 'password')
server.send_message(msg)
server.quit()
```

### 2. Verify Delivery
- Check Email Logs in dashboard
- Verify recipient received email
- Check spam folder if not in inbox
- Review delivery status

### 3. Monitor Performance
- Set up webhooks for events
- Configure alerts for failures
- Monitor delivery rates
- Track engagement metrics

## Troubleshooting Setup

### Common Issues

| Problem | Solution |
|---------|----------|
| Domain verification failed | Check DNS propagation, verify records |
| Authentication error | Regenerate credentials, check for typos |
| Connection timeout | Check firewall, verify port is open |
| Emails not sending | Verify domain, check sending limits |
| Going to spam | Complete domain authentication |

### Debug Checklist
- [ ] DNS records properly configured
- [ ] Domain verification complete
- [ ] Credentials are correct
- [ ] Using correct host/port
- [ ] Firewall allows outbound SMTP
- [ ] API token has send permission
- [ ] Not hitting rate limits

## Security Best Practices

### Credential Management
- Never commit credentials to version control
- Use environment variables
- Rotate credentials regularly
- Use different credentials per environment
- Implement IP restrictions when possible

### API Token Security
```javascript
// Good - Using environment variable
const apiToken = process.env.MAILTRAP_API_TOKEN;

// Bad - Hardcoded token
const apiToken = 'abc123def456...';  // Never do this!
```

### SMTP Security
- Always use TLS/STARTTLS
- Use strong passwords
- Implement rate limiting
- Monitor for unusual activity
- Set up alerts for failures

## Next Steps

1. **[Configure Templates](../email-templates/README.md)** - Set up reusable email templates
2. **[Set Up Analytics](../statistics/README.md)** - Track email performance
3. **[Configure Webhooks](../statuses-and-events.md)** - Real-time event notifications
4. **[Implement Best Practices](../deliverability/README.md)** - Optimize deliverability

## Support Resources

- [API Documentation](https://api-docs.mailtrap.io/)
- [Integration Examples](https://github.com/railsware/mailtrap-examples)
- [Video Tutorials](https://www.youtube.com/mailtrap)
- [Support Center](https://help.mailtrap.io/)
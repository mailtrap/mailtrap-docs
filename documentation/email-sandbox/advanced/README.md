---
title: Advanced Features
description: Reference documentation and advanced capabilities of Email Sandbox
---

# 🚀 Advanced Features

Explore the advanced capabilities and reference documentation for Email Sandbox. This section covers technical specifications, limits, terminology, and advanced features for power users.

## Documentation

### [Features and Limits](../features-and-limits.md)

Comprehensive overview of Email Sandbox capabilities and current limitations. Understand what you can do and plan your testing strategy accordingly.

### [Sandbox Glossary](../sandbox-glossary.md)

Quick reference for Email Sandbox terminology. Definitions of key terms and concepts to help you navigate the documentation and features.

## Advanced Capabilities

### API Automation

Leverage the Sandbox API for advanced testing workflows:

* Programmatic email retrieval
* Automated test validation
* CI/CD pipeline integration
* Bulk operations
* Custom test frameworks

### Performance Testing

Push Email Sandbox to its limits:

* Load testing with thousands of emails
* Concurrent sandbox operations
* Rate limit testing
* Queue management verification
* Scalability testing

### Integration Patterns

Advanced integration scenarios:

* Multi-environment testing
* Parallel test execution
* Webhook automation
* Custom email parsers
* Test data generation

## Technical Specifications

### Email Limits

| Feature            | Free Plan | Paid Plans |
| ------------------ | --------- | ---------- |
| Emails per Sandbox | 500/month | Unlimited  |
| Email Size         | 5MB       | 5MB        |
| Attachments        | Supported | Supported  |
| Retention          | 7 days    | 30+ days   |
| Sandboxes          | 2         | Unlimited  |

### Protocol Support

* **SMTP**: Ports 25, 465, 587, 2525
* **POP3**: Port 1100 (SSL: 9950)
* **API**: RESTful HTTP/HTTPS
* **Webhooks**: HTTP/HTTPS callbacks
* **WebSocket**: Real-time updates

### Authentication Methods

* **SMTP AUTH**: LOGIN, PLAIN, CRAM-MD5
* **API**: Bearer token authentication
* **OAuth**: Coming soon
* **IP Whitelisting**: Enterprise plans

## Advanced Use Cases

### Automated Testing

Build comprehensive test suites:

```javascript
// Example: Automated email testing
const testSuite = {
  async validatePasswordReset(email) {
    // Check subject line
    expect(email.subject).toBe('Password Reset Request');

    // Verify sender
    expect(email.from.email).toBe('noreply@example.com');

    // Check reset link
    const resetLink = extractResetLink(email.html);
    expect(resetLink).toMatch(/^https:\/\/.*\/reset\//);

    // Validate expiry
    const expiry = extractExpiry(email.html);
    expect(expiry).toBeWithinNext(24, 'hours');
  }
};
```

### Multi-Stage Testing

Test complex email workflows:

```python
# Example: Multi-stage workflow testing
def test_onboarding_sequence():
    # Stage 1: Welcome email
    welcome = sandbox.get_latest_email()
    assert welcome.subject == "Welcome to Our Platform"

    # Stage 2: Verification email
    verify_link = extract_verification_link(welcome)
    trigger_verification(verify_link)

    # Stage 3: Confirmation email
    confirmation = sandbox.get_latest_email()
    assert confirmation.subject == "Email Verified Successfully"

    # Stage 4: Onboarding tips
    tips = sandbox.get_emails_by_category("onboarding")
    assert len(tips) == 3  # Expecting 3-part series
```

### Performance Benchmarking

Measure email system performance:

```javascript
// Example: Performance testing
async function benchmarkEmailDelivery() {
  const results = [];

  for (let i = 0; i < 1000; i++) {
    const start = Date.now();
    await sendTestEmail(i);
    const email = await sandbox.waitForEmail(i);
    const duration = Date.now() - start;

    results.push({
      index: i,
      duration: duration,
      size: email.size,
      timestamp: email.received_at
    });
  }

  return analyzePerformance(results);
}
```

## Sandbox Optimization

### Best Practices

* **Sandbox Organization**: Use naming conventions
* **Regular Cleanup**: Delete old test emails
* **Environment Separation**: Dedicated sandboxes per environment
* **Access Management**: Control team permissions
* **Automation First**: Prefer API over manual testing

### Performance Tips

* Use batch operations for multiple emails
* Implement pagination for large result sets
* Cache frequently accessed data
* Use webhooks for real-time updates
* Optimize search queries

### Security Considerations

* Rotate API tokens regularly
* Use environment variables for credentials
* Implement IP restrictions
* Audit access logs
* Sanitize test data

## API Reference

### Key Endpoints

```bash
# Get sandbox messages
GET /api/v1/inboxes/{inbox_id}/messages

# Get specific message
GET /api/v1/inboxes/{inbox_id}/messages/{message_id}

# Delete message
DELETE /api/v1/inboxes/{inbox_id}/messages/{message_id}

# Clear inbox
PATCH /api/v1/inboxes/{inbox_id}/clean

# Get message source
GET /api/v1/inboxes/{inbox_id}/messages/{message_id}/source
```

### Webhook Events

Configure webhooks for real-time notifications:

* `email.received` - New email arrived
* `email.opened` - Email was opened
* `email.clicked` - Link was clicked
* `email.forwarded` - Email was forwarded
* `inbox.cleared` - Sandbox was cleared

## Advanced Configuration

### Custom Headers

Test with custom email headers:

```
X-Test-ID: test-123
X-Environment: staging
X-Feature-Flag: new-ui-enabled
X-User-Segment: beta-testers
```

### Email Variations

Test different email scenarios:

* Plain text vs. HTML
* With/without attachments
* Different character encodings
* Various MIME types
* Multipart messages

### Load Testing Configuration

Optimize for high-volume testing:

```yaml
load_test:
  concurrent_senders: 50
  emails_per_second: 100
  total_emails: 10000
  timeout_seconds: 300
  retry_policy:
    max_retries: 3
    backoff_multiplier: 2
```

## Troubleshooting Advanced Features

### Common Issues

* **Rate Limiting**: Implement exponential backoff
* **Large Attachments**: Stay under 5MB limit
* **API Timeouts**: Use async operations
* **Webhook Failures**: Implement retry logic
* **Search Performance**: Use specific filters

### Debug Tools

* Email source viewer
* Header analyzer
* MIME structure inspector
* Webhook debugger
* API request logger

## Resources

* [API Documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-documentation/branches/api-v1/5vhoj-mailtrap-api)
* [SDK Libraries](https://github.com/railsware/mailtrap-nodejs)
* [Webhook Guide](../sandbox-api-integration.md)
* [Performance Best Practices](../email-app-load-testing.md)
* [Security Guidelines](https://mailtrap.io/security)

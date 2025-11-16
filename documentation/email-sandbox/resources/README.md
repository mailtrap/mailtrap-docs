---
title: Resources
description: Reference materials, limits, and support for Email Sandbox
---

# Resources

Essential reference materials and support resources for Email Sandbox. Find information about features, limitations, terminology, and getting help.

## Reference Materials

### [Features and Limits](../features-and-limits.md)
Comprehensive overview of Email Sandbox capabilities and current limitations. Understand what you can do and plan accordingly.

### [Sandbox Glossary](../sandbox-glossary.md)
Definitions of key terms and concepts used in Email Sandbox. Quick reference for understanding features and documentation.

### [FAQs](../faqs.md)
Frequently asked questions about Email Sandbox. Quick answers to common queries about setup, usage, and troubleshooting.

### [Troubleshooting](../troubleshooting.md)
Step-by-step solutions to common issues. Get back on track quickly when things don't work as expected.

## Quick Reference

### Sandbox Limits
- **Emails per Sandbox**: 500 (Free plan), Unlimited (Paid plans)
- **Email Size**: Up to 5MB including attachments
- **Retention Period**: 7 days (Free), 30+ days (Paid)
- **Sandboxes**: 2 (Free), Unlimited (Paid)
- **Team Members**: 1 (Free), Varies by plan

### Supported Protocols
- **SMTP**: Ports 25, 465, 587, 2525
- **POP3**: Port 1100 (SSL: 9950)
- **API**: RESTful HTTP/HTTPS
- **Webhooks**: HTTP/HTTPS callbacks

### Email Features
- HTML and plain text emails
- Attachments support
- Multipart messages
- Custom headers
- BCC recipients
- Inline images

## Common Use Cases

### Development Testing
- Local development email testing
- Feature branch testing
- Integration testing
- Regression testing
- Performance testing

### QA Validation
- Template verification
- Cross-client testing
- Deliverability checks
- Link validation
- Content review

### Production Monitoring
- Pre-production validation
- Staging environment testing
- Customer communication testing
- Alert email testing
- Newsletter preview

## Getting Help

### Self-Service
1. Check the [FAQs](../faqs.md)
2. Review [Troubleshooting Guide](../troubleshooting.md)
3. Search documentation
4. Check [Status Page](https://status.mailtrap.io)

### Contact Support
- **Email**: support@mailtrap.io
- **Help Center**: [help.mailtrap.io](https://help.mailtrap.io)
- **Documentation**: Current location
- **API Reference**: [API Docs](https://api-docs.mailtrap.io)

### Community Resources
- Blog tutorials and guides
- Video tutorials
- Sample code repositories
- Integration examples
- Best practices articles

## Technical Specifications

### SMTP Configuration
```
Host: sandbox.smtp.mailtrap.io
Ports: 25, 465, 587, 2525
Encryption: TLS/SSL
Authentication: LOGIN, PLAIN, CRAM-MD5
```

### API Endpoints
```
Base URL: https://mailtrap.io/api/v1
Authentication: Bearer Token
Content-Type: application/json
Rate Limit: 100 requests/minute
```

### Webhook Events
- Email received
- Email opened
- Link clicked
- Attachment downloaded
- Email forwarded

## Best Practices Summary

### Testing Strategy
- Use separate sandboxes for different environments
- Implement automated testing
- Regular cleanup of old emails
- Document test scenarios
- Monitor sandbox usage

### Team Collaboration
- Define clear access policies
- Use consistent naming
- Share relevant test cases
- Document known issues
- Regular team sync on testing

### Security & Privacy
- Use test data only
- Avoid production data in sandbox
- Rotate credentials regularly
- Monitor access logs
- Follow data retention policies

## Version History & Updates

Stay informed about Email Sandbox updates:
- Check release notes regularly
- Subscribe to update notifications
- Review API version changes
- Test new features in sandbox
- Provide feedback on improvements
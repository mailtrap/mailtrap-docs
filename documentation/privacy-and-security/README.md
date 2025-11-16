---
title: Security & Privacy
description: >-
  Learn about Mailtrap's security measures, compliance standards, and data
  protection policies
---

# 🔒 Security & Privacy

Mailtrap takes security and privacy seriously. We implement industry-leading security measures to protect your data and ensure compliance with global privacy regulations.

## Security Features

### [Two-Factor Authentication](../account-and-billing/2fa.md)

Enhance account security with two-factor authentication. Protect against unauthorized access even if passwords are compromised.

### [API Tokens](api-tokens.md)

Secure API access with token-based authentication. Manage tokens, set permissions, and rotate credentials regularly.

## Compliance & Certifications

### [GDPR Compliance](gdpr-compliance.md)

Full compliance with General Data Protection Regulation. Learn about your rights and our data processing practices.

### [ISO Certification](iso-certification.md)

ISO 27001 certified information security management system. Industry-standard security controls and processes.

### [Legal Policies](legal-policies.md)

Comprehensive legal documentation including Terms of Service, Privacy Policy, and Data Processing Agreement.

## Security Architecture

### Infrastructure Security

* **Data Centers**: Tier 3+ certified facilities
* **Network Security**: DDoS protection, firewalls
* **Encryption**: TLS 1.3 for data in transit
* **Storage**: AES-256 encryption at rest
* **Monitoring**: 24/7 security monitoring

### Application Security

* **Authentication**: Multi-factor authentication support
* **Authorization**: Role-based access control
* **API Security**: OAuth 2.0 and API tokens
* **Code Security**: Regular security audits
* **Vulnerability Management**: Continuous scanning

## Data Protection

### Data Privacy Principles

* **Minimal Collection**: Only necessary data
* **Purpose Limitation**: Clear usage purposes
* **Data Minimization**: Limited retention
* **Accuracy**: Keep data updated
* **Transparency**: Clear privacy policies

### Your Data Rights

* **Access**: Request your data copy
* **Rectification**: Correct inaccurate data
* **Erasure**: Right to be forgotten
* **Portability**: Export your data
* **Objection**: Opt-out of processing

## Security Best Practices

### Account Security

1. Enable two-factor authentication
2. Use strong, unique passwords
3. Regularly review account activity
4. Manage API tokens carefully
5. Keep contact info updated

### API Security

```javascript
// Best practice: Use environment variables
const apiToken = process.env.MAILTRAP_API_TOKEN;

// Never hardcode tokens
// Bad: const apiToken = "abc123...";

// Rotate tokens regularly
// Use different tokens for different environments
```

### Team Security

* Implement least privilege principle
* Regular access reviews
* Remove ex-employees promptly
* Use SSO where available
* Audit team activities

## Compliance Standards

### Industry Compliance

* **GDPR**: EU data protection
* **CCPA**: California privacy rights
* **CAN-SPAM**: Email marketing rules
* **PIPEDA**: Canadian privacy law
* **LGPD**: Brazilian data protection

### Security Standards

* **ISO 27001**: Information security
* **SOC 2 Type II**: Security controls
* **PCI DSS**: Payment card security
* **NIST Framework**: Cybersecurity
* **OWASP Top 10**: Web security

## Security Features

### Access Control

* Multi-factor authentication (MFA)
* Single Sign-On (SSO)
* IP whitelisting
* Session management
* Password policies

### Data Encryption

* **In Transit**: TLS 1.3 encryption
* **At Rest**: AES-256 encryption
* **Key Management**: HSM-based
* **Certificate Management**: Auto-renewal
* **End-to-End**: Optional E2E encryption

### Monitoring & Auditing

* Real-time threat detection
* Activity logging
* Audit trails
* Anomaly detection
* Incident response

## Incident Response

### Security Incident Process

1. **Detection**: Automated monitoring
2. **Assessment**: Severity evaluation
3. **Containment**: Limit impact
4. **Eradication**: Remove threat
5. **Recovery**: Restore services
6. **Lessons Learned**: Improve defenses

### Notification Policy

* Immediate critical notifications
* 72-hour breach notification
* Transparent communication
* Regular status updates
* Post-incident reports

## Data Residency

### Data Locations

* **Primary**: United States (US-East)
* **EU Region**: Frankfurt, Germany
* **Backups**: Geographically distributed
* **CDN**: Global edge locations
* **Compliance**: Regional requirements

### Data Transfer

* EU-US Privacy Shield
* Standard Contractual Clauses
* Adequate protection measures
* Encrypted transfers
* Audit trails

## Security Resources

### Documentation

* [Security Whitepaper](https://mailtrap.io/security)
* [Privacy Policy](legal-policies.md)
* [Terms of Service](legal-policies.md)
* [DPA Template](legal-policies.md)
* Security FAQ

### Contact Security Team

* **Report Vulnerability**: security@mailtrap.io
* **Security Questions**: support@mailtrap.io
* **Bug Bounty Program**: Available
* **Response Time**: 24 hours
* **PGP Key**: Available on request

## Regular Updates

### Security Improvements

* Monthly security patches
* Quarterly security reviews
* Annual penetration testing
* Continuous monitoring
* Regular training

### Stay Informed

* Security bulletin subscriptions
* Status page updates
* Blog security posts
* Email notifications
* In-app alerts

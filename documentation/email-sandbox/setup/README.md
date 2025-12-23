---
title: Setup & Integration
description: Get Email Sandbox configured and integrated with your application
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Setup & Configuration

Get started with Email Sandbox quickly and easily. This section covers everything you need to integrate Email Sandbox into your development workflow.

## Integration Options

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Application Integration</strong></td><td>Step-by-step guide to integrate Email Sandbox with your application. Learn how to configure SMTP settings, use API endpoints, and route test emails to your sandbox.</td><td><a href="sandbox-smtp-integration.md">sandbox-smtp-integration.md</a></td></tr><tr><td><strong>Sandbox API</strong></td><td>Programmatically manage your sandboxes and emails using our comprehensive API. Automate testing workflows and integrate with your CI/CD pipeline.</td><td><a href="../sandbox-api-integration.md">sandbox-api-integration.md</a></td></tr><tr><td><strong>API Tokens</strong></td><td>Learn how to create, manage, and use API tokens for Email Sandbox.</td><td><a href="api-tokens.md">api-tokens.md</a></td></tr><tr><td><strong>Email Address per Sandbox</strong></td><td>Each sandbox gets a unique email address. Learn how to use sandbox-specific addresses for organizing and isolating test scenarios.</td><td><a href="../email-address-per-sandbox.md">email-address-per-sandbox.md</a></td></tr></tbody></table>

## Quick Start

#### 1. Create Your First Sandbox

* Log in to your Mailtrap account
* Navigate to Email Sandbox
* Click "Create New Sandbox"
* Name your sandbox (e.g., "Development", "Staging", "QA")

#### 2. Get Your Credentials

* SMTP Host: `sandbox.smtp.mailtrap.io`
* SMTP Port: `2525` (or `25`, `465`, `587`)
* Username: Your sandbox username
* Password: Your sandbox password

#### 3. Configure Your Application

```javascript
// Example Node.js configuration
const nodemailer = require('nodemailer');

const transporter = nodemailer.createTransport({
  host: 'sandbox.smtp.mailtrap.io',
  port: 2525,
  auth: {
    user: 'your_username',
    pass: 'your_password'
  }
});
```

#### 4. Send Test Email

```javascript
await transporter.sendMail({
  from: 'test@example.com',
  to: 'user@example.com',
  subject: 'Test Email',
  text: 'This is a test email'
});
```

## Integration Methods

#### SMTP Integration

* Universal compatibility with any SMTP client
* No code changes required
* Perfect for legacy applications
* Supports all major frameworks and languages

#### API Integration

* Full programmatic control
* Retrieve and analyze emails via API
* Automate testing workflows
* Perfect for CI/CD pipelines

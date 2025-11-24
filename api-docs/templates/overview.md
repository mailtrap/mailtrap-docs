---
title: Email Templates Overview
description: Create and manage reusable email templates for consistent branding
icon: file-code
---

# Email Templates Overview

Email Templates allow you to create reusable email designs with dynamic content. Maintain consistent branding, reduce errors, and speed up email creation with centralized template management.

## Benefits of Email Templates

{% columns %}
{% column %}
### Consistent Branding
Ensure all emails follow your brand guidelines with centralized templates.
{% endcolumn %}

{% column %}
### Dynamic Content
Use variables to personalize emails while maintaining consistent structure.
{% endcolumn %}

{% column %}
### Easy Updates
Update templates in one place to apply changes across all emails.
{% endcolumn %}
{% endcolumns %}

## Getting Started

{% stepper %}
{% step %}
### Create a Template

Design your email template with placeholders for dynamic content:

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .header { background: #007bff; color: white; padding: 20px; }
    .content { padding: 20px; font-family: Arial, sans-serif; }
    .button { background: #28a745; color: white; padding: 10px 20px; text-decoration: none; border-radius: 5px; }
  </style>
</head>
<body>
  <div class="header">
    <h1>Welcome, {{user_name}}!</h1>
  </div>
  <div class="content">
    <p>Thank you for joining {{company_name}}.</p>
    <p>Your account is ready. Get started by exploring our features:</p>
    <a href="{{dashboard_url}}" class="button">Go to Dashboard</a>
  </div>
</body>
</html>
```
{% endstep %}

{% step %}
### Save Template via API

Store your template in Mailtrap:

```javascript
const response = await fetch('https://mailtrap.io/api/accounts/{account_id}/templates', {
  method: 'POST',
  headers: {
    'Api-Token': 'YOUR_API_TOKEN',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    name: 'Welcome Email',
    subject: 'Welcome to {{company_name}}, {{user_name}}!',
    html: htmlContent,
    text: textContent,
    category: 'Onboarding'
  })
});

const template = await response.json();
// Returns: { uuid: 'abc-123-def', name: 'Welcome Email', ... }
```
{% endstep %}

{% step %}
### Send Email Using Template

Use the template UUID to send personalized emails:

{% tabs %}
{% tab title="Node.js" %}
```javascript
import { MailtrapClient } from "mailtrap";

const client = new MailtrapClient({
  token: process.env.MAILTRAP_API_KEY
});

await client.send({
  from: { email: "noreply@example.com" },
  to: [{ email: "user@example.com" }],
  template_uuid: 'abc-123-def',
  template_variables: {
    user_name: 'John Doe',
    company_name: 'Acme Corp',
    dashboard_url: 'https://app.example.com/dashboard'
  }
});
```
{% endtab %}

{% tab title="Python" %}
```python
import mailtrap as mt

client = mt.MailtrapClient(token="YOUR_API_KEY")

client.send(mt.Mail(
    sender=mt.Address(email="noreply@example.com"),
    to=[mt.Address(email="user@example.com")],
    template_uuid="abc-123-def",
    template_variables={
        "user_name": "John Doe",
        "company_name": "Acme Corp",
        "dashboard_url": "https://app.example.com/dashboard"
    }
))
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mailtrap\MailtrapClient;
use Mailtrap\Mime\MailtrapEmail;
use Symfony\Component\Mime\Address;

$mailtrap = MailtrapClient::initSendingEmails(
    apiKey: $_ENV['MAILTRAP_API_KEY']
);

$email = (new MailtrapEmail())
    ->from(new Address('noreply@example.com'))
    ->to(new Address('user@example.com'))
    ->templateUuid('abc-123-def')
    ->templateVariables([
        'user_name' => 'John Doe',
        'company_name' => 'Acme Corp',
        'dashboard_url' => 'https://app.example.com/dashboard'
    ]);

$mailtrap->send($email);
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require 'mailtrap'

client = Mailtrap::Client.new(api_key: 'YOUR_API_KEY')

mail = Mailtrap::Mail.from_template(
  from: { email: 'noreply@example.com' },
  to: [{ email: 'user@example.com' }],
  template_uuid: 'abc-123-def',
  template_variables: {
    user_name: 'John Doe',
    company_name: 'Acme Corp',
    dashboard_url: 'https://app.example.com/dashboard'
  }
)

client.send(mail)
```
{% endtab %}
{% endtabs %}
{% endstep %}
{% endstepper %}

## Template Variables

### Basic Variables

Use double curly braces for simple text replacement:

```html
<p>Hello {{first_name}} {{last_name}}!</p>
<p>Your order #{{order_number}} has been confirmed.</p>
```

### Nested Objects

Access nested properties with dot notation:

```html
<p>Shipping to: {{address.street}}, {{address.city}}, {{address.country}}</p>
<p>Total: ${{order.total}}</p>
```

### Conditionals

Show content based on variable values:

```html
{{#if premium_user}}
  <p>Thank you for being a Premium member!</p>
{{else}}
  <p>Upgrade to Premium for exclusive benefits.</p>
{{/if}}
```

### Loops

Iterate over arrays:

```html
<ul>
{{#each items}}
  <li>{{this.name}} - ${{this.price}}</li>
{{/each}}
</ul>
```

## Template Categories

Organize templates by use case:

{% tabs %}
{% tab title="Transactional" %}
**Account & Security**
- Welcome emails
- Password reset
- Email verification
- 2FA codes
- Account updates
{% endtab %}

{% tab title="Notifications" %}
**System & Activity**
- Order confirmations
- Shipping updates
- Payment receipts
- Activity alerts
- System notifications
{% endtab %}

{% tab title="Marketing" %}
**Campaigns & Engagement**
- Newsletters
- Promotions
- Product updates
- Event invitations
- Re-engagement
{% endtab %}

{% tab title="Lifecycle" %}
**User Journey**
- Onboarding series
- Trial expiration
- Renewal reminders
- Win-back campaigns
- Surveys
{% endtab %}
{% endtabs %}

## Template Management

### List All Templates

```javascript
const response = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/templates',
  {
    headers: { 'Api-Token': 'YOUR_API_TOKEN' }
  }
);

const templates = await response.json();
// Returns array of template objects
```

### Update Template

```javascript
await fetch(
  `https://mailtrap.io/api/accounts/{account_id}/templates/${templateId}`,
  {
    method: 'PUT',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      name: 'Updated Welcome Email',
      html: updatedHtml,
      text: updatedText
    })
  }
);
```

### Delete Template

```javascript
await fetch(
  `https://mailtrap.io/api/accounts/{account_id}/templates/${templateId}`,
  {
    method: 'DELETE',
    headers: { 'Api-Token': 'YOUR_API_TOKEN' }
  }
);
```

## Best Practices

### Template Design

{% hint style="success" %}
**Mobile-First**: Design templates that work well on mobile devices (60% of emails are opened on mobile).
{% endhint %}

1. **Single Column Layout**: Best for mobile readability
2. **Large CTAs**: Minimum 44x44 pixels for touch targets
3. **Web Fonts Fallback**: Include system font fallbacks
4. **Alt Text**: Always include for images
5. **Preheader Text**: Optimize preview text

### Variable Naming

Use consistent, descriptive variable names:

```javascript
// Good
template_variables: {
  user_first_name: 'John',
  order_total_amount: 99.99,
  shipping_tracking_number: 'ABC123'
}

// Avoid
template_variables: {
  name: 'John',      // Too generic
  amt: 99.99,        // Unclear abbreviation
  track: 'ABC123'    // Ambiguous
}
```

### Testing Templates

{% hint style="info" %}
Always test templates with different variable values and email clients.
{% endhint %}

```javascript
// Test with various data scenarios
const testCases = [
  { user_name: 'John', items: ['Item1', 'Item2'] },    // Normal case
  { user_name: 'A very long name here', items: [] },   // Edge cases
  { user_name: '', items: null }                        // Missing data
];

for (const testData of testCases) {
  await sendTestEmail(template, testData);
}
```

## Template Examples

### Welcome Email

```html
<div style="max-width: 600px; margin: 0 auto; font-family: Arial, sans-serif;">
  <div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); padding: 40px; text-align: center; color: white;">
    <h1 style="margin: 0;">Welcome to {{company_name}}!</h1>
  </div>

  <div style="padding: 40px; background: #f7f7f7;">
    <h2>Hi {{user_name}},</h2>
    <p>We're thrilled to have you on board! Your account is all set up and ready to go.</p>

    <div style="background: white; padding: 20px; border-radius: 8px; margin: 20px 0;">
      <h3>Get Started:</h3>
      <ol>
        <li>Complete your profile</li>
        <li>Explore our features</li>
        <li>Connect with the community</li>
      </ol>
    </div>

    <div style="text-align: center; margin: 30px 0;">
      <a href="{{activation_url}}" style="display: inline-block; padding: 15px 30px; background: #667eea; color: white; text-decoration: none; border-radius: 5px;">
        Activate Account
      </a>
    </div>

    <p style="color: #666; font-size: 14px;">
      If you have any questions, reply to this email or visit our
      <a href="{{help_url}}">Help Center</a>.
    </p>
  </div>
</div>
```

### Order Confirmation

```html
<div style="max-width: 600px; margin: 0 auto;">
  <h2>Order Confirmed!</h2>
  <p>Hi {{customer_name}}, your order #{{order_number}} has been received.</p>

  <table style="width: 100%; border-collapse: collapse;">
    <thead>
      <tr style="background: #f0f0f0;">
        <th style="padding: 10px; text-align: left;">Item</th>
        <th style="padding: 10px; text-align: right;">Quantity</th>
        <th style="padding: 10px; text-align: right;">Price</th>
      </tr>
    </thead>
    <tbody>
      {{#each items}}
      <tr>
        <td style="padding: 10px; border-bottom: 1px solid #eee;">{{this.name}}</td>
        <td style="padding: 10px; border-bottom: 1px solid #eee; text-align: right;">{{this.quantity}}</td>
        <td style="padding: 10px; border-bottom: 1px solid #eee; text-align: right;">${{this.price}}</td>
      </tr>
      {{/each}}
    </tbody>
    <tfoot>
      <tr>
        <td colspan="2" style="padding: 10px; text-align: right;"><strong>Total:</strong></td>
        <td style="padding: 10px; text-align: right;"><strong>${{order_total}}</strong></td>
      </tr>
    </tfoot>
  </table>

  <div style="margin-top: 30px; padding: 20px; background: #f9f9f9; border-radius: 5px;">
    <h3>Shipping Address:</h3>
    <p>{{shipping_address}}</p>
    <p>Estimated delivery: {{delivery_date}}</p>
  </div>
</div>
```

## Version Control

{% hint style="warning" %}
Always version your templates when making significant changes.
{% endhint %}

```javascript
// Maintain template versions
const templateVersions = {
  'welcome_v1': 'abc-123',  // Original
  'welcome_v2': 'def-456',  // Updated design
  'welcome_v3': 'ghi-789'   // Current version
};

// Gradual rollout
const useNewTemplate = Math.random() < 0.1; // 10% get new version
const templateId = useNewTemplate ?
  templateVersions.welcome_v3 :
  templateVersions.welcome_v2;
```

## Next Steps

{% hint style="success" %}
Start creating powerful, reusable email templates! Check out the API reference below for detailed endpoints and examples.
{% endhint %}
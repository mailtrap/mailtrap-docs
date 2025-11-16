---
title: Email Management
description: Manage and organize emails in your sandbox effectively
---

# 📁 Email Management

Efficiently manage, search, and organize emails within your Email Sandbox. These tools help you maintain a clean testing environment and quickly find the emails you need.

## Management Features

### [Searching Messages](../searching-messages.md)

Powerful search capabilities to find specific emails quickly. Filter by sender, subject, date, content, and custom criteria.

### [Automatic Forwarding](../automatic-email-forwarding.md)

Set up rules to automatically forward emails from your sandbox to real email addresses. Perfect for sharing test results with team members.

### [Manual Forwarding](../manual-email-forwarding.md)

Manually forward individual emails when needed. Share specific test cases or examples with stakeholders.

## Email Organization

### Search & Filter

* **Full-text Search**: Search email content and headers
* **Advanced Filters**: Filter by date, sender, recipient, subject
* **Custom Tags**: Add tags for easy categorization
* **Saved Searches**: Save frequently used search queries

### Email Actions

* **Mark as Read/Unread**: Track reviewed emails
* **Delete**: Remove unwanted test emails
* **Download**: Export emails for offline analysis
* **Forward**: Share with team members

### Bulk Operations

* **Select Multiple**: Act on multiple emails at once
* **Bulk Delete**: Clean up old test emails
* **Bulk Export**: Download multiple emails
* **Bulk Forward**: Share test sets with team

## Workflow Management

### Development Workflow

1. Send test emails to sandbox
2. Search and filter results
3. Analyze specific test cases
4. Forward results to QA team
5. Clean up after testing

### QA Workflow

1. Receive forwarded test emails
2. Validate against requirements
3. Document issues found
4. Share findings with developers
5. Verify fixes in new tests

### Automated Workflows

* Set up auto-forwarding rules
* Configure webhook notifications
* Integrate with issue trackers
* Automate cleanup schedules

## Best Practices

### Email Organization

* Use consistent naming conventions
* Tag emails by test type
* Regular cleanup of old emails
* Archive important test cases
* Document test scenarios

### Search Optimization

* Use specific search terms
* Combine multiple filters
* Save common searches
* Use date ranges effectively
* Search by custom headers

### Forwarding Guidelines

* Forward only necessary emails
* Include context in forwards
* Use auto-forwarding sparingly
* Respect privacy in test data
* Document forwarding rules

## Advanced Features

### API Management

```javascript
// Search emails via API
const emails = await mailtrap.search({
  inbox_id: 'your_inbox_id',
  query: 'subject:Test',
  from: 'test@example.com'
});

// Forward email via API
await mailtrap.forward({
  email_id: 'email_123',
  to: 'qa@yourcompany.com'
});
```

### Automation Rules

* Forward emails matching patterns
* Delete emails older than X days
* Tag emails automatically
* Trigger webhooks on receipt
* Export emails on schedule

### Integration Options

* Connect to Slack for notifications
* Export to JIRA for bug tracking
* Sync with test management tools
* Archive to cloud storage
* Generate test reports

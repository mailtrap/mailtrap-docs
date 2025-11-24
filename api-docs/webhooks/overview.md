---
title: Webhooks API Overview
description: Receive real-time notifications about email events
icon: webhook
---

# Webhooks API Overview

Webhooks allow you to receive real-time notifications about email events directly to your server. Instead of polling for updates, Mailtrap will push event data to your endpoint as soon as events occur.

## How Webhooks Work

{% stepper %}
{% step %}
### Configure Your Endpoint

Set up an HTTPS endpoint on your server that can receive POST requests from Mailtrap.

```javascript
// Example Express.js endpoint
app.post('/webhooks/mailtrap', (req, res) => {
  // Process webhook
  res.status(200).send('OK');
});
```
{% endstep %}

{% step %}
### Add Webhook in Mailtrap

1. Go to [Webhook Settings](https://mailtrap.io/webhooks)
2. Click "Add Webhook"
3. Enter your endpoint URL
4. Select events to receive
5. Choose payload format (JSON or Form Data)
{% endstep %}

{% step %}
### Test Your Webhook

Send a test webhook from Mailtrap to verify your endpoint is working correctly.

{% hint style="info" %}
Always respond with HTTP 200 to acknowledge receipt, even if processing fails.
{% endhint %}
{% endstep %}

{% step %}
### Process Events

Handle different event types based on your business logic:

```javascript
switch(event.type) {
  case 'delivery':
    // Mark email as delivered
    break;
  case 'bounce':
    // Handle bounce
    break;
  case 'open':
    // Track engagement
    break;
}
```
{% endstep %}
{% endstepper %}

## Supported Events

### Email Delivery Events

{% columns %}
{% column %}
**Delivery**
Email successfully delivered to recipient's mailbox.
{% endcolumn %}

{% column %}
**Bounce**
Permanent delivery failure (e.g., invalid email address).
{% endcolumn %}

{% column %}
**Soft Bounce**
Temporary delivery failure (e.g., mailbox full).
{% endcolumn %}
{% endcolumns %}

### Engagement Events

{% columns %}
{% column %}
**Open**
Recipient opened the email.
{% endcolumn %}

{% column %}
**Click**
Recipient clicked a link in the email.
{% endcolumn %}

{% column %}
**Unsubscribe**
Recipient unsubscribed from emails.
{% endcolumn %}
{% endcolumns %}

### Compliance Events

{% columns %}
{% column %}
**Spam Report**
Recipient marked email as spam.
{% endcolumn %}

{% column %}
**Suspension**
Email address added to suppression list.
{% endcolumn %}
{% endcolumns %}

## Webhook Security

{% hint style="warning" %}
Always verify webhook authenticity to prevent unauthorized requests.
{% endhint %}

### Best Practices

1. **Use HTTPS Only**: Always use HTTPS endpoints for security
2. **Verify Signatures**: Check `X-Mailtrap-Signature` header
3. **Whitelist IPs**: Only accept webhooks from Mailtrap IP addresses
4. **Implement Idempotency**: Use `event_id` to prevent duplicate processing
5. **Async Processing**: Process webhooks asynchronously to avoid timeouts
6. **Error Handling**: Implement proper error handling and retries

## Payload Formats

### JSON Format

Most common format for modern applications:

```json
{
  "events": [
    {
      "event": "delivery",
      "timestamp": 1728669700,
      "message_id": "abc-123",
      "email": "recipient@example.com",
      "event_id": "unique-event-id"
    }
  ]
}
```

### Form Data Format

Legacy format for compatibility with older systems:

```
event=delivery&email=recipient@example.com&message_id=abc-123
```

## Event Data

Each event contains:

| Field | Description | Required |
|-------|-------------|----------|
| `event` | Event type (delivery, bounce, etc.) | Yes |
| `timestamp` | Unix timestamp | Yes |
| `message_id` | Original message ID | Yes |
| `email` | Recipient email | Yes |
| `event_id` | Unique event identifier | Yes |
| `category` | Email category | No |
| `custom_variables` | Custom metadata | No |

## Retry Policy

{% hint style="info" %}
Mailtrap will retry failed webhook deliveries with exponential backoff.
{% endhint %}

- **Initial retry**: 1 minute after failure
- **Subsequent retries**: Exponentially increasing intervals
- **Maximum retries**: 10 attempts over 24 hours
- **Success criteria**: HTTP 200 response

## Common Use Cases

### Update Email Status

```python
def handle_webhook(event):
    if event['event'] == 'delivery':
        db.update_email_status(
            message_id=event['message_id'],
            status='delivered',
            delivered_at=event['timestamp']
        )
```

### Manage Suppressions

```python
def handle_bounce(event):
    if event['bounce_category'] == 'badrecipient':
        # Permanently suppress this email
        db.add_to_suppression_list(
            email=event['email'],
            reason='hard_bounce'
        )
```

### Track Engagement

```python
def handle_engagement(event):
    if event['event'] in ['open', 'click']:
        analytics.track(
            user=event['email'],
            event=event['event'],
            properties=event.get('custom_variables', {})
        )
```

## Testing Webhooks

### Local Development

Use ngrok to expose your local server:

```bash
ngrok http 3000
# Use the HTTPS URL for webhook configuration
```

### Webhook Testing Tools

- [Webhook.site](https://webhook.site) - Test webhook payloads
- [RequestBin](https://requestbin.com) - Inspect webhook requests
- [Postman](https://www.postman.com) - Test and mock webhooks

## Troubleshooting

### Common Issues

{% expand title="Webhook not receiving events" %}
- Verify endpoint URL is correct and accessible
- Check firewall rules allow Mailtrap IPs
- Ensure HTTPS certificate is valid
- Confirm webhook is enabled in settings
{% endexpand %}

{% expand title="Getting 401 Unauthorized" %}
- Verify signature validation logic
- Check API credentials are correct
- Ensure timestamp validation window is appropriate
{% endexpand %}

{% expand title="Duplicate events received" %}
- Implement idempotency using `event_id`
- Store processed event IDs in cache/database
- Return 200 immediately, process async
{% endexpand %}

## Next Steps

{% hint style="success" %}
Ready to implement webhooks? Check out the full API reference below for detailed specifications and code examples.
{% endhint %}
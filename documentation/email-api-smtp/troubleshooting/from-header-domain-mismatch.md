---
title: From Header Domain Mismatch
description: >-
  How to fix "From: Header does not match the sender's domain" error in Mailtrap
  Email Live Sending.
---

# From Header mismatch

### Error message

```
From: Header does not match the sender's domain
```

This error occurs when the `From:` header in your email doesn't match your verified domain in Mailtrap.

### The requirement

To send email with Mailtrap, your `From:` header **must match** your verified domain.

{% hint style="info" %}
**Example:** If your verified domain in Mailtrap is `acme.com`, your `From:` address must be `{anything}@acme.com`.

If you're sending from a subdomain like `mail.acme.com`, your `From:` address must match that subdomain exactly.
{% endhint %}

### Common causes

**1. Unverified domain**

Your domain hasn't been added or verified in Mailtrap yet.

**Solution:**

1. Go to [Sending Domains](https://mailtrap.io/domains)
2. Add your domain
3. Complete the DNS verification process

**2. Envelope From vs Header From mismatch**

In some frameworks (like Laravel), the `MAIL_FROM_ADDRESS` variable is used for the envelope from address, but it's not the same as the header `From:` address.

{% hint style="warning" %}
Make sure both the **envelope from** and the **header from** use the same domain.
{% endhint %}

**3. Subdomain confusion**

If you verified `example.com` but are trying to send from `mail.example.com`, you need to verify the subdomain separately.

### How to fix

{% stepper %}
{% step %}
**Verify your domain**

First, check if your domain has been added to your Mailtrap account.

1. Go to [Sending Domains](https://mailtrap.io/domains)
2. Look for your domain in the list
3. Ensure it has the **Verified** badge

If not verified, complete the DNS setup process.
{% endstep %}

{% step %}
**Check your email configuration**

Ensure your email message has a `From:` header that contains an address on your verified domain.

**Example for Laravel:**

{% code title=".env" %}
```bash
MAIL_FROM_ADDRESS=noreply@yourdomain.com
MAIL_FROM_NAME="Your App Name"
```
{% endcode %}

Make sure `MAIL_FROM_ADDRESS` uses your verified domain.
{% endstep %}

{% step %}
**Verify the envelope from matches header from**

Most likely, the envelope from address is set separately from the header. Make sure they match.

For Laravel specifically:

* Check that `MAIL_FROM_ADDRESS` in your `.env` file matches your verified domain
* Verify this address is used in both the envelope and header
{% endstep %}

{% step %}
**Test your configuration**

Send a test email and verify:

* The `From:` header shows your verified domain
* The envelope from (visible in email headers) matches
* No errors appear in your logs
{% endstep %}
{% endstepper %}

### Framework-specific examples

**Laravel**

In your `.env` file:

{% code title=".env" %}
```bash
MAIL_MAILER=smtp
MAIL_HOST=live.smtp.mailtrap.io
MAIL_PORT=587
MAIL_USERNAME=your-smtp-username
MAIL_PASSWORD=your-smtp-password
MAIL_ENCRYPTION=tls
MAIL_FROM_ADDRESS=noreply@yourdomain.com
MAIL_FROM_NAME="${APP_NAME}"
```
{% endcode %}

Ensure `MAIL_FROM_ADDRESS` uses your verified domain.

**Other frameworks**

The principle is the same across all frameworks:

1. Set your `From:` address to use your verified domain
2. Ensure both envelope and header from addresses match
3. Verify the domain in Mailtrap before sending

### Still having issues?

If you've verified your domain and updated your configuration but still see this error:

* Check your email sending code for hardcoded `From:` addresses
* Look for middleware or plugins that might be modifying the `From:` header
* Review your framework's documentation for email configuration
* Contact support at [support@mailtrap.io](mailto:support@mailtrap.io)

### Related rrticles

* [Sending Domain Setup](../../sending-domain/)
* [SMTP Integration](../smtp-integration.md)
* [Sending from Domain Not Allowed](sending-from-domain-not-allowed.md)
* [Unauthorized Error (401 Code)](unauthorized-401-error.md)

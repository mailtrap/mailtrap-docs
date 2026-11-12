---
title: Sending from Domain Not Allowed
description: >-
  How to fix "Sending from domain is not allowed" (550 5.7.1) error in Mailtrap
  Email Live Sending.
---

# Domain not allowed

### Error message

```
Error: Mail command failed: 550 5.7.1 Sending from domain is not allowed
```

This error occurs when you try to send an email using SMTP with a domain that doesn't match your verified domain in Mailtrap.

### Common causes

**1. Domain mismatch**

You're sending an email with `FROM: {anything}@mydomain.com`, but in Mailtrap, you've verified `anotherdomain.com`.

**The verified domain and FROM domain in your emails must match.**

{% hint style="warning" %}
If you verified `example.com` in Mailtrap, you can only send emails from `*@example.com` addresses.
{% endhint %}

**2. Domain not verified or Compliance Check failed**

Your domain might not be fully verified, or you haven't passed the Compliance Check.

### How to fix

{% stepper %}
{% step %}
**Check your verified domains**

Go to [Sending Domains](https://mailtrap.io/domains) in your Mailtrap account.
{% endstep %}

{% step %}
**Verify domain status**

Look for the **Verified** badge next to your domain. If you don't see it:

1. Click on the domain
2. Check if all DNS records are found by Mailtrap (all should be green)
3. If any records are missing or incorrect, update them with your DNS provider
{% endstep %}

{% step %}
**Check compliance status**

Scroll down to see the **Compliance Check** status.

If the compliance check hasn't passed:

* Review any additional steps required
* Complete any pending actions
* Wait for the check to complete
{% endstep %}

{% step %}
**Update your FROM address**

Ensure your application sends emails from an address that matches your verified domain:

* **Correct:** `noreply@yourdomain.com` (if `yourdomain.com` is verified)
* **Incorrect:** `noreply@otherdomain.com` (if `otherdomain.com` is not verified)
{% endstep %}
{% endstepper %}

### Related articles

* [Sending Domain Setup](../../sending-domain/)
* [SMTP Integration](../smtp-integration.md)
* [Unauthorized Error (401 Code)](unauthorized-401-error.md)

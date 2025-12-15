---
title: Sending from Domain Not Allowed
description: >-
  How to fix "Sending from domain is not allowed" (550 5.7.1) error in Mailtrap
  Email API/SMTP.
icon: ban
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

# Domain Not Allowed

### Error Message

```
Error: Mail command failed: 550 5.7.1 Sending from domain is not allowed
```

This error occurs when you try to send an email using SMTP with a domain that doesn't match your verified domain in Mailtrap.

### Common Causes

**1. Domain Mismatch**

You're sending an email with `FROM: {anything}@mydomain.com`, but in Mailtrap, you've verified `anotherdomain.com`.

**The verified domain and FROM domain in your emails must match.**

{% hint style="warning" %}
If you verified `example.com` in Mailtrap, you can only send emails from `*@example.com` addresses.
{% endhint %}

**2. Domain Not Verified or Compliance Check Failed**

Your domain might not be fully verified, or you haven't passed the Compliance Check.

### How to Fix

{% stepper %}
{% step %}
**Check Your Verified Domains**

Go to [Sending Domains](https://mailtrap.io/sending/domains) in your Mailtrap account.
{% endstep %}

{% step %}
**Verify Domain Status**

Look for the **Verified** badge next to your domain. If you don't see it:

1. Click on the domain
2. Check if all DNS records are found by Mailtrap (all should be green)
3. If any records are missing or incorrect, update them with your DNS provider
{% endstep %}

{% step %}
**Check Compliance Status**

Scroll down to see the **Compliance Check** status.

If the compliance check hasn't passed:

* Review any additional steps required
* Complete any pending actions
* Wait for the check to complete
{% endstep %}

{% step %}
**Update Your FROM Address**

Ensure your application sends emails from an address that matches your verified domain:

* **Correct:** `noreply@yourdomain.com` (if `yourdomain.com` is verified)
* **Incorrect:** `noreply@otherdomain.com` (if `otherdomain.com` is not verified)
{% endstep %}
{% endstepper %}

### Related Articles

* [Sending Domain Setup](../setup/sending-domain/)
* [SMTP Integration](../smtp-integration.md)
* [Unauthorized Error (401 Code)](unauthorized-401-error.md)

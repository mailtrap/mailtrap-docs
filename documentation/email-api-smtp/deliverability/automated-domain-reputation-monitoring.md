---
icon: monitor-waveform
---

# Automated Domain Reputation Monitoring

Domain Reputation Monitoring is an automated feature that continuously monitors the health of your sending domains. It helps detect early warning signs that may impact your email deliverability, allowing you to address potential issues before they affect your inbox placement.

Instead of manually checking multiple tools, Domain Reputation Monitoring provides a centralized view of your domain reputation and highlights risks in real time.

{% hint style="info" %}
You can also turn on [**Reputation Alerts**](https://docs.mailtrap.io/email-api-smtp/deliverability/deliverability-alerts), which send you automated email notifications each time a critical level of any metric from **Reputation Monitoring** dashboard is hit.&#x20;
{% endhint %}

### Why it matters

Domain reputation directly affects whether your emails reach recipients' inboxes or spam folders.

With Domain Reputation Monitoring, you can:

* Detect deliverability issues early
* Identify potential root causes faster
* Take action before deliverability declines
* Reduce manual investigation across multiple tools

### What is monitored

The system continuously monitors multiple areas that affect your domain's deliverability and security. All checks are organized into dedicated sections within the dashboard.

Each monitored metric is assigned one of the following statuses:

* <mark style="color:green;">**OK (green)**</mark> - Everything is working correctly.
* <mark style="color:orange;">**Warning (orange)**</mark> - Something requires your attention.
* <mark style="color:red;">**Critical (red)**</mark> - An issue that may significantly impact deliverability or security.
* **No status (gray)** - The metric cannot be evaluated due to insufficient data or because monitoring is unavailable.

This allows you to quickly identify where problems exist and prioritize the most critical issues.

To find Reputation Monitoring Dashboard, navigate to **Domains** → **Reputation** **Monitoring**.

<figure><img src="../../.gitbook/assets/reputation monitoring.png" alt=""><figcaption></figcaption></figure>

#### 1. Sending Overview

The **Sending Overview** section provides a high-level view of your email performance.

It includes metrics such as:

* Delivered emails
* Open rate
* Click rate
* Bounces and critical bounces
* Unsubscribes
* Spam complaints and spam reporters

For each metric, you can view:

* Total volume
* Rate (percentage)
* Benchmark (expected healthy range)
* Trend over time

You can also filter data by:

* Sending stream (for example, transactional, bulk, or campaigns)
* Mailbox provider (such as Google, Yahoo, Outlook, or Office 365)

This makes it easier to identify performance drops and unusual trends.

<figure><img src="../../.gitbook/assets/reputation monitoring 2.png" alt=""><figcaption></figcaption></figure>

#### 2. Bounce Categories

The **Bounce Categories** section breaks down bounced emails by failure type.

Examples include:

* General failures
* Timeouts
* Greylisting
* Transient failures
* Verification failures
* Bad sender issues

For each category, you can monitor:

* Volume
* Rate
* Trend over time

Data can also be filtered by:

* Sending stream
* Mailbox provider

This helps you identify which types of delivery failures are increasing and where they originate.

<figure><img src="../../.gitbook/assets/reputation monitoring 3.png" alt=""><figcaption></figcaption></figure>

#### 3. Google Postmaster Data

If Google Postmaster is integrated, this section provides Gmail-specific deliverability insights, including:

* Domain reputation status (for example, High)
* Spam reported rate
* Deliverability error trends over time

These insights help diagnose issues affecting Gmail inbox placement.

<figure><img src="../../.gitbook/assets/reputation monitoring 4.png" alt=""><figcaption></figcaption></figure>

#### 4. Domain Setup Status

The **Domain Setup Status** section verifies your domain's technical configuration.

It includes checks for:

* Domain verification status
* Dedicated IP assignments
* DNS records, including:
  * DKIM
  * DMARC
  * Domain tracking
  * MX records
  * A records
* Tracking configuration, including:
  * Open tracking
  * Click tracking
  * Custom tracking domain

Each item is evaluated individually, making it easier to detect configuration issues that could affect deliverability or tracking.

#### 5. Security & Abuse Monitoring

The **Security & Abuse Monitoring** section monitors potential security threats and unusual activity.&#x20;

It includes:

* Email abuse detection
* Sending volume spikes
* Unusual recipient growth
* Web application protection
* Web form abuse
* ENV file exposure
* SMTP cracking attempts
* Google Web Risk signals
* Malware detection
* Phishing and social engineering
* Advanced phishing detection
* Unwanted software detection

This helps protect your domain against misuse and external threats.

#### 6. Blocklist Monitor

The **Blocklist Monitor** checks whether your domain appears on known email blocklists.

It displays:

* Detected listings
* Affected blocklist providers
* Status (Warning or Critical)

Because blocklist listings can significantly impact email deliverability, this section helps you quickly identify issues that require immediate attention.

#### Summary

Together, these monitoring categories provide a complete view of your domain health, including:

* **Performance** (Sending Overview)
* **Deliverability** (Bounce Categories and Google Postmaster)
* **Technical configuration** (Domain Setup Status)
* **Security** (Security & Abuse Monitoring)
* **External reputation** (Blocklist Monitor)

Instead of guessing what caused a deliverability issue, Domain Reputation Monitoring provides a structured view of your domain's health so you can identify problems and take action more quickly.

### How to access the data

Domain Reputation Monitoring is available from the **Domains** menu.

#### Dashboard

All monitoring insights are available from a dedicated dashboard.

By default, the dashboard displays data for the last **48 hours**, with options to switch to:

* Last 24 hours
* Last 7 days
* Last 14 days

The dashboard highlights:

* Healthy metrics
* Warnings
* Critical issues requiring immediate attention

### Data availability requirements

To display monitoring data or trigger notifications, your domain must send at least **1,000 emails per week**.

If this threshold is not met:

* Dashboard insights won't be displayed.
* Email notifications won't be sent.

This ensures that insights and alerts are based on statistically meaningful data.

### Automated notifications

You can configure email notifications to stay informed about changes to your domain reputation.

Two notification types are available:

#### Critical alerts

Immediate notifications when serious risks are detected.

#### Weekly summary

A digest that includes:

* Overall domain status
* Warnings
* Positive trends

### Plan availability

Domain Reputation Monitoring is available on:

* Business and Enterprise Email API/SMTP plans
* Pro Email Marketing plans

Each subscription includes full monitoring for up to **50 domains**.

Full monitoring includes:

* Dashboard
* All monitoring categories
* Email notifications
* Webhooks

#### More than 50 domains?

If your subscription includes more than 50 domains:

* You can choose which domains receive full monitoring.
* Domains outside the selected 50 receive limited monitoring (sending statistics only).
* Additional fully monitored domains can be added through a paid add-on.

When upgrading to Enterprise, the system automatically selects the 50 highest-volume sending domains for full monitoring. You can change this selection at any time.

#### Other plans

Lower-tier plans include limited monitoring consisting of:

* Sending statistics
* Per-stream and mailbox-provider views
* Basic dashboard
* Email notifications based on sending statistics

The following features are not available:

* Bounce Categories
* Blocklist Monitor
* Google Postmaster integration
* Advanced risk signals
* Domain Health Status
* Webhooks

{% hint style="info" %}
Domain Reputation Monitoring is designed for domains sending significant email volume. Your domain must send at least **1,000 emails per week** to generate monitoring insights.
{% endhint %}

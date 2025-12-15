---
title: Deliverability Alerts
description: >-
  Get weekly health status reports and critical alerts for your email
  deliverability metrics including opens, clicks, bounces, unsubscribes, and
  spam complaints.
---

# Deliverability Alerts

Deliverability Alerts help you monitor your email performance by providing automated notifications about your sending metrics.

{% hint style="info" %}
A minimum of 500 emails per week is required to receive alerts, as the system needs sufficient data to provide meaningful statistics.
{% endhint %}

You can toggle off the alerts, however, we recommend keeping them enabled because a missed issue may affect your domain authority and sender reputation.

## Health Status Weekly

Health Status Weekly alerts are sent out on Mondays and provide a detailed preview of the following stats:

* Opened
* Clicks
* Bounces
* Unsubscribes
* Spam

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/deliverability-alerts-weekly-stats.png" alt="Weekly stats table showing email metrics with color-coded status indicators for All good, Attention required, and Critical" width="563"><figcaption><p>Health Status Weekly stats</p></figcaption></figure></div>

The report includes clearly color-coded comparisons to the previous week, making it immediately obvious if one or more stats need your attention or show a negative trend. Additionally, there are insights (digest explanations of the stats) to help you troubleshoot your email infrastructure faster.

## Integrate Mailtrap Alerts with Slack

Each Slack channel has a unique email address. You can leverage that to route Mailtrap Alerts directly to Slack. Here's how to do it on the desktop app:

{% stepper %}
{% step %}
#### Open Channel Integrations

Click the channel name in the header and select **Integrations**.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/slack-channel-integrations.png" alt="Slack channel settings showing Integrations tab highlighted with arrow" width="375"><figcaption><p>Slack channel Integrations tab</p></figcaption></figure></div>
{% endstep %}

{% step %}
#### Get Email Address

Click **Send emails to this channel**, then the **Get Email Address** button.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/slack-get-email-address.png" alt="Slack modal showing Get Email Address button for sending emails to channel" width="375"><figcaption><p>Get Slack channel email address</p></figcaption></figure></div>
{% endstep %}

{% step %}
#### Add Email to Mailtrap

Navigate to the Deliverability Alerts page in Mailtrap, and paste the Slack email address into the field under **Who receives notifications?**

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/deliverability-alerts-settings.png" alt="Mailtrap Deliverability Alerts settings page showing notification recipients field with Save button" width="563"><figcaption><p>Deliverability Alerts notification settings</p></figcaption></figure></div>
{% endstep %}

{% step %}
#### Save Settings

Click **Save** and all alerts will be routed to the Slack channel instead of your email.
{% endstep %}
{% endstepper %}

## Critical Alerts

{% hint style="warning" %}
Critical Alerts feature is currently switched off. We'll notify you once it's back on.
{% endhint %}

Critical Alerts are sent hourly (the system checks your metrics every three hours for the past 24 hours) when one or more of your critical stats are below the predetermined threshold.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/critical-alerts-demo.gif" alt="Animated demonstration of Critical Alerts notification appearing on mobile device" width="563"><figcaption><p>Critical Alerts notification</p></figcaption></figure></div>

The predetermined thresholds are based on extensive cross-industry research and examples of best practices.

{% hint style="info" %}
If you're getting a lot of false positives or negatives, feel free to reach out to us at [support@mailtrap.io](mailto:support@mailtrap.io).
{% endhint %}

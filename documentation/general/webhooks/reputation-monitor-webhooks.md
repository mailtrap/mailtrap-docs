---
description: Mailtrap’s Reputation Monitor regularly checks the health of a sending domain.
hidden: true
---

# Reputation Monitor webhooks

A Reputation Monitor webhook sends an event when one of those checks changes status (for example, it gets worse or recovers), so the customer hears about it right away.

What’s checked: blocklists, Google Postmaster data (spam rate, delivery, compliance), DNS records (A, MX, DMARC), bounce categories, sending stats, Google Web Risk, and abuse signals.

What the customer can choose:

* **Domain**: one sending domain or all domains. There are no event checkboxes: the customer gets every status change.
* **What each event contains**: which check changed and its new status (e.g. reputation\_monitor.domain\_monitor.hetrix\_tools\_domain\_blacklist.blacklisted), account ID, sending domain ID and name, a severity level (e.g. warning), and a timestamp.
* **Availability**: Needs the Reputation Monitoring paid feature, with Extended Monitoring turned on for the domain. Turning Extended Monitoring off disables these webhooks for that domain.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/reputation monitor webhooks.png" alt="" width="563"><figcaption></figcaption></figure></div>

#### Use cases

* **Spot problems before customers do**: Get alerted the moment a domain lands on a blocklist or its Gmail spam rate climbs, instead of finding out from falling open rates.
* **Route alerts to the on-call team**: Send events to PagerDuty, Opsgenie or a Slack channel so whoever is on duty can act right away.
* **Pause sending automatically**: If the domain’s severity turns critical, pause marketing sends or move traffic to another domain until it’s fixed.
* **Agencies and multi-brand senders**: Watch many client domains in one place and open a ticket for the right team when one degrades.

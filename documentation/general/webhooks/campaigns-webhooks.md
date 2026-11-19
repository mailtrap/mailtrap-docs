---
description: Sends real-time events for emails sent through Mailtrap Campaigns.
hidden: true
---

# Campaigns webhooks

What the customer can choose

* **Domain**: one sending domain or all domains
* **Events**: Delivery, Soft Bounce, Bounce, Suspension, Unsubscribe, Open, Spam Complaint, Click, Reject

What each event contains: event type, message ID, recipient email, event ID, timestamp, sending domain, campaign ID, and sending stream.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/campaign webhooks.png" alt="" width="563"><figcaption></figcaption></figure></div>

#### Use cases

* **Keep the CRM in sync**: Mark contacts as unsubscribed or bounced in HubSpot/Salesforce/your own database as soon as it happens, so nobody emails them again from another tool.
* **Campaign performance in your own BI**: Stream opens and clicks per campaign into a data warehouse or dashboard (Looker, Metabase, etc.) and combine with revenue data.
* **Trigger follow-ups**: Someone clicked the pricing link in a campaign → start a follow-up sequence.


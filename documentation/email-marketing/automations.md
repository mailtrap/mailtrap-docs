---
title: Automations
description: >-
  Create automated email sequences to engage your contacts with triggers,
  actions, and rules.
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

# Automations

The Automations feature allows you to create automated email sequences to engage your contacts.

Set up triggers, actions, and rules to automate your workflows.

## Use cases

Use integrations to add contacts into Mailtrap using API, SDKs, [Make.com](https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/integrations/make), [Zapier](https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/integrations/zapier), or [N8N](https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/integrations/n8n).

{% tabs %}
{% tab title="Welcome Series" %}
**Use case**: Greet new contacts, set expectations, and share first-week tips. Perfect for onboarding new subscribers and making a great first impression.

**How to set it up**:

1. Trigger: Contact created
2. Add Send email steps with Time delays
3. Optionally: Conditional split by plan or locale
{% endtab %}

{% tab title="Onboarding Prompts" %}
**Use case**: Nudge users when a field changes (e.g., trial started, role/plan updated). Ideal for guiding users through product adoption milestones.

**How to set it up**:

1. Trigger: Contact field updated
2. Send email with next steps
3. Add to list "Onboarding" for later messages
{% endtab %}

{% tab title="Segment-Based Campaigns" %}
**Use case**: Deliver targeted content as people enter key lists. Great for webinar registrants, new customers, or list cleanup workflows.

**How to set it up**:

1. Trigger: Contact added to list (or removed from list)
2. Send email
3. Add/Remove from lists to manage follow-ups
{% endtab %}

{% tab title="Event-Driven Follow-ups" %}
**Use case**: React to product or billing events. Excellent for purchase confirmations, payment failures, or milestone celebrations.

**How to set it up**:

1. Trigger: API event received
2. Send email
3. Optionally: Update contact field and Conditional split based on event data
{% endtab %}
{% endtabs %}

## Functionality

### Available components

{% tabs %}
{% tab title="Triggers" %}
Entry points for your automation

* **Contact created** — Starts when a new contact is added
* **Contact field updated** — Fires when specific field changes
* **Contact added to list** — Activates on list addition
* **Contact removed from list** — Triggers on list removal
* **Contact custom event** — API event received

{% hint style="info" %}
Each contact can only enter the same automation once every 24 hours.
{% endhint %}
{% endtab %}

{% tab title="Actions" %}
Operations to perform on contacts

* **Send email** — Deliver personalized messages
* **Update Contact Field** — Modify contact properties
* **Unsubscribe Contact** — Remove from all marketing
* **Add to List(s)** — Assign to one or more lists
* **Remove from List(s)** — Remove from specific lists
{% endtab %}

{% tab title="Rules" %}
Control flow and timing

* **Time delay** — Wait before next step
* **Conditional Split** — Branch based on criteria
{% endtab %}
{% endtabs %}

## Triggering via API Event

"Contact custom event" trigger requires you to send an API event.

{% hint style="warning" %}
Event in the trigger settings should be equal to the event you pass via API.
{% endhint %}

Here is [description of the endpoint](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/6b1b5749b0eec-create-contact-event).

{% code title="API Event Example" %}
```bash
curl -X POST https://api.mailtrap.io/contacts/{contact_id}/events \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "event": "purchase_completed",
    "data": {
      "amount": 99.99,
      "product": "Premium Plan"
    }
  }'
```
{% endcode %}

## Limits

* Limited number of automation runs based on your plan
* Each contact can go through the same automation once in 24 hours
* Check your limits in [Billing Dashboard](https://mailtrap.io/billing/dashboard)
* Look for "Automations run count"
* Feature is currently included in your plans (may change later)

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (23).png" alt="" width="563"><figcaption></figcaption></figure></div>

## Creating your first automation

To get started, navigate to the tab in your Mailtrap account or go to [https://mailtrap.io/automations](https://mailtrap.io/automations).

{% stepper %}
{% step %}
Define the name for your automation.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (24).png" alt="" width="375"><figcaption></figcaption></figure></div>

Choose a descriptive name that indicates the automation's purpose.
{% endstep %}

{% step %}
Set up an entry trigger and select when the automation should start.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (25).png" alt="" width="375"><figcaption></figcaption></figure></div>

For this example, we'll use the "Contact created" trigger. This means the automation will start whenever a new contact is added. After selecting the trigger type, click "Save".
{% endstep %}
{% endstepper %}

## Building your automation sequence

Now that you've set up the trigger, you can start adding steps to your automation.

{% stepper %}
{% step %}
Click the "Add Step" button to add your first action.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (26).png" alt="" width="375"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
Select "Send Email" as your first action.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (27).png" alt="" width="375"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
Customize your email content and settings.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (28).png" alt="" width="375"><figcaption></figcaption></figure></div>

Add your subject line, choose a template, and personalize with merge tags.
{% endstep %}
{% endstepper %}

### Adding delays and additional steps

To create a more complex sequence, you can add time delays and further actions.

{% stepper %}
{% step %}
Insert waiting periods between actions.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (29).png" alt="" width="375"><figcaption></figcaption></figure></div>

Configure the delay duration (minutes, hours, days, or weeks).
{% endstep %}

{% step %}
Continue building your sequence with additional messages or actions.

Repeat the process to add more emails, list assignments, or field updates.
{% endstep %}
{% endstepper %}

## Automation activation

Once you've built your automation sequence, it's time to activate it.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (30).png" alt="" width="375"><figcaption></figcaption></figure></div>

{% hint style="success" %}
**Before activating**

* Test with a small group first
* Review all email content
* Verify trigger conditions
* Check time delays
{% endhint %}

### Pausing and disabling

You can pause or disable your automation at any time.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (31).png" alt="" width="375"><figcaption></figcaption></figure></div>

{% tabs %}
{% tab title="Pause Automation" %}
**Temporary suspension**

* No new contacts can enter automation
* Contacts currently in automation continue the flow
* Use when making minor adjustments
{% endtab %}

{% tab title="Disable Automation" %}
**Complete shutdown**

* No new contacts can enter automation
* All contacts currently in automation will complete their current step
* Then removed from the flow
* Use for major changes or discontinuation
{% endtab %}
{% endtabs %}

## Stats — Monitoring automation performance

You can track the performance of your automation by clicking on the Reports tab within the automation builder.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (32).png" alt="" width="375"><figcaption></figcaption></figure></div>

### Available metrics

* Open rate per email
* Click rate per email
* Number of step completions
* Delivery rate

## Best practices

* **Start simple**: Begin with basic welcome series before complex flows.
* **Test thoroughly**: Use test contacts before going live.
* **Monitor performance**: Check reports weekly for optimization opportunities.
* **Segment wisely**: Use conditional splits for personalization.
* **Time delays**: Consider time zones and optimal send times.
* **Exit strategies**: Plan how contacts leave the automation.

## Common automation workflows

### Welcome Series Template

A multi-step onboarding sequence for new contacts:

{% tabs %}
{% tab title="Flow Overview" %}
1. **Trigger**: Contact created
2. **Email 1**: Welcome message (immediate)
3. **Delay**: 2 days
4. **Email 2**: Getting started guide
5. **Delay**: 3 days
6. **Email 3**: Feature highlights
{% endtab %}

{% tab title="Implementation Tips" %}
* Personalize with first name and signup source.
* Include clear CTAs in each email.
* Track engagement for segmentation.
* Consider time zones for optimal delivery.
* Test subject lines for best open rates.
{% endtab %}
{% endtabs %}

### Re-engagement campaign

Win back inactive subscribers with targeted messaging:

{% tabs %}
{% tab title="Flow Overview" %}
1. **Trigger**: Contact added to "Inactive" list
2. **Email 1**: We miss you + special offer
3. **Delay**: 3 days
4. **Email 2**: Last chance offer
5. **Delay**: 7 days
6. **Action**: Unsubscribe contact
{% endtab %}

{% tab title="Best Practices" %}
* Use compelling subject lines ("We miss you!").
* Offer exclusive incentives.
* Show what they're missing.
* Make unsubscribe easy.
* Clean list after campaign.
{% endtab %}
{% endtabs %}

### Post-purchase flow

Maximize customer value after purchase:

1. **Trigger**: API event "purchase\_completed"
2. **Email 1**: Order confirmation
3. **Delay**: 1 hour
4. **Email 2**: Thank you + getting started
5. **Delay**: 3 days
6. **Email 3**: Tips and tricks
7. **Delay**: 7 days
8. **Email 4**: Review request
9. **Action**: Update field "customer\_status" to "active"

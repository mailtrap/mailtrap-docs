---
title: Automations
description: >-
  Create automated email sequences to engage your contacts with triggers,
  actions, and rules
icon: robot
---

# Automations

Automations feature allows you to create automated email sequences to engage your contacts.

Set up triggers, actions, and rules to automate your workflows.

## Use Cases

Use [Integrations](https://mailtrap.io/integrations) to add contacts into Mailtrap using API, SDKs, Make.com, Zapier or n8n integration.

{% tabs %}
{% tab title="Welcome Series" %}
**Greet new contacts, set expectations, and share first-week tips**

How to set it up:

* Trigger: Contact created
* Add Send email steps with Time delays
* Optionally: Conditional split by plan or locale

Perfect for onboarding new subscribers and making a great first impression.
{% endtab %}

{% tab title="Onboarding Prompts" %}
**Nudge users when a field changes (e.g., trial started, role/plan updated)**

How to set it up:

* Trigger: Contact field updated
* Send email with next steps
* Add to list "Onboarding" for later messages

Ideal for guiding users through product adoption milestones.
{% endtab %}

{% tab title="Segment-Based Campaigns" %}
**Deliver targeted content as people enter key lists**

How to set it up:

* Trigger: Contact added to list (or removed from list)
* Send email
* Add/Remove from lists to manage follow-ups

Great for webinar registrants, new customers, or list cleanup workflows.
{% endtab %}

{% tab title="Event-Driven Follow-ups" %}
**React to product or billing events**

How to set it up:

* Trigger: API event received
* Send email
* Optionally: Update contact field and Conditional split based on event data

Excellent for purchase confirmations, payment failures, or milestone celebrations.
{% endtab %}
{% endtabs %}

## Functionality

### Available Components

{% tabs %}
{% tab title="Triggers" %}
**Entry points for your automation**

* **Contact created** - Starts when a new contact is added
* **Contact field updated** - Fires when specific field changes
* **Contact added to list** - Activates on list addition
* **Contact removed from list** - Triggers on list removal
* **Contact custom event** - API event received

{% hint style="info" %}
Each contact can only enter the same automation once every 24 hours.
{% endhint %}
{% endtab %}

{% tab title="Actions" %}
**Operations to perform on contacts**

* **Send email** - Deliver personalized messages
* **Update Contact Field** - Modify contact properties
* **Unsubscribe Contact** - Remove from all marketing
* **Add to List(s)** - Assign to one or more lists
* **Remove from List(s)** - Remove from specific lists
{% endtab %}

{% tab title="Rules" %}
**Control flow and timing**

* **Time delay** - Wait before next step
* **Conditional Split** - Branch based on criteria
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

{% hint style="info" %}
**Automation Limits**

* Limited number of automation runs based on your plan
* Each contact can go through the same automation once in 24 hours
* Check your limits in [Billing Dashboard](https://mailtrap.io/billing/dashboard)
* Look for "Automations run count"
* Feature is currently included in your plans (may change later)
{% endhint %}

<div align="left"><img src="../.gitbook/assets/marketing-automation-runs-limit.png" alt="Billing dashboard showing automation runs limit counter" width="563"></div>

## Creating Your First Automation

To get started, navigate to the tab in your Mailtrap account or go to [https://mailtrap.io/automations](https://mailtrap.io/automations).

{% stepper %}
{% step %}
#### Create New Automation

Define the name for your automation.

<div align="left"><img src="../.gitbook/assets/marketing-automation-create-name.png" alt="Dialog to enter automation name" width="375"></div>

Choose a descriptive name that indicates the automation's purpose.
{% endstep %}

{% step %}
#### Set Up Entry Trigger

Select when the automation should start.

<div align="left"><img src="../.gitbook/assets/marketing-automation-trigger-setup.png" alt="Interface showing automation trigger selection options" width="563"></div>

For this example, we'll use the "Contact created" trigger. This means the automation will start whenever a new contact is added. After selecting the trigger type, click "Save".
{% endstep %}
{% endstepper %}

## Building Your Automation Sequence

Now that you've set up the trigger, you can start adding steps to your automation.

{% stepper %}
{% step %}
#### Add an Action

Click the "Add Step" button to add your first action.

<div align="left"><img src="../.gitbook/assets/marketing-automation-add-action.png" alt="Button to add a new action to the automation sequence" width="375"></div>

<div align="left"><img src="../.gitbook/assets/marketing-automation-send-email-action.png" alt="Action selection menu showing Send Email option" width="563"></div>

Select "Send Email" as your first action.
{% endstep %}

{% step %}
#### Configure the Email

Set up your email content and settings.

<div align="left"><img src="../.gitbook/assets/marketing-automation-configure-email.png" alt="Email configuration interface with subject and content fields" width="563"></div>

Add your subject line, choose a template, and personalize with merge tags.
{% endstep %}
{% endstepper %}

### Adding Delays and Additional Steps

To create a more sophisticated sequence, you can add time delays and further actions.

{% stepper %}
{% step %}
#### Add a Time Delay

Insert waiting periods between actions.

<div align="left"><img src="../.gitbook/assets/marketing-automation-time-delay.png" alt="Time delay configuration showing options for delay duration" width="563"></div>

Configure the delay duration (minutes, hours, days, or weeks).
{% endstep %}

{% step %}
#### Add Another Email

Continue building your sequence with additional messages or actions.

Repeat the process to add more emails, list assignments, or field updates.
{% endstep %}
{% endstepper %}

## Automation Activation

Once you've built your automation sequence, it's time to activate it.

### Activate Automation

<div align="left"><img src="../.gitbook/assets/marketing-automation-activate.png" alt="Button to activate the automation" width="375"></div>

{% hint style="success" %}
**Before Activating**

* Test with a small group first
* Review all email content
* Verify trigger conditions
* Check time delays
{% endhint %}

### Pausing and Disabling

You can pause or disable your automation at any time.

<div align="left"><img src="../.gitbook/assets/marketing-automation-pause-disable.png" alt="Menu showing pause and disable automation options" width="375"></div>

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

## Stats - Monitoring Automation Performance

You can track the performance of your automation by clicking on the Reports tab within the automation builder.

<div align="left"><img src="../.gitbook/assets/marketing-automation-reports.png" alt="Automation reports dashboard showing performance metrics for each step" width="563"></div>

### Available Metrics

**Engagement Metrics**

* Open rate per email
* Click rate per email
* Number of step completions
* Delivery rate

## Best Practices

{% hint style="success" %}
**Automation Tips**

1. **Start Simple**: Begin with basic welcome series before complex flows
2. **Test Thoroughly**: Use test contacts before going live
3. **Monitor Performance**: Check reports weekly for optimization opportunities
4. **Segment Wisely**: Use conditional splits for personalization
5. **Time Delays**: Consider time zones and optimal send times
6. **Exit Strategies**: Plan how contacts leave the automation
{% endhint %}

## Common Automation Workflows

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
* Personalize with first name and signup source
* Include clear CTAs in each email
* Track engagement for segmentation
* Consider time zones for optimal delivery
* Test subject lines for best open rates
{% endtab %}
{% endtabs %}

### Re-engagement Campaign

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
* Use compelling subject lines ("We miss you!")
* Offer exclusive incentives
* Show what they're missing
* Make unsubscribe easy
* Clean list after campaign
{% endtab %}
{% endtabs %}

### Post-Purchase Flow

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

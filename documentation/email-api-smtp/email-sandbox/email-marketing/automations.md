# Automations

* [Building automation sequence](https://help.mailtrap.io/article/170-automations#Building-your-automation-sequence-DQlC8)
* [Adding delays and additional steps](https://help.mailtrap.io/article/170-automations#Adding-Delays-and-Additional-Steps-SeU37)
* [Automation activation](https://help.mailtrap.io/article/170-automations#Automation-activation-A4zJZ)
* [Monitoring automation's performance](https://help.mailtrap.io/article/170-automations#Monitoring-automations-performance-NZnhx)

\


Automations feature allows you to create, automated email sequences to engage your contacts.

Set up triggers, actions, and rules to automate your workflows.

### Use cases

Use [Integrations](https://mailtrap.io/integrations) to add contacts into Mailtrap using API, SDKs, Make.com, Zapier or n8n integration.

Welcome series

* Greet new contacts, set expectations, and share first-week tips.
* How to set it up: Trigger Contact created → add Send email steps with Time delays → optionally Conditional split by plan or locale.

Onboarding prompts from profile changes

* Nudge users when a field changes (e.g., trial started, role/plan updated).
* How to set it up: Trigger Contact field updated → Send email with next steps → Add to list “Onboarding” for later messages.

Segment-based campaigns

* Deliver targeted content as people enter key lists (webinar registrants, paying customers) — or clean up when they leave.
* How to set it up: Trigger Contact added to list (or removed from list) → Send email → Add/Remove from lists to manage follow-ups.

Event-driven follow-ups

* React to product or billing events (purchase made, payment failed, milestone hit) with confirmations, guides, or recovery emails.
* How to set it up: Trigger API event received → Send email → optionally Update contact field and Conditional split based on event data.&#x20;

### Functionality

#### Triggers

* Contact created
* Contact field updated
* Contact added to list
* Contact removed from list
* Contact custom event (API event received)

#### Actions

* Send email
* Update Contact Field
* Unsubscribe Contact
* Add to List(s)
* Remove from List(s)

#### Rules

* Time delay
* Conditional Split

### Triggering via API event

"Contact custom event" trigger requires you to send an API event.

Here is [description of the endpoint](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/6b1b5749b0eec-create-contact-event).

Event in the trigger settings should be equal to the event you pass via API.

### Limits

* You have a limited number of automation runs; higher plans have higher limits. You can check them in [Billing Dashboard](https://mailtrap.io/billing/dashboard), look for Automations run count.
* Each contact can go through the same automation once in 24 hours.
* The feature is currently free/include in your plans; it might change later.

<figure><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68876c26734dd51cee2971c4/file-vsNWlBpDmt.png" alt=""><figcaption><p>Check your runs limit</p></figcaption></figure>

### Creating your first automation

To get started, navigate to the tab in your Mailtrap account or go to [https://mailtrap.io/automations](https://mailtrap.io/automations).

Create a new automation:

1. Define the name

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68876d0180463b1f483684aa/file-DFOkXyJzgx.png)

2. Set up an Entry Trigger

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68876df480463b1f483684ac/file-eAQf1nTGVA.png)

For this example, we'll use the "Contact created" trigger. This means the automation will start whenever a new contact is added. After selecting the trigger type, click "Save".

### Building your automation sequence <a href="#building-your-automation-sequence-dqlc8" id="building-your-automation-sequence-dqlc8"></a>

Now that you've set up the trigger, you can start adding steps to your automation.

1. **Add an Action:**

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68876e7bb3b3eb04f64279d0/file-pTi6DNCIyX.png)

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68876eb2f35f195c4aa8de06/file-0SgJ36vkAz.png)

2. **Configure the Email**

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68876ee5734dd51cee2971cb/file-9hQKPWBUGY.png)

#### Adding delays and additional steps

To create a more sophisticated sequence, you can add time delays and further actions.

1. **Add a Time Delay** and configure it.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68877163c3d29c692643b09d/file-Fo2bkCnF8m.png)

2. **Add Another Email**

### Automation activation <a href="#automation-activation-a4zjz" id="automation-activation-a4zjz"></a>

Once you've built your automation sequence, it's time to activate it.

**Activate Automation:**

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68876f4f80463b1f483684b5/file-KmTqdw7jnj.png)

**Pausing and Disabling:**

You can pause or disable your automation at any time.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68876fbd80463b1f483684b7/file-fa63jJ6vVF.png)

* **Pause Automation:** No new contacts can enter automation, but contacts currently in automation continue the flow.
* **Disable Automation:** No new contacts can enter automation, and all contacts currently in automation will complete their current step and then be removed from the flow.

### Stats - Monitoring automation's performance

You can track the performance of your automation by clicking on the Reports tab within the automation builder. Here you can see metrics for each step of your sequence, including how many contacts have completed each action and the open and click rates for your emails.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/6887700ef35f195c4aa8de0a/file-9GKCPtPFhX.png)

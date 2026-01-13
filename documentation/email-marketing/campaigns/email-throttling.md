---
icon: gauge-high
---

# Email throttling

Spread campaign delivery over time rather than send all emails simultaneously and avoid sudden traffic spikes that can trigger ESP/IP reputation issues.

{% hint style="info" %}
The feature applies to both [shared and dedicated IP](https://docs.mailtrap.io/email-api-smtp/deliverability/ip-warmup) users for UI-launched campaigns only, not transactional or bulk stream.
{% endhint %}

### How to configure email throttling

We have introduced a new step in the Campaign creation flow called Delivery.

{% stepper %}
{% step %}
### Create your Campaign

Set up your Details, Design, and Audience as usual.
{% endstep %}

{% step %}
### Navigate to Step 4 (Delivery)

Here you will see two options:

* **Send all at once**: The standard method where Mailtrap attempts to deliver emails as fast as possible.
* **Send gradually (Throttling)**: The new option to control speed.
{% endstep %}

{% step %}
### Set your limit

Select Send gradually. Enter the number of Emails to send per hour.

<figure><img src="../../.gitbook/assets/Screenshot 2026-01-13 at 13.03.04.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Proceed to Schedule

Click **Continue**.

<figure><img src="../../.gitbook/assets/Screenshot 2026-01-13 at 13.12.45.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The Schedule options have moved to a dedicated Step 5. You can now choose to start the gradual process immediately ("No schedule") or pick a specific start date and time.
{% endhint %}
{% endstep %}
{% endstepper %}

### Benefits

Sending a massive blast of emails all at once can sometimes overwhelm recipient servers or trigger spam filters. By throttling your campaign, you can:

{% tabs %}
{% tab title="Improve deliverability" %}
Mimic more natural sending behavior, build trust with ISPs over time, avoid spam filters, and maximize engagement with your subscribers.
{% endtab %}

{% tab title="Protect sender reputation" %}
Avoid being flagged as "suspicious" by mailbox providers (Gmail, Outlook, etc.) due to sudden volume spikes.
{% endtab %}

{% tab title="Manage server load" %}
Lessen the immediate load on receiving servers so your emails are processed smoothly and delivered without any delays.
{% endtab %}
{% endtabs %}

### Use cases

{% tabs %}
{% tab title="Warming up sender reputation" %}
**Who is it for**: Teams sending medium to large campaigns.

We recommend enabling throttling from the very first campaigns, even for smaller batches of a few hundred recipients, to establish healthy sending patterns.
{% endtab %}

{% tab title="Managing large-scale campaigns (50K+)" %}
**Who is it for**: Anyone operating under hourly sending limits or following deliverability best practices.

Even for well-warmed senders, throttling helps control delivery pace and avoid volume spikes and possible limitations due to irregular sending patterns.
{% endtab %}
{% endtabs %}

### How email throttling works

By default, Mailtrap Email Campaigns send messages at the maximum possible speed. For high-volume senders, this can create challenges: many major email service providers may flag or block sudden bursts of traffic as suspicious, impacting deliverability. Managing this manually often requires workarounds that add extra time and effort.

Throttling allows you to set a maximum number of emails Mailtrap will send per hour for a campaign (e.g., 100 emails per hour). After setting the limit, Mailtrap automatically paces delivery to stay within your defined threshold - sending continuously but never exceeding it. This provides a predictable sending cadence, better control over sender reputation, and a safer rollout of large campaigns.

{% hint style="info" %}
The maximum throttling limit is 150,000 emails per hour.
{% endhint %}

When you set an hourly limit, Mailtrap does not send one email every minute. Instead, it splits your hourly limit into 5-minute batches.

**The formula**:

`[Emails per Hour] ÷ 12 = Emails sent every 5 minutes`

**Example**:

If you set your limit to 60 emails per hour:

* Mailtrap will send **5 emails** every **5 minutes**
* 60 emails / 12 five-minute slots = 5 emails per slot

#### Monitor your campaign

Once a gradual campaign has started, you can monitor its progress in real-time.

Go to your Campaigns list and click on the campaign being sent.

* **Status bar**: You will see a progress bar showing "X out of Y emails have been sent."
* **Delivery mode**: The details section will confirm the mode is set to "Send gradually" and show your configured rate (e.g., 60/hr).
* **Terminate sending**: If you need to stop the campaign immediately, click the red Terminate Sending button in the top right corner.

<figure><img src="../../.gitbook/assets/Screenshot 2026-01-13 at 13.28.43.png" alt=""><figcaption></figcaption></figure>

If you notice your inbox placement rates dropping, an increase in bounce rates or spam complaints, or if emails are taking longer than usual to deliver, terminate the campaign and review the recipients.<br>

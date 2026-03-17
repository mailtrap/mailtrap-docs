# Squarespace

To start sending emails with Mailtrap, you need to own a domain (e.g., yourcompany.com) and then verify your ownership over it. For this, you'll need access to your Squarespace account, more specifically, the DNS records management page.

In this guide, you'll learn how to add and verify a domain from Squarespace.

This guide assumes your domain uses Squarespace's nameservers (e.g., `ext-cust.squarespace.com`). This applies whether you registered your domain directly with Squarespace or pointed your DNS to Squarespace from another registrar. Not sure? Check your domain registrar's settings or look for where you manage your DNS records. If it's in the Squarespace Domains panel, you're in the right place.

### Step-by-step guide

{% stepper %}
{% step %}
Log in to your [Squarespace account](https://account.squarespace.com).
{% endstep %}

{% step %}
In the account menu, click **Domains**.

<figure><img src="../../../.gitbook/assets/Screenshot 2026-03-17 at 20.13.59.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Click the domain you want to verify.
{% endstep %}

{% step %}
Click **DNS Settings** and navigate down to **Custom records**.

<figure><img src="../../../.gitbook/assets/Screenshot 2026-03-17 at 20.28.14.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
In a separate browser tab, log in to your [Mailtrap account](https://mailtrap.io).
{% endstep %}

{% step %}
Navigate to **Sending Domains** and click on your domain.
{% endstep %}

{% step %}
Open the **Domain Verification** page; you will see a list of DNS records to add.

<figure><img src="../../../.gitbook/assets/Screenshot 2026-03-17 at 20.14.23.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
You will need to add the following record types. Here’s the basic field name mapping, see the next step for record-by-record mapping.&#x20;

| **Mailtrap UI** | **Squarespace UI (CNAME)** | **Squarespace UI (TXT)** |
| --------------- | -------------------------- | ------------------------ |
| Type            | Type dropdown              | Type dropdown            |
| Name            | Host                       | Host                     |
| Value           | Alias Data                 | Text                     |
| TTL (Auto)      | TTL (leave default)        | TTL (leave default)      |
{% endstep %}

{% step %}
Here’s the full record-by-record mapping:

| **Mailtrap Record**         | **Squarespace Type** | **Squarespace Host**                 | **Squarespace Value Field** | **What to paste**            |
| --------------------------- | -------------------- | ------------------------------------ | --------------------------- | ---------------------------- |
| Domain Verification (CNAME) | CNAME                | Copy Name from Mailtrap              | Alias Data                  | Copy **Value** from Mailtrap |
| DKIM 1 (CNAME)              | CNAME                | rwmt1.\_domainkey                    | Alias Data                  | Copy **Value** from Mailtrap |
| DKIM 2 (CNAME)              | CNAME                | rwmt2.\_domainkey                    | Alias Data                  | Copy **Value** from Mailtrap |
| Custom Tracking (CNAME)     | CNAME                | mt-link (or whatever Mailtrap shows) | Alias Data                  | Copy **Value** from Mailtrap |
| DMARC (TXT)                 | TXT                  | \_dmarc                              | Text                        | Copy **Value** from Mailtrap |

For each record, go back to Squarespace **DNS Settings** → click **Add Record** → select the **Type** (CNAME or TXT) → paste the **Name** and **Value** from Mailtrap → click **Save**.
{% endstep %}

{% step %}
Repeat step 9 for all records listed on your Mailtrap **Domain** **Verification** page.

{% hint style="info" %}
* **Squarespace doesn’t require you to add the SPF record**.
* **Different value field names** - Squarespace calls CNAME values "Alias Data" and TXT values "Text". Mailtrap calls both just "Value".
* **No trailing dot** - If Mailtrap's value ends with a (.), remove it before pasting into Squarespace.
* **Host = subdomain only** - Squarespace auto-appends your domain. If Mailtrap shows rwmt1.\_domainkey.yourdomain.com, enter only rwmt1.\_domainkey.
* **Squarespace does not support CNAME records on the root ( @ ) of the domain**. If a provider’s instructions tell you to create a CNAME with  @  as Host, this won’t work on Squarespace. Instead, use a subdomain (for example,  www ) for the CNAME and keep an A/ALIAS record on the root, or host your DNS with a provider that supports root‑level CNAME flattening.
{% endhint %}
{% endstep %}

{% step %}
Go back to your Mailtrap **Domain Verification** page.
{% endstep %}

{% step %}
Click **Re-check DNS Records**.
{% endstep %}

{% step %}
Once all records show a green verified status, your domain is verified and ready to send.

<figure><img src="../../../.gitbook/assets/Screenshot 2026-03-17 at 20.14.49.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
DNS changes can take **15 minutes to a few hours** to propagate across the internet. In rare cases, propagation may take up to 24 hours. Mailtrap automatically re-checks DNS records every hour, but you can trigger a manual check anytime with the **Re-check DNS Records** button.
{% endhint %}
{% endstep %}
{% endstepper %}

If you have additional questions, consult the official [Squarespace DNS documentation](https://support.squarespace.com/hc/en-us/articles/360001280748) or contact Mailtrap support at [support@mailtrap.io](mailto:support@mailtrap.io).

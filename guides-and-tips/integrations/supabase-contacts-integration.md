---
title: Sync Contacts with Supabase
description: >-
  Seamlessly sync your Supabase user base with Mailtrap to update email lists,
  create segments, launch personalized campaigns, and measure effectiveness.
---

# Sync Contacts with Supabase

You can seamlessly sync your Supabase user base with Mailtrap, which allows you to:

* Seamlessly update your email list
* Create segments based on user data
* Launch personalized email campaigns
* Measure campaign effectiveness

In this guide, you'll learn how to:

* Generate a Mailtrap API token
* Create contacts in Supabase and Mailtrap
* Update contacts in Supabase and Mailtrap
* Demo and test the integration

{% hint style="info" %}
You can read more about Contacts in our [dedicated article](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-marketing/contacts).
{% endhint %}

## Generate a Mailtrap API token

Whether you want to only create contacts or update them via Mailtrap x Supabase, you'll first need a Mailtrap API token.

{% stepper %}
{% step %}
### Access API Tokens

Go to **Settings** on the left side-bar menu, navigate to **API Tokens**, and click on **Add Token**.

![Mailtrap Settings page showing API Tokens section with Add Token button highlighted](../.gitbook/assets/supabase-contacts-integration-1.png)
{% endstep %}

{% step %}
### Configure Token Permissions

Enter the desired name, click on **Add Token**, tick the desired permission checkboxes, and hit **Save**.

![Mailtrap API Token creation dialog with name field and permission checkboxes](../.gitbook/assets/supabase-contacts-integration-2.png)
{% endstep %}

{% step %}
### Copy and Store Token

Copy the token and save it in a secure place.

![Mailtrap API Token display showing generated token ready to copy](../.gitbook/assets/supabase-contacts-integration-3.png)
{% endstep %}
{% endstepper %}

## Creating contacts

Before we start, let me briefly explain the workflow:

* A user registers in your app
* Their email appears not only in Supabase but also in the Contacts page
* Then, you can easily group the new contact into different lists, segments, etc.

### Step 1. Create an Edge Function in Supabase

First, let's create an Edge Function containing our Mailtrap API token.

{% stepper %}
{% step %}
### Open Edge Functions

Open your Supabase [project dashboard](https://supabase.com/dashboard/projects) and go to **Edge Functions**.

![Supabase project dashboard with Edge Functions navigation highlighted in sidebar](../.gitbook/assets/supabase-contacts-integration-4.png)
{% endstep %}

{% step %}
### Deploy New Function

Click on **Deploy a new Function** in the upper-right corner and select **Via Editor**.

![Supabase Edge Functions page showing Deploy a new Function button with dropdown menu](../.gitbook/assets/supabase-contacts-integration-5.png)
{% endstep %}

{% step %}
### Add Function Code

Inside the function editor, you should see the default serverless function template.

![Supabase Edge Function editor showing default function template code](../.gitbook/assets/supabase-contacts-integration-6.png)

Replace it with the following code snippet that will send user data to Contacts:

{% code title="create-contact Edge Function" %}
```javascript
const MAILTRAP_API_TOKEN = Deno.env.get("MAILTRAP_TOKEN") || "";
const MAILTRAP_ACCOUNT_ID = Deno.env.get("MAILTRAP_ACCOUNT_ID") || "";

const handler = async (req) => {
  const requestData = await req.json();
  const { email } = requestData.record;
  const options = {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      "Accept": "application/json",
      "Authorization": `Bearer ${MAILTRAP_API_TOKEN}`
    },
    body: JSON.stringify({
      contact: {
        email: email,
        list_ids: [
          4292 // List for New Users
        ]
      }
    })
  };
  return await fetch(`https://mailtrap.io/api/accounts/${MAILTRAP_ACCOUNT_ID}/contacts`, options);
};

Deno.serve(handler);
```
{% endcode %}

Replace the variable `list_ids:` value (4292 in this example) with the ID of the list where you want to add the contact.

Then, click on **Deploy Function**.

![Supabase Edge Function editor with Deploy Function button highlighted](../.gitbook/assets/supabase-contacts-integration-7.png)
{% endstep %}

{% step %}
### Verify Deployment

Supabase will build and deploy the Edge Function.

![Supabase Edge Function deployment progress showing build and deploy status](../.gitbook/assets/supabase-contacts-integration-8.png)
{% endstep %}
{% endstepper %}

### Step 2. Set up webhooks for contact creation

Next, we will create a [Supabase Webhook](https://supabase.com/docs/guides/database/webhooks) to trigger the Edge Function we just created.

{% stepper %}
{% step %}
### Navigate to Database Webhooks

Open your Supabase Dashboard, go to **Database Webhooks**, and click on **Create a new hook**.

![Supabase Database page with Webhooks section and Create a new hook button](../.gitbook/assets/supabase-contacts-integration-9.png)
{% endstep %}

{% step %}
### Configure Basic Settings

Configure the following:

* **Name**: create\_contact
* **Table**: users
* **Events**: ✅ Insert

![Supabase webhook configuration form showing name, table, and Insert event checkbox](../.gitbook/assets/supabase-contacts-integration-10.png)
{% endstep %}

{% step %}
### Configure Webhook Type

Configure the following:

* Choose **Supabase Edge Functions** under 'Webhook configuration'
* Go for **POST** under 'Method'
* Select the previously created function **create-contact**
* Set the desired timeout (e.g., 5000)

![Supabase webhook configuration showing Edge Functions type, POST method, and function selection](../.gitbook/assets/supabase-contacts-integration-11.png)
{% endstep %}

{% step %}
### Set HTTP Headers

Set HTTP headers for Auth:

* **Content-type**: application/json
* **Authorization**: Bearer \[your-token]

Click **Create webhook** to activate it.

![Supabase webhook HTTP headers configuration with Content-type and Authorization fields](../.gitbook/assets/supabase-contacts-integration-12.png)
{% endstep %}
{% endstepper %}

## Updating contacts

Here, the flow is quite similar to creating contacts, with the major difference being the code we'll use.

How it works:

* A registered user updates their name/account info
* The newly updated info appears not only in Supabase but also in the Mailtrap Contacts page
* Then, you can send more personalized emails (e.g., name or state fields)

### Step 1. Create an edge function

Again, we start by creating an Edge Function and adding Mailtrap API token to it.

{% stepper %}
{% step %}
### Open Edge Functions

Open your Supabase [project dashboard](https://supabase.com/dashboard/projects) and go to **Edge Functions**.

![Supabase project dashboard with Edge Functions navigation highlighted in sidebar](../.gitbook/assets/supabase-contacts-integration-4.png)
{% endstep %}

{% step %}
### Deploy New Function

Click on **Deploy a new function** in the upper-right corner and select **Via Editor**.

![Supabase Edge Functions page showing Deploy a new function button with dropdown menu](../.gitbook/assets/supabase-contacts-integration-5.png)
{% endstep %}

{% step %}
### Add Function Code

Inside the function editor, you should see the default serverless function template.

![Supabase Edge Function editor showing default function template code](../.gitbook/assets/supabase-contacts-integration-6.png)

Replace it with the following code snippet, which will:

* Receive user data from the webhook
* Call the Mailtrap API to update existing contact details

{% code title="update-contact Edge Function" %}
```javascript
// Setup type definitions for built-in Supabase Runtime APIs
import "jsr:@supabase/functions-js/edge-runtime.d.ts";
import { createClient } from 'jsr:@supabase/supabase-js@2';

// Define environment variables (you'll need to set these in Supabase)
const MAILTRAP_API_TOKEN = Deno.env.get("MAILTRAP_TOKEN") || "";
const MAILTRAP_ACCOUNT_ID = Deno.env.get("MAILTRAP_ACCOUNT_ID") || "";

const handler = async (req) => {
  const requestData = await req.json();
  let userEmail;
  try {
    const supabase = createClient(Deno.env.get('SUPABASE_URL'), Deno.env.get('SUPABASE_SERVICE_ROLE_KEY'), {
      auth: {
        autoRefreshToken: false,
        persistSession: false
      }
    });
    // Access auth admin api
    const { data, error } = await supabase.auth.admin.getUserById(requestData.record.id);
    if (error) {
      throw error;
    }
    userEmail = data.user.email;
  } catch (err) {
    // error handling
  }
  const options = {
    method: "PATCH",
    headers: {
      "Content-Type": "application/json",
      "Accept": "application/json",
      "Authorization": `Bearer ${MAILTRAP_API_TOKEN}`
    },
    body: JSON.stringify({
      contact: {
        email: userEmail,
        fields: {
          name: requestData.record.full_name
        },
        unsubscribed: false
      }
    })
  };
  return await fetch(`https://mailtrap.io/api/accounts/${MAILTRAP_ACCOUNT_ID}/contacts/${userEmail}`, options);
};

Deno.serve(handler);
```
{% endcode %}

And, of course, click on **Deploy updates/Deploy function**.

![Supabase Edge Function editor with Deploy function button highlighted](../.gitbook/assets/supabase-contacts-integration-16.png)
{% endstep %}
{% endstepper %}

### Step 2. Set up a webhook for updating contacts

{% stepper %}
{% step %}
### Create Webhook

If you don't already have a webhook for updating contacts, open your Supabase Dashboard, go to **Database Webhooks**, and click on **Create a new hook**.

Navigate to **Integrations** → **Webhooks** and configure the following:

* **Name**: update\_contact
* **Table**: profiles
* **Events**: ✅ Update

![Supabase webhook configuration form showing name set to update\_contact, table set to profiles, and Update event checkbox](../.gitbook/assets/supabase-contacts-integration-17.png)
{% endstep %}

{% step %}
### Configure Webhook Settings

Configure the following:

* **Type of webhook**: HTTP Request
* **Method**: POST
* **Edge Function**: Select the previously created **update-contact** function
* **Add HTTP Headers**:
  * **Content-Type**: application/json
  * **Authorization**: Bearer \[your-token]

![Supabase webhook configuration showing HTTP Request type, POST method, Edge Function selection, and HTTP headers](../.gitbook/assets/supabase-contacts-integration-18.png)
{% endstep %}
{% endstepper %}

## Integration demo and testing

Finally, let's test our webhook configuration. For this example, I'll use a demo app created in FlutterFlow.

{% stepper %}
{% step %}
### Create Test Account

First, create an account as if you were a new user.

![Demo app account creation form showing email and password fields with Create Account button](../.gitbook/assets/supabase-contacts-integration-19.png)
{% endstep %}

{% step %}
### Verify in Supabase

A new user should appear in the **Users** page within your Supabase Project.

![Supabase Authentication Users page showing newly created user in table](../.gitbook/assets/supabase-contacts-integration-20.png)
{% endstep %}

{% step %}
### Verify in Mailtrap

At the same time, a new user also appears in your Mailtrap Contacts page.

![Mailtrap Contacts page showing newly synced contact with email address](../.gitbook/assets/supabase-contacts-integration-21.png)
{% endstep %}

{% step %}
### Check Initial Data

Since the demo app only requires email and password upon registration, that's all the info the webhook sends to the Mailtrap Contacts page initially.

![Mailtrap contact detail showing only email field populated](../.gitbook/assets/supabase-contacts-integration-22.png)
{% endstep %}

{% step %}
### Update Profile

If you go to your demo app and update the profile name...

![Demo app profile update form showing full name field being edited](../.gitbook/assets/supabase-contacts-integration-23.png)
{% endstep %}

{% step %}
### Verify Update in Supabase

It should get updated in your Supabase Project...

![Supabase profiles table showing updated full\_name field](../.gitbook/assets/supabase-contacts-integration-24.png)
{% endstep %}

{% step %}
### Verify Update in Mailtrap

And the Mailtrap Contacts Page, so everything works as intended!

![Mailtrap Contacts page showing updated contact with name field now populated](../.gitbook/assets/supabase-contacts-integration-25.png)

Now, every time a new user logs in and updates their name, their information will be logged in your Mailtrap Contacts page. There, you can group them into lists, segment them accordingly, and use Fields to personalize your email campaigns further.
{% endstep %}
{% endstepper %}

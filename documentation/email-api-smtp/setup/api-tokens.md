---
title: API Tokens
description: Learn how to create, manage, and use API tokens for Email API/SMTP.
icon: key
---

# API Tokens

<details>

<summary>For use with AI assistants</summary>

AI-readable resources:

This page as Markdown — [https://docs.mailtrap.io/email-api-smtp/setup/api-tokens.md](https://docs.mailtrap.io/email-api-smtp/setup/api-tokens.md)

API reference as Markdown — [https://docs.mailtrap.io/developers/account-management/api-tokens.md](https://docs.mailtrap.io/developers/account-management/api-tokens.md)

llms.txt — [https://docs.mailtrap.io/llms.txt](https://docs.mailtrap.io/llms.txt)

llms-full.txt — [https://docs.mailtrap.io/llms-full.txt](https://docs.mailtrap.io/llms-full.txt)



* The very first API token must be created manually by the user in the Mailtrap UI at [https://mailtrap.io/settings/api-tokens](https://mailtrap.io/settings/api-tokens) — this cannot be done via API.
* Once a token exists, all further token management — creating, resetting, and deleting tokens — can be done programmatically via the API.
* Before creating, ask the user for the token name and desired permissions&#x20;
* Important: the full token value is only returned on create or reset. Store it securely — it cannot be retrieved again.

</details>

#### Add and manage tokens manually

{% @arcade/embed flowId="iWYZTaQURqnQsQBjRPqk" url="https://app.arcade.software/share/iWYZTaQURqnQsQBjRPqk" %}

{% stepper %}
{% step %}
Navigate to **Settings** in the menu on the left and select **API Tokens**.
{% endstep %}

{% step %}
To add a new token, click the **Add Token** button in the upper-right corner.
{% endstep %}

{% step %}
**Type the token name** into the designated field.&#x20;

It’s perfectly fine to have a custom name for the API token, as it’s only for your reference, regardless of the use case.
{% endstep %}

{% step %}
**Assign permissions** by checking the boxes in the corresponding access level columns. Note that you must have admin permissions on a particular domain to send emails with this token.
{% endstep %}

{% step %}
Click the **Save** button and preview the new token under the **API Tokens** main menu.
{% endstep %}
{% endstepper %}

#### Auto-created token per domain

When you create a domain, a token is automatically created and named based on the following formula: \[domain name] + \[token] + \[token ID].

For example, if you add the example.com domain, the token for that domain will be named example.com token 1234. By default, the automatically generated token gets Domain Admin Mailtrap for the given domain.

{% hint style="info" %}
You need to edit permissions for the automatically generated token to allow for authorization on other domains.
{% endhint %}

### Where to find tokens?

Select **Settings** in the left menu, then API Tokens. You’ll see all active tokens, their creator, and their access level.&#x20;

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/image (42).png" alt="" width="563"><figcaption></figcaption></figure></div>

The automatically assigned token per domain is under the Integration tab in Sending Domains. Choose the desired stream, click Integrate, and toggle the switch to API. You'll see the endpoint (Host) and your API Token.

### Reset token

Go to **Settings** > **API Tokens**, click the three-dot menu icon next to the token you want to reset, and click **Reset API Token**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/api-tokens-reset-menu-option.png" alt="" width="563"></div>

Confirm your choice by clicking on the corresponding button.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/api-tokens-reset-confirmation.png" alt="" width="563"></div>

{% hint style="success" %}
**Tip:** The three-dot menu icon next to the token also allows you to copy a token to your clipboard.
{% endhint %}

{% hint style="warning" %}
**Important notes:**

* After clicking the Reset credentials or Reset API Token buttons, the existing token becomes invalid after 12 hours. So, you have a 12-hour window to update all apps that use the old API token. Once the old token expires, some parts of your application will not work properly unless you've updated the token. All expired tokens get deleted from your account within 24 hours after expiration.
* After the API token is reset and expired, a new token is created. The token ID is added to the token name the same way it's done for automatically generated tokens, e.g., mailtrap.example token 4231.
{% endhint %}

### Edit permissions

As mentioned earlier, click the menu icon at the far right of a token and select **Edit permissions**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/api-tokens-edit-permissions-option.png" alt="" width="563"></div>

Click on the corresponding boxes to add or remove token permissions. Then, confirm your selection with the **Save** button.

### Delete token

To delete a token, click a three-dot menu icon and choose the **Delete** **token** option.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/api-tokens-delete-menu-option.png" alt="" width="563"></div>

Confirm the action by clicking the **Confirm** button.

<div data-with-frame="true"><img src="../../.gitbook/assets/api-tokens-delete-confirmation.png" alt=""></div>

{% hint style="warning" %}
**Important:** Keep in mind that a token is deleted immediately, and you can't delete the last token per domain.
{% endhint %}

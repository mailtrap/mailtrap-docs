---
title: API Tokens
description: >-
  Learn how to create, manage, and use API tokens for Email API/SMTP and Email
  Sandbox
---

# 🔑 API Tokens

### Mailtrap Email API/SMTP

#### Add and manage tokens manually

Navigate to Settings in the menu on the left and select API Tokens.

![API Tokens settings page showing list of tokens with Name, Created By, Access, and Token columns](.gitbook/assets/api-tokens-settings-page.png)

To add a new token, click the Add Token button in the upper right corner.

![API Tokens page with arrow pointing to the Add Token button in upper right corner](.gitbook/assets/api-tokens-add-token-button.png)

Type the token name into the designated field. It’s perfectly fine to have a custom name for the API token, as it’s only for your reference, regardless of the use case.

Then, assign permissions by checking the boxes in the corresponding access level columns. Note that you must have admin permissions on a particular domain to send emails with this token.

![Token permissions editor showing different access levels for Account, Billing, Email Sending, and other resources](.gitbook/assets/api-tokens-permissions-editor.png)

Click the Save button and preview the new token under the API Tokens main menu.

#### Auto-created token per domain

When you create a domain, a token is automatically created and named based on the following formula: \[domain name] + \[token] + \[token ID].

For example, if you add the example.com domain, the token for that domain will be named example.com token 1234. By default, the automatically generated token gets Domain Admin Mailtrap for the given domain.

Note: You'll need to edit permissions for the automatically generated token to allow for authorization on other domains.

#### Where to find tokens?

**API Integration**

The automatically assigned token per domain is under the Integration tab in Sending Domains. Choose the desired stream, click Integrate, and toggle the switch to API. You'll see the endpoint (Host) and your API Token.

![API integration credentials showing Transactional and Bulk Stream options with Host and API Token fields](.gitbook/assets/api-integration-credentials-streams.png)

**SMTP Integration**

The automatically assigned token per domain is under the Integration tab in Sending Domains. Choose the desired stream, click Integrate, and toggle the switch to SMTP. SMTP password is the same as the API Token.

![SMTP integration credentials showing Transactional and Bulk Stream options with Host, Port, Username, and Password fields](.gitbook/assets/smtp-integration-credentials-streams.png)

### Email Sandbox

The guidelines assume that you've set up Email Sandbox and use the corresponding [APIv2](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/a2041e813d169-sandbox-api).

#### Where to find tokens?

Select Settings in the left menu, then API Tokens. You'll see all active tokens, their creator, and their access level.

![API Tokens settings page showing list of tokens with Name, Created By, Access, and Token columns](.gitbook/assets/api-tokens-settings-page.png)

Click the three-dot menu to the far right of the specific user token and select Edit permissions.

![Token context menu with Edit permissions option highlighted](.gitbook/assets/api-tokens-edit-permissions-menu.png)

{% hint style="info" %}
**Important Notes:**

* You can also give Account Admin access to the token and get access to all Projects, Sandboxes, and domains on that account.

<img src=".gitbook/assets/api-tokens-account-admin-access.png" alt="Sandbox token permissions showing Account Admin access checkbox selected" data-size="original">

If you want to test how it works, you need to get authenticated using your API token. Mailtrap uses Bearer Authentication, so you must pass the token under the Authorization header of your email.
{% endhint %}

### Reset token

There are two ways to reset API tokens: clicking Reset Credentials under Integration or resetting them from the API Tokens menu.

#### Resetting API tokens from the Integration menu

To reset tokens, go to the Integration tab in the Sending Domains menu and click Integrate under Transactional or Bulk Stream (depending on which tokens you want to reset). You’ll find the Reset Credentials function next to your credentials.

![Integration credentials page with Reset Credentials button highlighted](.gitbook/assets/api-tokens-reset-credentials-button.png)

Then, click Reset Credentials and confirm your choice with the Yes, Reset button.

![Reset credentials confirmation dialog asking Are you sure you want to reset credentials with Yes Reset button](.gitbook/assets/api-tokens-reset-credentials-dialog.png)

#### Resetting API Tokens from the API Tokens menu

Go to API Tokens, click the three-dot menu icon next to the token you want to reset, and click Reset API Token.

![API Tokens page with three-dot menu showing Reset API Token option](.gitbook/assets/api-tokens-reset-menu-option.png)

Confirm your choice by clicking on the corresponding button.

![Confirmation dialog asking Are you sure you want to reset this API Token with Confirm button](.gitbook/assets/api-tokens-reset-confirmation.png)

{% hint style="success" %}
**Tip:** The three-dot menu icon next to the token also allows you to copy a token to your clipboard.
{% endhint %}

{% hint style="warning" %}
**Important Notes:**

* After clicking the Reset credentials or Reset API Token buttons, the existing token becomes invalid after 12 hours. So, you have a 12-hour window to update all apps that use the old API token. Once the old token expires, some parts of your application will not work properly unless you've updated the token. All expired tokens get deleted from your account within 24 hours after expiration.
* After the API token is reset and expired, a new token is created. The token ID is added to the token name the same way it's done for automatically generated tokens, e.g., mailtrap.example token 4231.
{% endhint %}

### Edit permissions

As mentioned earlier, click the menu icon at the far right of a token and select Edit permissions.

![API Tokens page with three-dot menu showing Edit permissions option highlighted](.gitbook/assets/api-tokens-edit-permissions-option.png)

Click on the corresponding boxes to add or remove token permissions. Then, confirm your selection with the Save button.

### Delete token

To delete a token, click a three-dot menu icon and choose the Delete token option.

![API Tokens page with three-dot menu showing Delete token option highlighted](.gitbook/assets/api-tokens-delete-menu-option.png)

Confirm the action by clicking the Confirm button.

![Confirmation dialog asking Are you sure you want to remove this Api Token with Confirm button](.gitbook/assets/api-tokens-delete-confirmation.png)

{% hint style="warning" %}
**Important Note:** Keep in mind that a token is deleted immediately, and you can't delete the last token per domain.
{% endhint %}

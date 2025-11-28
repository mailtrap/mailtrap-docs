---
title: <i class="fa-microsoft">:microsoft:</i> Setup SSO with Azure (Microsoft Entra)
description: >-
  Step-by-step guide to configure SAML-based Single Sign-On between Azure Active
  Directory and Mailtrap with role mapping support.
---

# Setup SSO with Azure (Microsoft Entra)

## Overview

This guide walks you through configuring SAML-based Single Sign-On (SSO) between Azure Active Directory (Microsoft Entra) and Mailtrap.

## Configure Single Sign-On with Azure

### Create Enterprise Application

{% stepper %}
{% step %}
**Open Enterprise Applications**

Open your Azure Active Directory and select **Enterprise applications**

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-azure-1.png" alt="" width="375"></div>
{% endstep %}

{% step %}
**Add New Application**

Add new application by clicking the **+ New application** button
{% endstep %}

{% step %}
**Create Custom Application**

Choose **+ Create your own application**
{% endstep %}

{% step %}
**Name Your Application**

Enter the name of the application (e.g., "Mailtrap")
{% endstep %}

{% step %}
**Select Non-Gallery Integration**

Select **Integrate any other application you don't find in the gallery (Non-gallery)**

<div data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-azure-2.png" alt="Azure Browse gallery showing create your own application dialog with Mailtrap name and non-gallery option selected" width="563"></div>
{% endstep %}
{% endstepper %}

### Set Up Single Sign-On

After the application has been created, you can set up single sign-on:

{% stepper %}
{% step %}
**Choose Set Up Single Sign-On**

Choose **Set up single sign-on** in the **Getting Started** section

<div data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-azure-3.png" alt="Mailtrap application overview page in Azure showing Set up single sign-on option in Getting Started section"></div>
{% endstep %}

{% step %}
**Select SAML Mode**

For **Single Sign-on** mode, select **SAML** based Sign-on

<div data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-azure-4.png" alt="Azure single sign-on method selection page with SAML option highlighted"></div>

Follow the steps on the SSO with SAML screen. Azure AD has a detailed [configuration guide](https://docs.microsoft.com/en-gb/azure/active-directory/manage-apps/configure-single-sign-on-non-gallery-applications) at the top of the page for further guidance.
{% endstep %}
{% endstepper %}

### Basic SAML Configuration

Click edit in the dropdown menu and provide the following SAML Provider details to your Azure from Mailtrap:

* **Entity ID** → Identifier (Entity ID)
* **Assertion Consumer Service URL** → Reply URL (Assertion Consumer Service URL)
* **Single Logout Service URL** → Logout URL

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-azure-5.png" alt="" width="563"></div>

### User Attributes and Claims

In the User Identifier field, enter **user.mail**.

### SAML Signing Certificate

{% stepper %}
{% step %}
Click **Edit** and choose **SHA-1** Signing Algorithm
{% endstep %}

{% step %}
Click **Save**

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-azure-6.png" alt="" width="375"></div>
{% endstep %}

{% step %}
Download **Certificate (Base64)**
{% endstep %}

{% step %}
Open it in any text editor and copy its content
{% endstep %}

{% step %}
Paste the certificate content into the Mailtrap **X509 Certificate** field
{% endstep %}
{% endstepper %}

### Identity Provider Details

Provide the following to Mailtrap from Azure:

* **IdP Entity ID** (Identity Provider Issuer) → Azure AD Identifier
* **Single Sign-on URL** → Login URL
* **Optional: Single Logout Service (SLO) URL** → Logout URL

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-azure-7.png" alt="" width="563"></div>

Now you can save your SAML configuration on Mailtrap.

### Assign Users and Groups

With SAML configuration complete, you need to add users or groups to your application in Azure:

{% stepper %}
{% step %}
**Navigate to Users and Groups**

Click **Users and groups** on the left sidebar
{% endstep %}

{% step %}
**Add Users**

Click on **+ Add User → Users and Groups**
{% endstep %}

{% step %}
**Select Users**

Select all users you want to add to the application and click **Select**
{% endstep %}
{% endstepper %}

## Permissions

By default, we create users with no permissions. If you want the user to be automatically assigned to Account Admin or Account Viewer role, you need to set up the role mapping.

### Configure Role Mapping in Mailtrap

In the following example, we assign the roles depending on the **title** attribute value:

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-azure-8.png" alt="" width="375"></div>

### Configure Attributes in Azure

1. Navigate to **Attributes & Claims**

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-azure-9.png" alt="" width="563"></div>

2. Click **Add new claim**

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-azure-10.png" alt="" width="375"></div>

3. Add the **title** claim with the appropriate source attribute (e.g., **user.jobtitle**)

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-azure-11.png" alt="" width="375"></div>

4. Click **Save**

Your Azure SSO configuration with role mapping is now complete.

---
title: <i class="fa-google">:google:</i> Setup SSO with Google Workspace
description: >-
  Step-by-step guide to configure SAML-based Single Sign-On between Google
  Workspace and Mailtrap with role mapping support.
---

# Setup SSO with Google Workspace

## Overview

This guide walks you through configuring SAML-based Single Sign-On (SSO) between Google Workspace and Mailtrap.

## On Google Admin side

### Access the Apps section

{% stepper %}
{% step %}
Go to **Apps** in the **Google Admin console**

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-1.png" alt="" width="375"></div>
{% endstep %}

{% step %}
Navigate to **Web and mobile apps**

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-2.png" alt="" width="375"></div>
{% endstep %}
{% endstepper %}

### Create a custom SAML app

{% stepper %}
{% step %}
Navigate to the **Web and mobile apps** section in Google Admin.
{% endstep %}

{% step %}
Click the **Add app** dropdown button to see available app options.
{% endstep %}

{% step %}
Select **Add custom SAML app** from the dropdown menu.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-3.png" alt="" width="563"></div>
{% endstep %}
{% endstepper %}

### Copy Google identity provider details

Google will provide you with the following SAML configuration details. Copy these values to use in Mailtrap:

* **SSO URL**
* **Entity ID**
* **Certificate**

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-4.png" alt="" width="375"></div>

### Configure service provider details

Provide the following SAML Provider details to Google from Mailtrap:

* **ACS URL** → Assertion Consumer Service URL from Mailtrap
* **Entity ID** → Entity ID from Mailtrap

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-5.png" alt="" width="375"></div>

### Verify the application

After configuration, your SAML app will appear in the Web and mobile apps list:

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-6.png" alt="" width="563"></div>

### Review the configuration

You can review the service provider details and configure attribute mapping:

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-7.png" alt="" width="563"></div>

### Enable the application

Turn on the SAML app for your users:

{% stepper %}
{% step %}
Go to the **Service Status** section for your SAML app.
{% endstep %}

{% step %}
Select **ON for everyone** to enable the app for all users, or choose specific organizational units if you want to limit access.
{% endstep %}

{% step %}
Click **Save** to apply the changes and enable the application.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-8.png" alt="" width="563"></div>
{% endstep %}
{% endstepper %}

## Permissions

By default, we create users with no permissions. If you want the user to be automatically assigned to Account Admin or Account Viewer role, you need to set up the role mapping.

### Configure role mapping

In the following example, we assign the roles depending on the **Type** of employee attribute value.

#### Configure attribute mapping in Google

{% stepper %}
{% step %}
Click **SAML attribute mapping**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-9.png" alt="" width="375"></div>
{% endstep %}

{% step %}
Map the **Google Directory attribute** to the **App attribute**

* **Google Directory attributes**: Employee Details > Type
* **App attributes**: Type

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-10.png" alt="" width="563"></div>
{% endstep %}

{% step %}
Save your attribute mapping configuration.
{% endstep %}
{% endstepper %}

#### Set employee type in Google Directory

In the **Google Directory** user profile, set the **Type of employee** field (e.g., "Admin", "Viewer"):

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-11.png" alt="" width="375"></div>

#### Configure role mapping in Mailtrap

In Mailtrap SSO settings, map the **Type** attribute to the appropriate Mailtrap roles (Admin, Viewer)

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-12.png" alt="" width="563"></div>

Your Google Workspace SSO configuration with role mapping is now complete.

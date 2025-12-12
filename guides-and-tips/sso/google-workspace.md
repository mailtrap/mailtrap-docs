---
title: <i class="fa-google">:google:</i> Setup SSO with Google Workspace
description: >-
  Step-by-step guide to configure SAML-based Single Sign-On between Google
  Workspace and Mailtrap with role mapping support.
---

# Setup SSO with Google Workspace

## Overview

This guide walks you through configuring SAML-based Single Sign-On (SSO) between Google Workspace and Mailtrap.

## On Google Admin Side

### Access Apps Section

{% stepper %}
{% step %}
**Go to Apps in the Google Admin console**

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-1.png" alt="" width="375"></div>
{% endstep %}

{% step %}
**Navigate to Web and mobile apps**

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-2.png" alt="" width="375"></div>
{% endstep %}
{% endstepper %}

### Create Custom SAML App

{% stepper %}
{% step %}
**Go to Web and mobile apps**

Navigate to the **Web and mobile apps** section in Google Admin.
{% endstep %}

{% step %}
**Click Add app dropdown**

Click the **Add app** dropdown button to see available app options.
{% endstep %}

{% step %}
**Select Add custom SAML app**

Select **Add custom SAML app** from the dropdown menu.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-3.png" alt="Web and mobile apps page with Add app dropdown showing custom SAML app option" width="563"></div>
{% endstep %}
{% endstepper %}

### Copy Google Identity Provider Details

Google will provide you with the following SAML configuration details. Copy these values to use in Mailtrap:

* **SSO URL**
* **Entity ID**
* **Certificate**

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-4.png" alt="" width="375"></div>

### Configure Service Provider Details

Provide the following SAML Provider details to Google from Mailtrap:

* **ACS URL** ← Assertion Consumer Service URL from Mailtrap
* **Entity ID** ← Entity ID from Mailtrap

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-5.png" alt="" width="375"></div>

### Verify Application

After configuration, your SAML app will appear in the Web and mobile apps list:

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-6.png" alt="Web and mobile apps list showing configured SAML sandbox MT application with certificate expiration" width="563"></div>

### Review Configuration

You can review the service provider details and configure attribute mapping:

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-7.png" alt="SAML sandbox MT app overview showing service provider details and attribute mapping configuration" width="563"></div>

### Enable the Application

Turn on the SAML app for your users:

{% stepper %}
{% step %}
**Navigate to Service Status**

Go to the **Service Status** section for your SAML app.
{% endstep %}

{% step %}
**Select ON for everyone**

Select **ON for everyone** to enable the app for all users, or choose specific organizational units if you want to limit access.
{% endstep %}

{% step %}
**Click Save**

Click **Save** to apply the changes and enable the application.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-8.png" alt="SAML sandbox MT service status page with ON for everyone option selected" width="563"></div>
{% endstep %}
{% endstepper %}

## Permissions

By default, we create users with no permissions. If you want the user to be automatically assigned to Account Admin or Account Viewer role, you need to set up the role mapping.

### Configure Role Mapping

In the following example, we assign the roles depending on the **Type** of employee attribute value.

#### Configure Attribute Mapping in Google

{% stepper %}
{% step %}
**Navigate to your SAML app details**

Click **SAML attribute mapping**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-9.png" alt="" width="375"></div>
{% endstep %}

{% step %}
**Map the Google Directory attribute to the App attribute**

* **Google Directory attributes**: Employee Details > Type
* **App attributes**: Type

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-10.png" alt="SAML attribute mapping page showing Google Directory Type field mapped to App Type attribute" width="563"></div>
{% endstep %}

{% step %}
**Click Save**

Save your attribute mapping configuration.
{% endstep %}
{% endstepper %}

#### Set Employee Type in Google Directory

In the Google Directory user profile, set the **Type of employee** field (e.g., "Admin", "Viewer"):

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-11.png" alt="" width="375"></div>

#### Configure Role Mapping in Mailtrap

In Mailtrap SSO settings, configure the SAML Role Mapping:

* Map the **Type** attribute to the appropriate Mailtrap roles (Admin, Viewer)

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-google-workspace-12.png" alt="Mailtrap SAML Role Mapping configuration with Admin and Viewer roles mapped to Type attribute" width="563"></div>

Your Google Workspace SSO configuration with role mapping is now complete.

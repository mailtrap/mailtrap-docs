---
title: Setup SSO with JumpCloud
description: Step-by-step guide to configure SAML-based Single Sign-On between JumpCloud and Mailtrap with role mapping support.
---

# Overview

<i class="fa-cloud">:cloud:</i>

This guide walks you through configuring SAML-based Single Sign-On (SSO) between JumpCloud and Mailtrap.

# On JumpCloud Side

{% stepper %}
{% step %}
## Navigate to SSO and Add Application

Navigate to **SSO** in JumpCloud and click the **+** button to add new application.

![JumpCloud SSO applications page with plus button to add new application highlighted](../.gitbook/assets/setup-sso-with-jumpcloud-1.png)
{% endstep %}

{% step %}
## Select Custom SAML App

Search for **SAML** and choose **Custom SAML App**.

![JumpCloud application search showing Custom SAML App option with configure button](../.gitbook/assets/setup-sso-with-jumpcloud-2.png)
{% endstep %}

{% step %}
## Name the Application

Specify the application name and proceed to the **SSO** tab.

![JumpCloud new application general info tab showing display label and description fields](../.gitbook/assets/setup-sso-with-jumpcloud-3.png)
{% endstep %}

{% step %}
## Configure SAML Settings

Provide the following SAML Provider details to JumpCloud from Mailtrap:

- **SP Entity ID** ← Entity ID from Mailtrap
- **ACS URL** ← Assertion Consumer Service URL from Mailtrap

![Split view showing Mailtrap and JumpCloud SAML configuration fields with mapping arrows](../.gitbook/assets/setup-sso-with-jumpcloud-4.png)

Additional SAML settings:

- **SAMLSubject NameID** should be `email`
- **SAMLSubject NameID Format** leave default value
- **Signature Algorithm** leave default value
{% endstep %}

{% step %}
## Configure User Attributes (Optional)

If you want to use role mapping, specify attributes for role mapping:

![JumpCloud user attributes configuration showing service provider and JumpCloud attribute name mapping](../.gitbook/assets/setup-sso-with-jumpcloud-5.png)
{% endstep %}

{% step %}
## Activate and Download Certificate

Click **Activate**, then click **Save** after successful activation. Download the certificate from the **IDP Certificate Valid** section.

![JumpCloud SAML application status showing integration active with certificate download option](../.gitbook/assets/setup-sso-with-jumpcloud-6.png)
{% endstep %}
{% endstepper %}

# On Mailtrap Side

After configuration is ready on JumpCloud side, set up the configuration on Mailtrap side.

{% stepper %}
{% step %}
## Configure Identity Provider Details

Provide the following to Mailtrap from JumpCloud:

- **IdP Entity ID** (Identity Provider Issuer) ← IdP Entity ID from JumpCloud
- **Single Sign-on URL** ← IDP URL from JumpCloud
- **X509 Certificate** ← Value from downloaded certificate

![Split view showing Mailtrap SSO configuration fields mapped from JumpCloud settings](../.gitbook/assets/setup-sso-with-jumpcloud-7.png)
{% endstep %}

{% step %}
## Save Configuration

Click **Save** in Mailtrap SSO configuration. For role mapping, configure additional settings as described in the [SSO Guide](sso-guide.md#step-5-role-mapping).

Your SAML configuration is now complete.
{% endstep %}
{% endstepper %}

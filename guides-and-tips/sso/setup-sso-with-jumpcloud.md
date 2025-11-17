---
title: Setup SSO with JumpCloud
description: Step-by-step guide to configure SAML-based Single Sign-On between JumpCloud and Mailtrap with role mapping support.
---

# Overview

This guide walks you through configuring SAML-based Single Sign-On (SSO) between JumpCloud and Mailtrap.

# On JumpCloud Side

## Create SAML Application

1. Navigate to **SSO** in JumpCloud
2. Click the **+** button to add new application

![JumpCloud SSO applications page with plus button to add new application highlighted](../.gitbook/assets/setup-sso-with-jumpcloud-1.png)

3. Search for **SAML** and choose **Custom SAML App**

![JumpCloud application search showing Custom SAML App option with configure button](../.gitbook/assets/setup-sso-with-jumpcloud-2.png)

4. Specify the application name and proceed to the **SSO** tab

![JumpCloud new application general info tab showing display label and description fields](../.gitbook/assets/setup-sso-with-jumpcloud-3.png)

## Configure SAML Settings

Provide the following SAML Provider details to JumpCloud from Mailtrap:

- **SP Entity ID** ← Entity ID from Mailtrap
- **ACS URL** ← Assertion Consumer Service URL from Mailtrap

![Split view showing Mailtrap and JumpCloud SAML configuration fields with mapping arrows](../.gitbook/assets/setup-sso-with-jumpcloud-4.png)

Additional SAML settings:

- **SAMLSubject NameID** should be `email`
- **SAMLSubject NameID Format** leave default value
- **Signature Algorithm** leave default value

## Configure User Attributes (Optional)

If you want to use role mapping, specify attributes for role mapping:

![JumpCloud user attributes configuration showing service provider and JumpCloud attribute name mapping](../.gitbook/assets/setup-sso-with-jumpcloud-5.png)

## Activate and Download Certificate

1. Click **Activate**
2. Click **Save** after successful activation
3. Download the certificate from the **IDP Certificate Valid** section

![JumpCloud SAML application status showing integration active with certificate download option](../.gitbook/assets/setup-sso-with-jumpcloud-6.png)

# On Mailtrap Side

After configuration is ready on JumpCloud side, set up the configuration on Mailtrap side.

## Configure Identity Provider Details

Provide the following to Mailtrap from JumpCloud:

- **IdP Entity ID** (Identity Provider Issuer) ← IdP Entity ID from JumpCloud
- **Single Sign-on URL** ← IDP URL from JumpCloud
- **X509 Certificate** ← Value from downloaded certificate

![Split view showing Mailtrap SSO configuration fields mapped from JumpCloud settings](../.gitbook/assets/setup-sso-with-jumpcloud-7.png)

## Save Configuration

1. Click **Save** in Mailtrap SSO configuration
2. (Optional) For role mapping, configure additional settings as described in the [SSO Guide](sso-guide.md#step-5-role-mapping)

Your SAML configuration is now complete.

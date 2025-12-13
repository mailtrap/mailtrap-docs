---
title: <i class="fa-cloud">:cloud:</i> Setup SSO with JumpCloud
description: >-
  Step-by-step guide to configure SAML-based Single Sign-On between JumpCloud
  and Mailtrap with role mapping support.
---

# Setup SSO with JumpCloud

## Overview

This guide walks you through configuring SAML-based Single Sign-On (SSO) between JumpCloud and Mailtrap.

## On JumpCloud side

{% stepper %}
{% step %}
Navigate to **SSO** in JumpCloud and click the **+** button to add new application.

<div data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-jumpcloud-1.png" alt=""></div>
{% endstep %}

{% step %}
Search for **SAML** and choose **Custom SAML App**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-jumpcloud-2.png" alt="" width="563"></div>
{% endstep %}

{% step %}
Specify the application name and proceed to the **SSO** tab.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-jumpcloud-3.png" alt="" width="563"></div>
{% endstep %}

{% step %}
Provide the following SAML Provider details to JumpCloud from Mailtrap:

* **SP Entity ID** → Entity ID from Mailtrap
* **ACS URL** → Assertion Consumer Service URL from Mailtrap

<div data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-jumpcloud-4.png" alt=""></div>

Additional SAML settings:

* **SAMLSubject NameID** should be `email`
* **SAMLSubject NameID Format** leave default value
* **Signature Algorithm** leave default value
{% endstep %}

{% step %}
If you want to use role mapping, specify **User Attributes** for role mapping:

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-jumpcloud-5.png" alt="" width="375"></div>
{% endstep %}

{% step %}
Click **Activate**, then click **Save** after successful activation. Then, download the certificate from the **IDP Certificate Valid** section.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-jumpcloud-6.png" alt="" width="188"></div>
{% endstep %}
{% endstepper %}

## On Mailtrap side

After configuration is ready on JumpCloud side, you can set up the configuration on Mailtrap side.

{% stepper %}
{% step %}
Provide the following to Mailtrap from JumpCloud:

* **IdP Entity ID** (Identity Provider Issuer) → IdP Entity ID from JumpCloud
* **Single Sign-on URL** → IDP URL from JumpCloud
* **X509 Certificate** → Value from the downloaded certificate

<div data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-jumpcloud-7.png" alt=""></div>
{% endstep %}

{% step %}
Click **Save** in Mailtrap SSO configuration. For role mapping, configure additional settings as described in the [SSO Guide](sso-guide.md#step-5-role-mapping).

Your SAML configuration is now complete.
{% endstep %}
{% endstepper %}

---
title: <i class="fa-shield-halved">:shield-halved:</i> Setup SSO with OneLogin
description: >-
  Learn how to configure Single Sign-On (SSO) integration between Mailtrap and
  OneLogin using SAML.
---

# Setup SSO with OneLogin

## Overview

This guide walks you through setting up Single Sign-On (SSO) between Mailtrap and OneLogin using a SAML custom connector.

## On OneLogin Side

{% stepper %}
{% step %}
**Navigate to Applications**

Access the Applications section in your OneLogin admin console.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-onelogin-1.png" alt="Navigate to Applications in OneLogin admin console" width="563"></div>
{% endstep %}

{% step %}
**Search for SAML Custom Connector**

Look for "SAML custom connector" in the applications catalog.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-onelogin-2.png" alt="Search for SAML custom connector" width="563"></div>

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-onelogin-3.png" alt="Select SAML custom connector" width="563"></div>
{% endstep %}

{% step %}
**Open SAML Custom Connector Configuration**

Open the SAML custom connector configuration screen.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-onelogin-4.png" alt="SAML custom connector configuration screen" width="563"></div>
{% endstep %}

{% step %}
**Enter SSO Data from Mailtrap**

Configure the SAML connector with the SSO details provided by Mailtrap.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-onelogin-5.png" alt="Enter SSO configuration data from Mailtrap" width="563"></div>

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-onelogin-6.png" alt="Complete SAML configuration with Mailtrap details" width="563"></div>
{% endstep %}
{% endstepper %}

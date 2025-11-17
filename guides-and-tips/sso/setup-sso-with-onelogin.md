---
title: <i class="fa-shield-halved">:shield-halved:</i> Setup SSO with OneLogin
description: Learn how to configure Single Sign-On (SSO) integration between Mailtrap and OneLogin using SAML.
---

# Overview

This guide walks you through setting up Single Sign-On (SSO) between Mailtrap and OneLogin using a SAML custom connector.

# On OneLogin Side

{% stepper %}
{% step %}
## Navigate to Applications

Access the Applications section in your OneLogin admin console.

![Navigate to Applications in OneLogin admin console](<../.gitbook/assets/setup-sso-with-onelogin-1.png>)
{% endstep %}

{% step %}
## Search for SAML Custom Connector

Look for "SAML custom connector" in the applications catalog.

![Search for SAML custom connector](<../.gitbook/assets/setup-sso-with-onelogin-2.png>)

![Select SAML custom connector](<../.gitbook/assets/setup-sso-with-onelogin-3.png>)
{% endstep %}

{% step %}
## Open SAML Custom Connector Configuration

Open the SAML custom connector configuration screen.

![SAML custom connector configuration screen](<../.gitbook/assets/setup-sso-with-onelogin-4.png>)
{% endstep %}

{% step %}
## Enter SSO Data from Mailtrap

Configure the SAML connector with the SSO details provided by Mailtrap.

![Enter SSO configuration data from Mailtrap](<../.gitbook/assets/setup-sso-with-onelogin-5.png>)

![Complete SAML configuration with Mailtrap details](<../.gitbook/assets/setup-sso-with-onelogin-6.png>)
{% endstep %}
{% endstepper %}

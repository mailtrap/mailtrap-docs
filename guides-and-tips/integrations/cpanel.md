---
title: How to Configure Mailtrap as SMTP Relay in cPanel
description: Configure Mailtrap Email Sending as an SMTP relay (Smarthost) in cPanel using Exim mail server configuration.
---

# Overview

You can use Mailtrap Email Sending as an SMTP relay (Smarthost) in cPanel.

## Prerequisites

1. In your Mailtrap account, go to **Sending Domains** and click on the verified domain. Then, navigate to the **SMTP/API Settings** tab.
2. Locate your `/etc/exim.conf` file and open it with a text editor. You'll need root access to change the configuration settings for the Exim server.

## Configuration

Once the file is open, modify the following code blocks:

### Step 1: Authentication mechanism

The first block defines the authentication mechanism. You should change it to include Mailtrap credentials. Substitute `username` with `api` and `password` with **your SMTP password**.

{% code title="/etc/exim.conf - Authentication" %}
```
mailtrap_login:
driver = plaintext
public_name = LOGIN
client_send = : username : password
```
{% endcode %}

### Step 2: Router configuration

The second block is part of Exim's router section. It configures a route to send all outgoing emails through the Mailtrap SMTP server.

{% code title="/etc/exim.conf - Router" %}
```
send_via_mailtrap:
driver = manualroute
domains = ! +local_domains
transport = mailtrap_smtp
route_list = "* live.smtp.mailtrap.io::587 byname"
host_find_failed = defer
no_more
```
{% endcode %}

### Step 3: Transport configuration

The third block is part of Exim's transport section. It defines Mailtrap transport that will handle email delivery.

{% code title="/etc/exim.conf - Transport" %}
```
mailtrap_smtp:
driver = smtp
hosts = live.smtp.mailtrap.io
hosts_require_auth = $host_address
hosts_require_tls = $host_address
```
{% endcode %}

## Apply changes

Restart the Exim service with the following command:

```bash
$ systemctl restart exim
```

Mailtrap will now be used as your cPanel Smarthost.

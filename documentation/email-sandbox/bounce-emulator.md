---
title: Bounce Emulator
description: >-
  Learn how to test your SMTP client's behavior when the server responds with an
  error
---

# Bounce Emulator

## Constructing the address

The recipient's username should start with bounce+ and contain the response in URL-encoded form: `bounce+550+no+such+user+here@inbox.mailtrap.io` .

To create it, use [https://www.urlencoder.org](https://www.urlencoder.org/) or any other URL encoding solution.

Tip: You cannot use capital letters because email addresses are converted to lowercase by any responsible SMTP client. But you can use URL encoding to express capital letters: `bounce+550+%4Eo+such+user+here@inbox.mailtrap.io` .

## Using Bounce Emulator with an email client

Just use the inbox.mailtrap.io host with any email client or application and send an email to `bounce+451+server+unavailable@inbox.mailtrap.io` .

## Using Bounce Emulator with Sandbox

If your application is connected to Email Sandbox SMTP, send an email from the application to `bounce+454+authentication+required@anydomain.com` , and your application will receive a bounce response from the Sandbox SMTP server.

_Note: This feature does not work with API, as bounce codes are specific to SMTP._

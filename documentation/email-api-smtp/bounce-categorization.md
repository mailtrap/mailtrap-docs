---
title: Bounce Categorization
description: >-
  Understand how Mailtrap categorizes email bounces based on MX server
  responses, including bounce types, descriptions, and automatic suppression
  rules.
icon: turn-down-left
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Bounce Categorization

Mailtrap categorizes [bounces](statistics/stats-dashboard.md) based on the responses from the recipients' MX servers.

The table below lists these responses and their descriptions. It also contains information on whether these bounces cause automatic suppression.

You can find bounce categories in the app, specifically in event history in Email Logs, Webhooks payload for bounce and soft\_bounce events, and Suppressions for hard bounces.

<table><thead><tr><th width="132.73046875">Category</th><th width="156.31640625">Event name</th><th width="361.05859375">Description</th><th>Adding to Suppressions</th></tr></thead><tbody><tr><td>transientfail</td><td>Transient failure</td><td>The email encountered a temporary issue.</td><td>No</td></tr><tr><td>greylisting</td><td>Greylisting</td><td>The email was temporarily rejected by the recipient's server to determine whether the sender was legitimate or not.</td><td>No</td></tr><tr><td>badsender</td><td>Bad sender</td><td>The email was rejected because the sender's address was invalid or unrecognized.</td><td>No</td></tr><tr><td>block</td><td>Blocked</td><td>The recipient's email server blocked the email, possibly due to security policies.</td><td>No</td></tr><tr><td>content</td><td>Content issue</td><td>The email content triggered content filters and was rejected by the recipient's server.</td><td>No</td></tr><tr><td>dnsFail</td><td>DNS failure</td><td>The email could not be delivered due to issues with the DNS configuration of the recipient's domain.</td><td>No</td></tr><tr><td>generalfail</td><td>General failure</td><td>The email could not be delivered due to a general failure on the recipient's server.</td><td>No</td></tr><tr><td>other</td><td>Other</td><td>The email was bounced for an unspecified or unknown reason.</td><td>No</td></tr><tr><td>relayfail</td><td>Relay failure</td><td>The email was rejected because the server is not allowed to relay messages.</td><td>No</td></tr><tr><td>serverfail</td><td>Server failure</td><td>The email could not be delivered due to a failure on the recipient's server.</td><td>No</td></tr><tr><td>spam</td><td>Spam detected</td><td>The email was identified as spam by the recipient's mail server.</td><td>No</td></tr><tr><td>verifyfail</td><td>Verification failed</td><td>The email was rejected because the sender's or recipient's addresses could not be verified.</td><td>No</td></tr><tr><td>timeout</td><td>Timeout</td><td>The email was bounced due to an unspecified issue, probably a timeout.</td><td>Yes</td></tr><tr><td>badrecipient</td><td>Bad recipient</td><td>The email was bounced because the recipient's email address is invalid or does not exist.</td><td>Yes</td></tr><tr><td>overquota</td><td>Over quota</td><td>The recipient's mailbox is full and cannot accept new messages.</td><td>Yes</td></tr><tr><td>serverpolicy</td><td>Server policy</td><td>The email was rejected due to the recipient's server policy settings.</td><td>No</td></tr><tr><td>spam_gmail</td><td>Gmail limitation</td><td>The email bounced due to limitations from Gmail recipient due to either incorrect authentication, sudden increase of email traffic, or reputation issue</td><td>No</td></tr></tbody></table>

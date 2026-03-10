---
title: Rate Limits
description: >-
  API rate limits for Mailtrap endpoints to ensure fair usage and service
  stability
---

# Rate Limits

Mailtrap API enforces rate limits to ensure fair usage and maintain service stability for all users. Different API endpoints have different rate limiting rules based on their purpose and resource requirements.

## General Rate Limit

The following rate limit applies to all API endpoints:

| Scope             | Requests     | Time Window | Applied To    |
| ----------------- | ------------ | ----------- | ------------- |
| All API endpoints | 150 requests | 10 seconds  | Per API token |

## API-Specific Rate Limits

In addition to the general rate limit, some APIs have their own specific limits:

<table><thead><tr><th width="160">API</th><th width="159.5">Endpoint</th><th>Requests</th><th>Time Window</th><th>Applied To</th></tr></thead><tbody><tr><td><a href="https://docs.mailtrap.io/developers/promotional/contacts/contacts">Contacts API</a></td><td>All</td><td>200 requests</td><td>60 seconds</td><td>Per account</td></tr><tr><td><a href="https://docs.mailtrap.io/developers/email-sending/stats">Stats API</a></td><td>All</td><td>10 requests</td><td>60 seconds</td><td>Per account</td></tr><tr><td><a href="https://docs.mailtrap.io/developers/email-sending/suppressions">Suppressions API</a></td><td>All</td><td>10 requests</td><td>60 seconds</td><td>Per account</td></tr><tr><td><a href="https://docs.mailtrap.io/developers/email-sending/email-logs">Email Logs API</a></td><td><a href="https://docs.mailtrap.io/developers/email-sending/email-logs#get-api-accounts-account_id-email_logs">List email logs</a></td><td>60 requests</td><td>60 seconds</td><td>Per account</td></tr><tr><td><a href="https://docs.mailtrap.io/developers/email-sending/email-logs">Email Logs API</a></td><td><a href="https://docs.mailtrap.io/developers/email-sending/email-logs#get-api-accounts-account_id-email_logs-sending_message_id">Get an email log message by ID</a><br></td><td>1000 requests</td><td>60 seconds</td><td>Per account</td></tr></tbody></table>

{% hint style="warning" %}
Unless specified otherwise, for APIs with account-level limits (like Contacts, Stats, and Suppressions), all endpoints within that API share the same limit pool. For example, if you have 5 Stats API endpoints, each can be called twice per minute to stay within the 10 requests/60 seconds limit.
{% endhint %}

## Handling Rate Limits

When you exceed a rate limit, the API returns a `429 Too Many Requests` response. To handle rate limits gracefully:

1. Implement exponential backoff when receiving 429 responses
2. Distribute requests evenly over time rather than sending bursts
3. Cache responses when possible to reduce API calls

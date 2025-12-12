---
title: Rate Limits
description: API rate limits for Mailtrap endpoints to ensure fair usage and service stability
---

# Overview

Mailtrap API enforces rate limits to ensure fair usage and maintain service stability for all users. Different API endpoints have different rate limiting rules based on their purpose and resource requirements.

## General Rate Limit

The following rate limit applies to all API endpoints:

| Scope | Requests | Time Window | Applied To |
|-------|----------|-------------|------------|
| All API endpoints | 150 requests | 10 seconds | Per API token |

## API-Specific Rate Limits

In addition to the general rate limit, some APIs have their own specific limits:

| API | Requests | Time Window | Applied To |
|-----|----------|-------------|------------|
| Contacts API | 200 requests | 60 seconds | Per account |
| Stats API | 10 requests | 60 seconds | Per account |
| Suppressions API | 10 requests | 60 seconds | Per account |

{% hint style="info" %}
Stats API and Suppressions API are currently in development. Rate limits shown are planned values.
{% endhint %}

{% hint style="warning" %}
For APIs with account-level limits (like Contacts, Stats, and Suppressions), all endpoints within that API share the same limit pool. For example, if you have 5 Stats API endpoints, each can be called twice per minute to stay within the 10 requests/60 seconds limit.
{% endhint %}

## Handling Rate Limits

When you exceed a rate limit, the API returns a `429 Too Many Requests` response. To handle rate limits gracefully:

1. Implement exponential backoff when receiving 429 responses
2. Distribute requests evenly over time rather than sending bursts
3. Cache responses when possible to reduce API calls

# Static IPs for sending & webhooks

Mailtrap sends all outgoing traffic, both SMTP email delivery and webhook callbacks, from a fixed set of Mailtrap-owned IP ranges. Two IPv4 CIDR blocks cover everything: `45.158.83.0/24` and `5.181.200.0/24`.

### How it works

All SMTP sending exits through proxy instances with Elastic IPs from these ranges. Webhook traffic (audit logs, transactional events, test webhooks) routes through NAT gateways pinned to the same ranges.&#x20;

To whitelist, add these to your firewall's inbound rules:

```
# IPv4 CIDR blocks — covers both sending and webhooks
45.158.83.0/24
5.181.200.0/24

# Or, for webhooks only (specific IPs)
45.158.83.129
45.158.83.130

# Protocols
TCP — SMTP (port 25/587/465) for sending
TCP — HTTPS (port 443) for webhooks
```

{% hint style="info" %}
For automated firewall provisioning (Terraform, CloudFlare, AWS Security Groups), use the machine-readable endpoint: [https://mailtrap.io/ip-ranges.json](https://mailtrap.io/ip-ranges.json)
{% endhint %}

### When to use it

* Your webhook endpoint sits behind a firewall that blocks unknown IPs
* Your security team requires an explicit allowlist for all inbound traffic
* You're automating infrastructure and need static CIDRs for IaC templates
* You're in a regulated industry (finance, healthcare, insurance) with strict network policies

### Limitations

* IPv6 ranges are AWS-provided, not Mailtrap-owned — available on request
* Specific sending IPs may change; whitelist the full /24 range rather than individual addresses

### FAQ

<details>

<summary>Can I whitelist specific webhook IPs?</summary>

Both SMTP sending and webhooks use the same Mailtrap-owned IPv4 ranges:

* `45.158.83.0/24`
* `5.181.200.0/24`

Protocols: SMTP for sending, HTTPS for webhooks. TCP, any port.\
For IPv6 — contact support.

To automate IP retrieval, use the JSON reference: [https://mailtrap.io/ip-ranges.json](https://mailtrap.io/ip-ranges.json)

</details>

<details>

<summary>What are Mailtrap’s IP ranges for firewall whitelisting?</summary>

Yes. Add both `45.158.83.0/24` and `5.181.200.0/24` for webhook IP whitelisting. These are the same ranges used for SMTP sending, so one set of firewall rules covers everything.

To automate IP retrieval, use the JSON reference: [https://mailtrap.io/ip-ranges.json](https://mailtrap.io/ip-ranges.json)

</details>

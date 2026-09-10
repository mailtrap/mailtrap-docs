---
icon: ban
---

# Unsubscribe settings

Unsubscribe links are mandatory for bulk emails as per privacy laws. If your emails don't include an unsubscribe link, Mailtrap will add an unsubscribe footer automatically. This is what it will look like:

<figure><img src="../../.gitbook/assets/Screenshot 2026-09-10 at 17.11.37.png" alt="" width="375"><figcaption></figcaption></figure>

To add an unsubscribe link anywhere in your template, include this tag in your HTML template: `<a href="__unsubscribe_url__">unsubscribe</a>` . Mailtrap will render a clickable link in your email.

Unsubscribe footer and links are optional for transactional emails and are switched off by default.

However, if you want to, you can still add an unsubscribe footer to your transactional emails by toggling the switch On under **Transactional stream email footer** or adding an HTML tag mentioned above.

<figure><img src="../../.gitbook/assets/Screenshot 2026-09-10 at 17.13.36.png" alt=""><figcaption></figcaption></figure>

You can also mix both approaches: automatically add a footer to emails sent from one domain and do it manually (when applicable) for emails sent from another domain.

If an end-user uses an unsubscribe link, Mailtrap will reject any future emails sent to this address from this particular domain. You can quickly find all such emails in the [Email Logs](https://docs.mailtrap.io/email-api-smtp/analytics/logs) by filtering for the “reject” event.

You will still be able to email them using other domains or subdomains added to your Mailtrap account.

For that reason, it's worth having different domains or subdomains for different types of emails. This way, users can, for example, unsubscribe from your bulk or marketing messages while still receiving vital transactional messages.

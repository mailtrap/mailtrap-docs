# Unsubscribe settings - Footers & Links

Unsubscribe links are mandatory for bulk emails as per privacy laws. If your emails don't include an unsubscribe link, Mailtrap will add an unsubscribe footer automatically. This is what it will look like:

<figure><img src="../../.gitbook/assets/Screenshot 2026-09-10 at 17.11.37.png" alt="" width="375"><figcaption></figcaption></figure>

In campaigns and automation emails, the footer reads **Manage subscriptions | Unsubscribe** when at least two [Subscription Topics](../../general/suppressions-list/subscription-topics-unsubscribe-groups.md) are available for the email's sending domain. Otherwise, it has only **Unsubscribe**, as shown above. A Manage subscriptions link in your template doesn't count as an unsubscribe link: if your template has one but no unsubscribe link, Mailtrap still adds the footer, with **Unsubscribe** only.

To add an unsubscribe link anywhere in your template, include this tag in your HTML template: `<a href="__unsubscribe_url__">unsubscribe</a>` . Mailtrap will render a clickable link in your email.

In campaigns and automation emails, you can also link the recipient's preferences with `<a href="__manage_subscriptions_url__">Manage subscriptions</a>`. See [Manage subscriptions link](#manage-subscriptions-link) below for when Mailtrap shows it.

Unsubscribe footer and links are optional for transactional emails and are switched off by default.

However, if you want to, you can still add an unsubscribe footer to your transactional emails by toggling the switch On under **Transactional stream email footer** or adding the `__unsubscribe_url__` tag mentioned above.

<figure><img src="../../.gitbook/assets/Screenshot 2026-09-10 at 17.13.36.png" alt=""><figcaption></figcaption></figure>

You can also mix both approaches: automatically add a footer to emails sent from one domain and do it manually (when applicable) for emails sent from another domain.

If an end-user uses an unsubscribe link, Mailtrap will reject any future emails sent to this address from this particular domain. You can quickly find all such emails in the [Email Logs](https://docs.mailtrap.io/email-api-smtp/analytics/logs) by filtering for the “reject” event.

You will still be able to email them using other domains or subdomains added to your Mailtrap account.

For that reason, it's worth having different domains or subdomains for different types of emails. This way, users can, for example, unsubscribe from your bulk or marketing messages while still receiving vital transactional messages.

## Manage subscriptions link <a href="#manage-subscriptions-link" id="manage-subscriptions-link"></a>

In campaigns and automation emails, you can link the recipient's **Manage subscriptions** page, where they choose which [Subscription Topics](../../general/suppressions-list/subscription-topics-unsubscribe-groups.md) they want to receive. Include this tag in your HTML template: `<a href="__manage_subscriptions_url__">Manage subscriptions</a>`, or select **Manage subscriptions** from the drag & drop editor's link options. Default Mailtrap email templates include both links as **Manage subscriptions | Unsubscribe**.

Mailtrap keeps the link only when at least two Subscription Topics are available for the email's sending domain, including topics assigned to All domains. Otherwise, it removes the link from the email, together with one separator next to it (such as `|`), so **Manage subscriptions | Unsubscribe** becomes **Unsubscribe**. Live Sending emails have no Subscription Topic, so the link is always removed from them. In the plain-text version, where links can't be removed, a removed link opens the unsubscribe page instead.

Opening the Manage subscriptions page changes nothing until the recipient clicks **Save**. A saved topic preference applies to every sending domain the topic is available for.

Unlike topic preferences, the unsubscribe links in campaigns and automation emails (`__unsubscribe_url__`, the footer's **Unsubscribe**, and the `List-Unsubscribe` header) unsubscribe the recipient from all marketing emails from the domain, whatever the email's Subscription Topic.

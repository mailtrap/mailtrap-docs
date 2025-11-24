---
title: Excluding Specific Links from Tracking
description: >-
  Learn how to exclude specific links from tracking using the data-mt-no-track
  attribute to preserve app deeplinks and sensitive URLs.
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

# Excluding Links from Tracking

By default, when link tracking is enabled for a domain, Mailtrap rewrites links in your emails to add tracking redirects. However, in some cases you may want to exclude certain links (such as app deeplinks or sensitive URLs) from being tracked.

### How to Disable Tracking for a Specific Link

To prevent a link from being tracked, add the special attribute `data-mt-no-track` to your `<a>` tag in the HTML body of the email.

```html
<a data-mt-no-track href="https://example.com/deeplink">Open in App</a>
```

When this attribute is present:

* The link in the HTML body will not be replaced with a tracking redirect.
* If the same link also exists in the Text body of your email, it will also remain untouched (not rewritten).

### Notes

* This works on a per-link basis - all other links without the attribute will still be tracked.
* The attribute must be included in the HTML body. If the identical URL also appears in the Text body, it will inherit the no-track behavior.
* Use this for app deeplinks or any URL where tracking redirects could break functionality.

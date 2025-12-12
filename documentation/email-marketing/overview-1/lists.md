---
description: Organize contacts into targeted groups for effective email campaigns
icon: list
---

# Lists

Lists are static groups of contacts that help you organize your audience for targeted email campaigns. Unlike segments, lists don't update automatically - contacts must be manually added or removed.

## Understanding Lists

{% hint style="info" %}
**Lists vs. Segments**

* **Lists**: Static groups that you manually manage
* **Segments**: Dynamic groups that update automatically based on criteria

Use lists for stable groups (e.g., "Newsletter Subscribers") and segments for criteria-based targeting (e.g., "Active in last 30 days").
{% endhint %}

## Creating Lists

### Quick Create

{% stepper %}
{% step %}
**Navigate to Lists**

Go to **Contacts** → **Lists** in your dashboard.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-lists-create-button.png" alt="Create List button in the Lists interface" width="563"></div>
{% endstep %}

{% step %}
**Create New List**

Click **Create List** to open the creation dialog.
{% endstep %}

{% step %}
**Name Your List**

Enter a descriptive name for your list.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-lists-create-form.png" alt="Form to enter new list name" width="563"></div>

{% hint style="warning" %}
List names must be unique. You cannot create duplicate list names.
{% endhint %}
{% endstep %}

{% step %}
**Save List**

Click **Create** to save your new list.

Your list is now ready to receive contacts.
{% endstep %}
{% endstepper %}

### List Creation During Import

You can also create lists while importing contacts:

{% code title="Import Flow" %}
```
1. Upload CSV → 2. Map Fields → 3. Create New List → 4. Add Contacts
```
{% endcode %}

## Managing Lists

Access all your lists from **Contacts** → **Lists**:

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-lists-manage.png" alt="Lists management page showing all created lists" width="563"></div>

### List Actions

{% tabs %}
{% tab title="View Contacts" %}
**See all contacts in a list**

* Click on list name
* View contact count
* Filter within list
* Export list members
{% endtab %}

{% tab title="Rename List" %}
**Change list name**

* Click rename icon
* Enter new name
* Ensure uniqueness
* Save changes
{% endtab %}

{% tab title="Delete List" %}
**Remove list permanently**

* Click delete icon
* Confirm deletion
* Contacts remain in database
* Only list association removed

{% hint style="info" %}
Deleting a list doesn't delete the contacts, only their association with that list.
{% endhint %}
{% endtab %}

{% tab title="Merge Lists" %}
**Combine multiple lists**

* Select source lists
* Choose destination
* Remove duplicates
* Preserve all contacts
{% endtab %}
{% endtabs %}

## Adding Contacts to Lists

### Methods Overview

{% tabs %}
{% tab title="During Import" %}
Add contacts to lists while uploading CSV files:

* Select existing lists
* Create new lists on the fly
* Add to multiple lists at once
{% endtab %}

{% tab title="Individual Add" %}
Add single contacts from contact details:

1. Open contact profile
2. Click "Add to Lists"
3. Select target lists
4. Save changes
{% endtab %}

{% tab title="Bulk Add" %}
Add multiple contacts at once:

1. Select contacts in grid
2. Choose "Add to Lists"
3. Pick destination lists
4. Confirm action
{% endtab %}

{% tab title="API Integration" %}
Programmatically add contacts:

```javascript
{
  "email": "user@example.com",
  "lists": ["list_id_1", "list_id_2"]
}
```
{% endtab %}
{% endtabs %}

## List Best Practices

{% hint style="success" %}
**Effective List Management**

1. **Naming Convention**: Use clear, consistent names (e.g., "2024-Q1-Newsletter")
2. **Regular Maintenance**: Review and clean lists quarterly
3. **Documentation**: Note list purpose and criteria
4. **Size Limits**: Keep lists under 50,000 for optimal performance
5. **Avoid Duplication**: Use segments for criteria-based filtering
{% endhint %}

## List Strategies

### Welcome Series Lists

{% stepper %}
{% step %}
**Create Onboarding Lists**

* Day 1 Welcome
* Day 3 Follow-up
* Week 1 Check-in
* Day 30 Milestone
{% endstep %}

{% step %}
**Automate Movement**

Use API or integrations to move contacts through lists based on timeline.
{% endstep %}

{% step %}
**Track Progress**

Monitor engagement at each stage to optimize onboarding.
{% endstep %}
{% endstepper %}

### A/B Testing Lists

Split your audience for testing:

{% code title="Test Structure" %}
```
Main List: Newsletter Subscribers (10,000)
├── Test Group A (2,500) - Subject Line A
├── Test Group B (2,500) - Subject Line B
└── Remainder (5,000) - Winning Version
```
{% endcode %}

### Suppression Lists

Create lists for contacts to exclude:

* Competitors
* Internal emails
* Bounced addresses
* Complaint/spam reporters
* Do not contact

## List Performance Metrics

### Key Indicators

{% tabs %}
{% tab title="Growth Rate" %}
**Track list expansion**

```
Monthly Growth = (New - Removed) / Total × 100
```

Healthy growth: 2-5% monthly
{% endtab %}

{% tab title="Engagement Score" %}
**Measure list quality**

```
Engagement = (Opens + Clicks) / Sent × 100
```

Good engagement: >25% open rate
{% endtab %}

{% tab title="Churn Rate" %}
**Monitor list health**

```
Churn = Unsubscribes / Total × 100
```

Acceptable churn: <2% per campaign
{% endtab %}

{% tab title="List Overlap" %}
**Identify redundancy**

```
Overlap = Shared Contacts / Smaller List × 100
```

Consider merging if >70% overlap
{% endtab %}
{% endtabs %}

## Advanced List Management

### Dynamic List Updates

Use webhooks to automatically update lists:

{% code title="Webhook Example" %}
```json
{
  "event": "user.signup",
  "action": "add_to_list",
  "list_id": "new_users_2024",
  "contact": {
    "email": "user@example.com",
    "signup_date": "2024-01-20"
  }
}
```
{% endcode %}

### List Segmentation

Combine lists with segments for powerful targeting:

{% code title="Combined Targeting" %}
```
List: "Premium Customers"
  + Segment: "Opened Last Campaign"
  + Filter: "Location = USA"
  = Targeted Campaign Group
```
{% endcode %}

## List Limits and Quotas

{% hint style="info" %}
**Technical Specifications**

* **Lists per account**: Unlimited
* **Contacts per list**: No hard limit (recommend <50,000)
* **List name length**: 100 characters
* **Bulk operations**: 1,000 contacts at once
* **API rate limits**: 100 requests/minute
{% endhint %}

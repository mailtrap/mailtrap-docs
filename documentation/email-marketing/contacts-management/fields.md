---
title: Custom Fields
description: >-
  Create and manage custom fields to store additional contact information for
  personalization
icon: table-columns
---

# Custom Fields

Custom fields allow you to store additional information about your contacts beyond their email address. Use these fields to personalize campaigns and create targeted segments.

## Understanding Custom Fields

{% hint style="info" %}
**What are Custom Fields?** Custom fields are variables that store specific information about your contacts, such as:

* Personal details (first name, last name, birthday)
* Geographic information (city, country, timezone)
* Preferences (product interests, communication frequency)
* Custom data specific to your business
{% endhint %}

## Default Fields

Every contact in Mailtrap has these default fields:

{% tabs %}
{% tab title="Email (Required)" %}
**Primary identifier for contacts**

* Automatically created
* Cannot be deleted or modified
* Must be unique across your account
* Used for sending campaigns
{% endtab %}

{% tab title="Subscription Status" %}
**Tracks consent and engagement**

* Subscribed
* Unsubscribed
* Pending (awaiting confirmation)
{% endtab %}
{% endtabs %}

## Creating Custom Fields

{% stepper %}
{% step %}
### Navigate to Fields

Go to **Contacts** → **Fields** in your Mailtrap dashboard.

<div align="left"><img src="../../.gitbook/assets/marketing-contacts-fields-menu.png" alt="Contacts menu showing Fields tab" width="563"></div>
{% endstep %}

{% step %}
### Click Create Field

Select the **Create Field** button to open the field creation form.

<div align="left"><img src="../../.gitbook/assets/marketing-contacts-create-field-button.png" alt="Create Field button in the fields interface" width="375"></div>
{% endstep %}

{% step %}
### Configure Field Properties

Fill in the field details:

* **Field Name**: Display name (e.g., "First Name")
* **Type**: Select the appropriate data type
* **Merge Tag**: Variable for personalization (e.g., `first_name`)

<div align="left"><img src="../../.gitbook/assets/marketing-contacts-field-form.png" alt="Form to create a new contact field with name, type, and merge tag inputs" width="375"></div>

{% hint style="warning" %}
**Merge Tag Format** Use underscores for multi-word merge tags (e.g., `last_name`, `date_of_birth`)
{% endhint %}
{% endstep %}

{% step %}
### Save Your Field

Click **Create** to add the field to your account.

<div align="left"><img src="../../.gitbook/assets/marketing-contacts-fields-list.png" alt="List of created contact fields including name and email" width="563"></div>
{% endstep %}
{% endstepper %}

## Field Types

Choose the appropriate field type based on your data:

{% tabs %}
{% tab title="Text" %}
**For short text values**

* Names, titles, company names
* Short descriptions
* Single-line inputs
* Maximum 255 characters

Example: `first_name`, `company`, `job_title`
{% endtab %}

{% tab title="Number" %}
**For numeric values**

* Age, scores, counts
* Integers and decimals
* Mathematical operations in segments

Example: `age`, `purchase_count`, `loyalty_points`
{% endtab %}

{% tab title="Date" %}
**For date and time values**

* Birthdays, anniversaries
* Registration dates
* Last activity timestamps
* Format: YYYY-MM-DD

Example: `birthday`, `registration_date`, `last_purchase`
{% endtab %}

{% tab title="Boolean" %}
**For yes/no values**

* Preferences and flags
* Subscription statuses
* Feature toggles
* Values: true/false

Example: `is_vip`, `newsletter_subscriber`, `has_purchased`
{% endtab %}

{% tab title="List" %}
**For predefined options**

* Categories, segments
* Multiple choice values
* Dropdown selections

Example: `product_interest`, `customer_tier`, `preferred_language`
{% endtab %}
{% endtabs %}

## Using Fields in Campaigns

### Personalization with Merge Tags

Use merge tags to personalize your email content:

{% code title="Example Email Template" %}
````

</div>

### Dynamic Content

Create conditional content based on field values:

<div data-gb-custom-block data-tag="code" data-title='Conditional Content Example'>
```liquid
{% if preferred_language == "Spanish" %}
  Hola {{first_name}},
{% elsif preferred_language == "French" %}
  Bonjour {{first_name}},
{% else %}
  Hello {{first_name}},
{% endif %}
````
{% endcode %}

## Best Practices

{% hint style="success" %}
**Field Management Tips**

1. **Plan before creating**: Map out all fields you need before importing contacts
2. **Use descriptive names**: Make field names clear and intuitive
3. **Consistent naming**: Use a naming convention for merge tags
4. **Data validation**: Choose appropriate field types to ensure data quality
5. **Document usage**: Keep notes on what each field represents
{% endhint %}

## Common Use Cases

## Field Limits and Considerations

{% hint style="info" %}
**Technical Specifications**

* Maximum fields per account: Depends on your plan
* Field name length: Up to 50 characters
* Merge tag length: Up to 50 characters
* Text field value: Up to 255 characters
* Cannot delete fields with existing data
{% endhint %}

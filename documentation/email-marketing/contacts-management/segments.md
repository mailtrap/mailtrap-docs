---
title: Segments
description: Create dynamic contact groups that automatically update based on criteria
icon: filter
---

# Segments

Segments are dynamic groups of contacts that automatically update based on criteria you define. Unlike static lists, segments continuously evaluate your contacts and adjust membership as contact properties change.

## Understanding Segments

{% hint style="info" %}
**Dynamic vs. Static Groups**
- **Segments**: Automatically update based on rules and conditions
- **Lists**: Manually managed, static groups

Example: A segment for "Active Users" automatically adds contacts who opened emails in the last 30 days and removes those who haven't.
{% endhint %}

## Why Use Segments?

{% tabs %}
{% tab title="Automation" %}
**Self-maintaining groups**
- No manual updates needed
- Always current membership
- Reduces human error
- Saves time on list management
{% endtab %}

{% tab title="Precision Targeting" %}
**Complex criteria combinations**
- Multiple conditions (AND/OR)
- Behavioral targeting
- Demographic filtering
- Engagement-based grouping
{% endtab %}

{% tab title="Real-time Updates" %}
**Always accurate**
- Instant membership changes
- Reflects latest data
- No stale information
- Perfect for time-sensitive campaigns
{% endtab %}

{% tab title="Scalability" %}
**Grows with your database**
- Handles any contact volume
- Consistent rules application
- No performance degradation
- Efficient processing
{% endtab %}
{% endtabs %}

## Creating Segments

{% stepper %}
{% step %}
## Navigate to Segments
Go to **Contacts** → **Segments** in your dashboard.
{% endstep %}

{% step %}
## Click Create Segment
Select **Create Segment** to start building your dynamic group.
{% endstep %}

{% step %}
## Name Your Segment
Provide a descriptive name that clearly indicates the segment's purpose.

Example: "High-Value Customers - Last 90 Days"
{% endstep %}

{% step %}
## Define Conditions
Set up rules using:
- Contact fields
- Engagement metrics
- List membership
- Custom properties

Use AND/OR logic to combine multiple conditions.
{% endstep %}

{% step %}
## Preview Results
Review the contacts that match your criteria before saving.
{% endstep %}

{% step %}
## Save and Activate
Save your segment to start using it in campaigns.
{% endstep %}
{% endstepper %}

## Segment Builder

### Basic Conditions

{% code title="Simple Segment Example" %}
```
Condition: Email contains "@company.com"
Result: All employees
```
{% endcode %}

### Complex Conditions

{% code title="Advanced Segment Example" %}
```
(Location = "USA" OR Location = "Canada")
AND
(Last_Purchase > 30 days ago)
AND
(Total_Spent > $500)
AND
(Email_Opens > 5)
```
{% endcode %}

## Common Segment Types

### Engagement Segments

{% expand title="Highly Engaged" %}
**Most active subscribers**
```
Opened >= 5 emails in last 30 days
AND
Clicked >= 2 links in last 30 days
```

Use for:
- Premium content
- Special offers
- Beta testing invitations
{% endexpand %}

{% expand title="At Risk" %}
**Declining engagement**
```
Opened < 2 emails in last 60 days
AND
Previously opened > 5 emails
AND
Subscribed > 90 days ago
```

Use for:
- Re-engagement campaigns
- Win-back offers
- Survey requests
{% endexpand %}

{% expand title="Never Engaged" %}
**No interaction**
```
Opens = 0
AND
Subscribed > 30 days ago
```

Use for:
- Different content approach
- Preference center invitation
- Sunset policy candidates
{% endexpand %}

### Behavioral Segments

{% expand title="Recent Purchasers" %}
**Post-purchase targeting**
```
Last_Purchase < 7 days ago
```

Use for:
- Thank you messages
- Product reviews
- Cross-sell opportunities
{% endexpand %}

{% expand title="Cart Abandoners" %}
**Incomplete purchases**
```
Cart_Value > 0
AND
Last_Purchase = NULL
AND
Last_Activity < 24 hours ago
```

Use for:
- Reminder emails
- Discount offers
- Support outreach
{% endexpand %}

{% expand title="Browse Abandoners" %}
**Window shoppers**
```
Products_Viewed > 3
AND
Cart_Items = 0
AND
Last_Visit < 48 hours ago
```

Use for:
- Product recommendations
- Limited-time offers
- Educational content
{% endexpand %}

### Demographic Segments

{% expand title="Geographic Targeting" %}
**Location-based groups**
```
Country = "USA"
AND
State IN ("CA", "NY", "TX")
AND
Timezone = "PST"
```

Use for:
- Local events
- Regional offers
- Time-zone optimization
{% endexpand %}

{% expand title="Birthday Month" %}
**Celebration targeting**
```
MONTH(Birthday) = CURRENT_MONTH()
```

Use for:
- Birthday wishes
- Special discounts
- Loyalty rewards
{% endexpand %}

{% expand title="Customer Lifecycle" %}
**Tenure-based segments**
```
Account_Age > 365 days
AND
Customer_Tier = "Gold"
```

Use for:
- Loyalty programs
- Exclusive access
- Retention campaigns
{% endexpand %}

## Advanced Segmentation

### Nested Conditions

Create sophisticated segments with grouped conditions:

{% code title="Complex Nested Example" %}
```
(
  (Product_Interest = "Software" AND Job_Title CONTAINS "Developer")
  OR
  (Product_Interest = "Marketing" AND Job_Title CONTAINS "Marketing")
)
AND
(
  Company_Size > 100
  OR
  Budget > $10000
)
```
{% endcode %}

### Dynamic Date Ranges

Use relative dates for evergreen segments:

{% tabs %}
{% tab title="Rolling Windows" %}
```
Last_Activity > TODAY - 30 days
```
Always shows last 30 days of activity
{% endtab %}

{% tab title="Anniversary Dates" %}
```
Signup_Anniversary = TODAY
```
Triggers on signup date each year
{% endtab %}

{% tab title="Seasonal" %}
```
MONTH(TODAY) IN (11, 12)
```
Active during holiday season
{% endtab %}
{% endtabs %}

### Calculated Fields

Use formulas in segment criteria:

{% code title="Calculation Examples" %}
```
Average_Order_Value = Total_Revenue / Order_Count
Customer_Score = (Opens × 2) + (Clicks × 5) + (Purchases × 10)
Days_Since_Purchase = TODAY - Last_Purchase_Date
```
{% endcode %}

## Segment Performance

### Key Metrics

{% tabs %}
{% tab title="Size Tracking" %}
Monitor segment growth:
- Current member count
- Growth rate over time
- Churn from segment
- Overlap with other segments
{% endtab %}

{% tab title="Engagement Rates" %}
Track performance:
- Open rate by segment
- Click rate comparison
- Conversion metrics
- Revenue per segment
{% endtab %}

{% tab title="Update Frequency" %}
Understand dynamics:
- How often membership changes
- Average time in segment
- Entry/exit patterns
- Stability metrics
{% endtab %}
{% endtabs %}

## Segment Strategies

### Progressive Profiling

Build detailed segments over time:

{% stepper %}
{% step %}
## Start Basic
Begin with email and name only.
{% endstep %}

{% step %}
## Add Behavior
Track opens, clicks, and site visits.
{% endstep %}

{% step %}
## Gather Preferences
Use surveys and preference centers.
{% endstep %}

{% step %}
## Refine Segments
Create increasingly specific groups.
{% endstep %}
{% endstepper %}

### Lifecycle Automation

Move contacts through segments automatically:

{% code title="Customer Journey" %}
```
Prospect → Lead → Trial → Customer → Loyal → Advocate

Each stage = Different segment with specific criteria
```
{% endcode %}

## Best Practices

{% hint style="success" %}
**Effective Segmentation**
1. **Start Simple**: Begin with 3-5 basic segments
2. **Test and Learn**: Compare segment performance
3. **Document Logic**: Keep notes on segment purposes
4. **Regular Review**: Audit segments quarterly
5. **Avoid Over-Segmentation**: Balance precision with volume
6. **Use Descriptive Names**: Make purpose obvious
7. **Monitor Size**: Ensure segments aren't too small
{% endhint %}

## Combining Segments with Lists

### Hybrid Targeting

Use both for maximum flexibility:

{% code title="Combined Strategy" %}
```
Static List: "VIP Customers"
  ∩
Dynamic Segment: "Active Last 30 Days"
  =
Target Group: "Engaged VIPs"
```
{% endcode %}

### Exclusion Logic

Create suppression segments:

{% code title="Exclusion Example" %}
```
Send to: "All Subscribers"
Exclude: Segment "Purchased This Week"
Result: Non-purchasers only
```
{% endcode %}

## Technical Considerations

{% hint style="info" %}
**Segment Specifications**
- **Processing**: Real-time evaluation
- **Update frequency**: Every 15 minutes
- **Maximum conditions**: 20 per segment
- **Nesting depth**: Up to 5 levels
- **Performance**: No impact on send speed
{% endhint %}

## Troubleshooting Segments

{% expand title="Segment not updating?" %}
**Check these factors:**
- Condition syntax is correct
- Field names match exactly
- Data types are compatible
- No conflicting conditions
- Processing delay (up to 15 min)
{% endexpand %}

{% expand title="Unexpected members?" %}
**Review your logic:**
- Check AND vs OR operators
- Verify date range calculations
- Test individual conditions
- Look for NULL values
- Consider edge cases
{% endexpand %}

{% expand title="Segment too small/large?" %}
**Adjust criteria:**
- Broaden or narrow conditions
- Check for typos in values
- Verify data availability
- Test with sample contacts
- Review condition logic
{% endexpand %}

## Segment Templates

### Quick Start Templates

{% tabs %}
{% tab title="Welcome Series" %}
```
Subscribed < 7 days ago
AND
Welcome_Email_Sent = FALSE
```
{% endtab %}

{% tab title="Win-Back" %}
```
Last_Purchase > 180 days ago
AND
Previous_Customer = TRUE
```
{% endtab %}

{% tab title="Top Tier" %}
```
Lifetime_Value > $1000
OR
Purchase_Frequency > 5/year
```
{% endtab %}

{% tab title="Inactive" %}
```
Last_Open > 90 days ago
AND
Subscription_Status = "Active"
```
{% endtab %}
{% endtabs %}

## API Integration

### Creating Segments via API

{% code title="API Example" %}
```javascript
const segment = {
  name: "High Value Active",
  conditions: [
    {
      field: "lifetime_value",
      operator: "greater_than",
      value: 500
    },
    {
      field: "last_activity",
      operator: "within_days",
      value: 30
    }
  ],
  logic: "AND"
};

await api.createSegment(segment);
```
{% endcode %}

## Next Steps

<table data-view="cards">
<thead>
<tr><th></th><th></th></tr>
</thead>
<tbody>
<tr>
<td><strong>Create Your First Segment</strong><br>Start with engagement-based targeting</td>
<td><a href="#">Get Started →</a></td>
</tr>
<tr>
<td><strong>Launch Targeted Campaign</strong><br>Use segments for precision marketing</td>
<td><a href="../campaigns.md">Create Campaign →</a></td>
</tr>
<tr>
<td><strong>Analyze Performance</strong><br>Compare segment metrics</td>
<td><a href="../analytics.md">View Analytics →</a></td>
</tr>
</tbody>
</table>
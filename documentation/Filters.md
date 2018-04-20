# Filters

[Item Search API](Item_Search_Service_API.md)

## Match Filter

The **Match Filter** provides a facility for searching by a particular property and possible values.  A collection of values can be passed into this filter, making the filter act like an SQL `IN` clause.

**Match Filter Fields**

This table describes the fields that comprise the match filter:

| Field | Description | Type | Required |
| -------- | ----------- |---- | -------- |
| type   | Must be "match" | string | yes
| property | The property to run the match filter.  Supported properties listed below. | string | yes
| values | The values to match against | array | yes

**Properties supported**

Values supported can be found within the Item Data Dictionary.  These values match exactly with what is stored within the item.json format unless stated otherwise.

| Field| Description |
| -----| -------|
| itemId | The unique item id  |
| grade | The grade for the item |
| stimulusId | The associated stimulus id for an item  |
| depthOfKnowledge | Filter by depth of knowledge values |
| workflowStatus | Allows filtering by workflow statuses.   |
| itemType | Filter by item types  |
| subject | Filter by subject |
| organizationTypeId | Filter by Organization Type.  Typical values are "member", "nonMember", "vendor", "smarterBalanced" |
| primaryClaim | Filter by claim id | 
| primaryAssessmentTarget | filter by primary assessment target |
| contentTaskModel | filter by content task model |

**Example Usage**

* Find all items with a workflow status equal to "Draft":

```json
{
	"type": "match",
	"property": "workflowStatus",
	"values": ["Draft"]
}
```
* Find all items for grades 3 and 4:

```json
{
	"type": "match",
	"property": "workflowStatus",
	"values": ["3", "4"]
}
```

## Integer Range Filter

The **Integer Range Filter** allows for filtering items by a range of numbers.  By passing in a minimum and maximum number, this filter will apply an inclusive range filter on the results.  In effect, this filter acts like an SQL `BETWEEN` clause.

**Integer Range Filter Fields**

| Field | Description | Type | Required |
| -------- | ----------- |---- | -------- |
| type   | Must be "integerRange" | string | yes
| property | The property to run the integer range filter.  Supported properties listed below. | string | yes
| min | The minimum of the range | number | yes
| max | The maximum of the range | number | yes

**NOTE:** The `min` value must be smaller than the `max` value.

**Properties supported**

The integer range filter does not currently apply to any searchable properties.

**Example Usage**

* Find all items with an id between 1 and 10:

```json
{
    "type": "integerRange",
    "property": "id",
    "min": 1,
    "max": 10
}
```

## Number of Days in Range Filter

The **Number of Days in Range** filter allows searching for items with a property that has a date older than a number of days ago.  This filter can be used in two ways:

* property date is older than _X_ number of days ago
* property date is older than _X_ number of days ago but newer than _Y_ number of days ago

_**Additional Notes**_

* The `min` value must be smaller than the `max` value.
* The `min` value can be set to 0, which is effectively telling the filter to find everything older than today.

**Number of Days in Range Filter Fields**

| Field | Description | Type | Required |
| -------- | ----------- |---- | -------- |
| type   | Must be "daysRange" | string | yes
| property | The property to run the number of days range filter.  Supported properties listed below. | string | yes
| min | The minimum number of days an item must be in a status | number | yes
| max | The maximum number of days in the item must be in a status | number | no

**Properties supported**

| Field| Description |
| -----| -------|
| workflowStatusSetAt  | The date/time when an item's workflow status changed  |

**Example Usage**

* Find all items with a workflow status date that is at least five days old:

```json
{
	"type": "daysRange",
	"property": "workflowStatusSetAt",
	"min": 5
}
```

* Find all items with a workflow status between five and ten days old:

```json
{
	"type": "daysRange",
	"property": "workflowStatusSetAt",
	"min": 5,
	"max": 10
}
```

* Find all items with a workflow status date that was changed exactly five days ago:

```json
{
	"type": "daysRange",
	"property": "workflowStatusSetAt",
	"min": 5,
	"max": 5
}
```

* Find all items with a workflow status date that was changed today:

```json
{
	"type": "daysRange",
	"property": "workflowStatusSetAt",
	"min": 0,
	"max": 0
}
```
## Boolean Filter
This filter does an exact match against supported boolean/flag fields

**Boolean Filter Fields**

This table describes the fields that comprise the match filter:

| Field | Description | Type | Required |
| -------- | ----------- |---- | -------- |
| type   | Must be "booleanFlag" | string | yes
| property | The property to run the boolean filter.  Supported properties listed below. | string | yes
| value | `true` or `false` | boolean | yes

**Properties supported**

Values supported can be found within the Item Data Dictionary.  These values match exactly with what is stored within the item.json format unless stated otherwise.

| Field| Description |
| -----| -------|
| beingCreated | `true` means the item is in the process of being created but has not been added to the item bank.  |

**Example Usage**

* Find all items with a workflow status equal to "Draft":

```json
{
	"type": "booleanFlag",
	"property": "beingCreated",
	"value": true
}
```

## Contains Filter

The **Contains Filter** allows searching for items where the property's value matches any part of the value(s) passed in.  When multiple values are passed in, the values will be `OR`ed together.  For example, if "abc" and "def" are passed in as a `contains` filter's `values`, the search will look for any items that has "abc" OR "def" anywhere in the property's value.  In effect, this filter acts like an SQL `LIKE` clause.

_**Additional Notes**_

* This filter is case-insensitive: providing "abc" will match "abc", "ABC" and/or "aBc"

**Contains Filter Fields**

| Field | Description | Type | Required |
| -------- | ----------- |---- | -------- |
| type   | Must be "contains" | string | yes
| property | The property to run the number of days range filter.  Supported properties listed below. | string | yes
| values | A collection of possible values to search for | array | yes

**Properties supported**

| Field| Description |
| -----| -------|
| organizationName  | The name of the organization assigned to an item |

**Example Usage**

* Find all items with an organization name that contains "abc" somewhere in its value:

```json
{
	"type": "contains",
	"property": "organizationName",
	"values": ["abc"]
}
```

* Find all items with an organization name that contains "abc" or "def" somewhere in its value:

```json
{
	"type": "contains",
	"property": "organizationName",
	"values": ["abc", "def"]
}
```
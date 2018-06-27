# Filters

[Item Search API](Item_Search_Service_API.md)

## Match Filter

The **Match Filter** provides a facility for searching by a particular property and possible values.  A collection of values can be passed into this filter, making the filter act like an SQL `IN` clause.

**Match Filter Fields**

This table describes the fields that comprise the match filter:

| Field | Description | Type | Required |
| -------- | ----------- |---- | -------- |
| property | The property to run the match filter.  Supported properties listed below. | string | yes
| values | The values to match against | array | yes

**Properties supported**

Values supported can be found within the Item Data Dictionary.  These values match exactly with what is stored within the item.json format unless stated otherwise.

| Field| Description |
| -----| -------|
| id | The unique item id  |
| intendedGrade | The grade for the item |
| stimulusId | The associated stimulus id for an item  |
| depthOfKnowledge | Filter by depth of knowledge values |
| workflowStatus | Allows filtering by workflow statuses.   |
| type | Filter by item types  |
| subject | Filter by subject |
| organizationTypeId | Filter by Organization Type.  Typical values are "member", "nonMember", "vendor", "smarterBalanced" |
| primaryClaim | Filter by claim id | 
| primaryTarget | filter by primary target |
| secondaryClaim | Filter by secondary claim id | 
| secondaryTarget | filter by secondary target |
| tertiaryClaim | Filter by tertiary claim id | 
| tertiaryTarget | filter by tertiary target |
| quaternaryClaim | Filter by quaternary claim id | 
| quaternaryTarget | filter by quaternary target |
| contentTaskModel | filter by content task model |
| isAslRequired | filter by ASL content requirement |
| isAslProvided | filter by whether ASL content has been provided |
| isBrailleRequired | filter by Braille content requirement |
| isBrailleProvided | filter by whether Braille content has been provided |
| isClosedCaptioningRequired | filter by closed-captioning content requirement |
| isCloseCaptioningProvided | filter by whether closed-captioning has been provided |
| isTranslationRequired | filter by Translation content requirement |
| isTranslationProvided | filter by whether Translation content has been provided |
| isVisualTTSRequired | filter by Text-to-Speech content requirement |
| formType | filter by the form type on an item's forms |
| assessmentType | filter by the asssessment type on an item's forms |

**Example Usage**

* Find all items with a workflow status equal to "Draft":

```json
{
	"property": "workflowStatus",
	"values": ["Draft"]
}
```
* Find all items for grades 3 and 4:

```json
{
	"property": "workflowStatus",
	"values": ["3", "4"]
}
```

## Integer Range Filter

The **Integer Range Filter** allows for filtering items by a range of numbers.  By passing in a minimum and maximum number, this filter will apply an inclusive range filter on the results.  In effect, this filter acts like an SQL `BETWEEN` clause.

**Integer Range Filter Fields**

| Field | Description | Type | Required |
| -------- | ----------- |---- | -------- |
| property | The property to run the integer range filter.  Supported properties listed below. | string | yes
| min | The minimum of the range | number | no, if max is supplied
| max | The maximum of the range | number | no, if min is supplied

**NOTE:** The `min` value must be smaller than the `max` value.  

**Properties supported**

| Field| Description |
| -----| -------|
| calculatedFormCount | Count of all forms associated with an item |
| calculatedExposuresCount | All exposures across all forms |
| itemDifficultyQuintile | The difficulty level of the item |
| daysInWorkflowStatus | The number of days an item has been in the currently workflow status |

**Example Usage**

* Find all items with an calculated form count between 1 and 10:

```json
{
    "property": "calculatedFormCount",
    "min": 1,
    "max": 10
}
```

## Boolean Filter
This filter does an exact match against supported boolean/flag fields

**Boolean Filter Fields**

This table describes the fields that comprise the match filter:

| Field | Description | Type | Required |
| -------- | ----------- |---- | -------- |
| property | The property to run the boolean filter.  Supported properties listed below. | string | yes
| value | `true` or `false` | boolean | yes

**Properties supported**

Values supported can be found within the Item Data Dictionary.  These values match exactly with what is stored within the item.json format unless stated otherwise.

| Field| Description |
| -----| -------|
| isBeingCreated | `true` means the item is in the process of being created but has not been added to the item bank.  |
| isVisualTTSProvided | `true` means the item's Text-to-Speech visual content has been provided |
| isSightTTSProvided | `true` means the item's Text-to-Speech sight-related content has been provided |

**Example Usage**

* Find all items with a workflow status equal to "Draft":

```json
{
	"property": "isBeingCreated",
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
| property | The property to run the number of days range filter.  Supported properties listed below. | string | yes
| values | A collection of possible values to search for | array | yes

**Properties supported**

| Field| Description |
| -----| -------|
| organizationName  | The name of the organization assigned to an item |
| itemAuthor  | The item author for the item.  This is the ItemAuthor field as defined in the IDD |
| createdBy  | The Gitlab user that created the item |

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

## Date Range Filter

The **Date Range Filter** allows for filtering items by a range of dates.  In effect, this filter acts like an SQL `BETWEEN` clause for timestamps.

**Date Range Filter Fields**

| Field | Description | Type | Required |
| -------- | ----------- |---- | -------- |
| property | The property to run the date range filter.  Supported properties listed below. | string | yes
| from | The "from" date in UTC | time | no
| to | The "to" date in UTC | time | no

**Date Range Filter Behavior**

* If the `from` date is provided but the `to` date is not, the filter will effectively be `my_date >= fromDate`
* If the `to` date is provided but the `from` date is not, the filter will effectively be `my_date <= toDate`
* If the `to` date and `from` date are both provided, the filter will effectively be `my_date BETWEEN fromDate AND toDate`
* If neither the `from` date nor `to` date are provided, the filter will be ignored

**Properties supported**

| Field| Description |
| -----| -------|
| workflowStatusUpdatedDate  | The date the current worfklow status was set |
| createDate  | The date the item was created within gitlab |

* Find all items whose workflow status was updated between 4/11/2018 12AM and 4/13/2018 11:59:59 PM

```json
{
	"filters": [
		{
			"type": "dateRange",
			"property": "workflowStatusUpdatedDate",
			"from": "2018-04-11T00:00:00Z",
			"to": "2018-04-13T11:59:59Z"
		}
	],
	"sort": {
		"property": "grade",
		"direction": "asc"
	},
	"page": {
		"pageSize": 10,
		"pageNumber": 0
	}
}
```


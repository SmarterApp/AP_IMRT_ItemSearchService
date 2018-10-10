# Filters

[Item Search API](Item_Search_Service_API.md)

This page covers the available filters within the search system. The filterable fields can be found on the [Search Fields page](imrt_search_fields.md).  The table on the linked page lists each field and which filter it supports.


## Match Filter

The **Match Filter** provides a facility for searching by a particular property and possible values.  A collection of values can be passed into this filter, making the filter act like an SQL `IN` clause.

**Match Filter Fields**

This table describes the fields that comprise the match filter:

| Field | Description | Type | Required |
| -------- | ----------- |---- | -------- |
| property | The property to run the match filter.  Supported properties listed below. | string | yes
| values | The values to match against | array | yes
| includeBlanks | `true` to include items where the property is not set | no

**Example Usage**

* Find all items with a workflow status equal to "Draft":

```json
{
	"property": "workflowStatus",
	"values": ["Draft"],
	"includeBlanks" : false
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
| includeBlanks | `true` to include items where the property is not set | no

**NOTE:** The `min` value must be smaller than the `max` value.  

**Example Usage**

* Find all items with an calculated form count between 1 and 10:

```json
{
    "property": "calculatedFormCount",
    "min": 1,
    "max": 10,
    "includeBlanks" : false
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
| values | A collection of possible values to search for | array | yes |
| includeBlanks | `true` to include items where the property is not set | no |

**Example Usage**

* Find all items with an organization name that contains "abc" somewhere in its value:

```json
{
	"type": "contains",
	"property": "organizationName",
	"values": ["abc"],
	"includeBlanks": false
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
| includeBlanks | `true` to include items where the property is not set | no

**Date Range Filter Behavior**

* If the `from` date is provided but the `to` date is not, the filter will effectively be `my_date >= fromDate`
* If the `to` date is provided but the `from` date is not, the filter will effectively be `my_date <= toDate`
* If the `to` date and `from` date are both provided, the filter will effectively be `my_date BETWEEN fromDate AND toDate`
* If neither the `from` date nor `to` date are provided, the filter will be ignored

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


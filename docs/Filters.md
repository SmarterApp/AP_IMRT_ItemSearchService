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



## Keywords Filter

The **Keywords Filter** allows for filtering items by its keyword content. 
The content is culled from various item fields depending on the item type, as shown
in the following table:

**Content Sections by Item Type**

| Item Type | Fields |
| --------- | ------------|
| EQ | Prompt/Stem, Left Labels, Right Labels |  
| EBSR | Prompt/Stem, Part A Stem, Part A Options, Part B Stem, Part B Options |
| GI | Prompt/Stem |
| HTQO | Prompt/Stem, Interactive Texts |
| HTQS | Prompt/Stem, Interactive Text |
| MI | Prompt/Stem, Table Column Headers, Table Row Labels |
| MC | Prompt/Stem, Options |
| MS | Prompt/Stem, Options |
| SA | Prompt/Stem |
| TI | Prompt/Stem, Table Title, Table Column Headers, Table Cells (all types) |
| WER | Prompt/Stem |
| STIM | Content |
| TUT | Content |

*Note: each item type also includes translated content for the fields it includes.* 


**Keywords Filter Fields**

| Field | Description | Type | Required |
| -------- | ----------- |---- | -------- |
| property | The property to run the keywords filter. Supported properties listed below. | string | yes
| value | The keyword search string. Syntax for this string described below. | string | yes
| isCaseSensitive | `true` to search match the case of words in the keyword search, otherwise the search is case insensitive |true/false|no

**Keywords Filter Behavior**

| Type | Operator | Functionality |
| ---- | ---------|--------------|
| Single words| n/a | matches content containing the pattern, e.g., text matches text, texts, context, textbook|
| Multiple words| n/a | all words must appear consecutively in the content, e.g., my text matches my textbook|
|Single wildcard | _ | underscore (_) matches exactly one non-space character, e.g., te_t matches text, test, but not tet|
|Multi wildcard| \* |asterisk (\*) matches zero to many non-space characters, e.g., te*t matches tet, text, test, termagant, but not "tell them" |
|Logical AND | && | the && operator allows matching multiple words which do not have to be consecutive, e.g. good && men matches "all good men", "the men are here, which is good","for the good of all women and men"|
| Logical OR| \|\| | the \|\| operator allows matching either of two words, e.g., color || colour matches "the color gray" and "the colour grey"|
| Logical grouping | { and } | the { and } operators allow building complex logical expressions, e.g., {Tom Sawyer \|\| Huck Finn} && ~Becky Thatcher |
| Quoted String | \"" | in order to search for double quotes literally, use two double quotes, e.g., He said, ""Hi"" matches He said, "Hi" in the content. This works inside or outside quoted strings |
| Whitespace | n/a | all whitespace in the keywords filter is only significant to separate words, so words can be separated by multiple spaces, tabs, or new lines and the search will act as if they are separated a single space character| 
  
**Keyword Filter Example Usages**

* Find items with content containing the word or partial word "text"
```json
{
	"property": "keywords",
	"value": "text"
}
```

* Find items with content containing the words "my text" consecutively
```json
{
	"property": "keywords",
	"value": "my text"
}
```

* Find items with content containing te_t, where _ is any single non-space character
```json
{
	"property": "keywords",
	"value": "te_t"
}
```

* Find items with content containing te*t, where * is zero or more characters, not
crossing word boundaries
```json
{
	"property": "keywords",
	"value": "te*t"
}
```
* Find items with content containing both good and men in any order
```json
{
	"property": "keywords",
	"value": "good && men"
}
```

* Find items with content containing Tom or Dick or Harry (or some or all of these)
```json
{
	"property": "keywords",
	"value": "Tom || Dick || Harry",
	"isCaseSensitive": true
}
```

* Find items with content containing not containing Tom Sawyer
```json
{
	"property": "keywords",
	"value": "~Tom Sawyer",
	"isCaseSensitive": true
}
```

* Find items with content containing Tom Sawyer or Huck Finn, but not Becky Thatcher
```json
{
	"property": "keywords",
	"value": "{Tom Sawyer || Huck Finn} && ~Becky Thatcher",
	"isCaseSensitive": true
}
```

* Find items with content containing a special character (other than ")
```json
{
	"property": "keywords",
	"value": "\"I am about ~40 years old\"",
	"isCaseSensitive": true
}
```

* Find items with content containing double quote (")
```json
{
	"property": "keywords",
	"value": "He said, \"\"Hi\"\"",
	"isCaseSensitive": false
}
```

* Extra whitespace is not significant
```json
{
	"property": "keywords",
	"value": "English   \n   Spanish   \n  French   \n   ",
	"isCaseSensitive": true
}
```
is the same as: 
```json
{
	"property": "keywords",
	"value": "English Spanish French",
	"isCaseSensitive": true
}
```


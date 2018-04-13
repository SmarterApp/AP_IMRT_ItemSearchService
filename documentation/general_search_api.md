# General Search

[Go Back](Item_Search_Service_API.md)

This page covers the API to search items

### Supported Content Types

* `application/json`

### Search Request

Searches the imrt item bank for items.  Results are paged by defaul with a max page size of 1000 results.  Due to the size of search configurations searches leverage a POST.

The values within each filter is "OR"ed with each filter being "AND"ed together.  In the "Request Body" section below there is a discription of how this would work.

`POST /v1/items/search`

### Request Body Description
#### Filters

The property name for this is "filters".  This is an array of `filter` JSON objects describing different filters to run.

##### Match Filter

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

##### Integer Range Filter

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

##### Number of Days in Range Filter

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

#### Page

This is the `page` property in the request body below.  This drives the page configruation for the results.  This is not a required object and will default to page size of 1000 and the first page.

| Field | Description | Required | 
| -------- | ----------- | -------- |
| size   | The number of results per page. If blank each page will have 1000 records | no
| number | The page number.  This is 1 based meaning when getting the first page you should pass in number == 1| yes

#### Sort

This is the `sort` property in the request body below.  This is not required and is only needed if one wants to sort results.

| Field | Description | Required | 
| -------- | ----------- | -------- |
| property   | the property to sort.  Align with filterable properties | yes 
| order | "ASC" for ascending and "DESC" for descending | yes

### Request Body

```json
{
	"filters": [
		{
			"type": "match",
			"property": "grade",
			"values":["2","3"]
		},
		{
			"type": "integerRange",
			"property": "timeInWorkflowStatus",
			"min": 1,
			"max": 5
		}
	],
	"sort": {
		"property": "itemId",
		"order": "DESC"
	},
	"page": {
		"size": 4,
		"number": 1
	}
}
```

### Response Body

The table below describes the page information included in the response.

| Field | Description | 
| -------- | ----------- | 
| last   | True if this is the last page
| first | True if this is the first page
| totalPages | The total number of pages.  Based on page size in request
| total | Total number of results |

```json
{
  "results": [
    {
      "id": "888",
      "subject": "MATH",
      "grade": "4",
      "workflowStatus": "Draft",
      "itemType": "EQ",
      "depthOfKnowledge": "dok",
      "createdBy": "me",
      "createdAt": "2018-04-08T22:40:21.673Z",
      "standardIds": [],
      "itemDetail": null
    },
    {
      "id": "777",
      "subject": "MATH",
      "grade": "4",
      "workflowStatus": "Draft",
      "itemType": "EQ",
      "depthOfKnowledge": "dok",
      "createdBy": "me",
      "createdAt": "2018-04-08T22:40:21.673Z",
      "standardIds": [],
      "itemDetail": null
    },
    {
      "id": "666",
      "subject": "MATH",
      "grade": "4",
      "workflowStatus": "Draft",
      "itemType": "EQ",
      "depthOfKnowledge": "dok",
      "createdBy": "me",
      "createdAt": "2018-04-08T22:40:21.673Z",
      "standardIds": [],
      "itemDetail": null
    },
    {
      "id": "555",
      "subject": "MATH",
      "grade": "4",
      "workflowStatus": "Draft",
      "itemType": "EQ",
      "depthOfKnowledge": "dok",
      "createdBy": "me",
      "createdAt": "2018-04-08T22:40:21.673Z",
      "standardIds": [],
      "itemDetail": null
    }
  ],
  "last": false,
  "first": true,
  "totalPages": 2,
  "total": 7
}
```

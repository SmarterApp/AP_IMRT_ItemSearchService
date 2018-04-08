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

The property name for this is "filters".  This is an array of "filter" JSON objects describing different filters to run.

##### Match Filter

| Field | Description | Required | 
| -------- | ----------- | -------- |
| type   | Must be "match" | yes 
| property | The property to run the match filter.  Supported properties listed below. | yes
| values | The values to match against | yes

Properties supported
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

##### Integer Range Filter
| Field | Description | Required | 
| -------- | ----------- | -------- |
| type   | Must be "match" | yes 
| property | The property to run the match filter.  Supported properties listed below. | yes
| min | The minimum of the range | yes
| min | The maximim of the range | yes

Properties supported

| Field| Description |
| -----| -------|
|  |   | 


#### Page
This is the "page" property in the request body below.  This drives the page configruation for the results.  This is not a required object and will default to page size of 1000 and the first page.

| Field | Description | Required | 
| -------- | ----------- | -------- |
| size   | The number of results per page. If blank each page will have 1000 records | no
| number | The page number | yes

#### Sort
This is the "sort" property in the request body below.  This is not required and is only needed if one wants to sort results.

| Field | Description | Required | 
| -------- | ----------- | -------- |
| property   | the property to sort.  Align with filterable properties | yes 
| order | "ASC" for ascending and "DESC" for descending | yes

### Request Body

<pre>
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
</pre>

### Response Body

The table below describes the page information included in the response.

| Field | Description | 
| -------- | ----------- | 
| last   | True if this is the last page
| first | True if this is the first page
| totalPages | The total number of pages.  Based on page size in request
| total | Total number of results |

<Pre>
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
</Pre>

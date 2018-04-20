# General Search

[Go Back](Item_Search_Service_API.md)

This page covers the API to search items

### Supported Content Types

* `application/json`

### Supported Accept types

* `application/json`

### Search Request

Searches the imrt item bank for items.  Results are paged by default with a max page size of 1000 results.  Due to the size of search configurations searches leverage a POST.

The values within each filter is "OR"ed with each filter being "AND"ed together.  In the "Request Body" section below there is a discription of how this would work.

**All properties are required in requests**

`POST /v1/items/search`

### Request Body Description

#### Filters

The property name for this is "filters".  This is an array of `filter` JSON objects describing different filters to run.  If one does not want any filters simply provide an empty array.

```json
filters: []
```

Available filters can be found [here](Filters.md)

#### Page

This is the `page` property in the request body below.  This drives the page configruation for the results.  

| Field | Description | Required | 
| -------- | ----------- | -------- |
| size   | The number of results per page. The current max page IMRT is 1000 items. | yes
| number | The page number.  This is 0 based meaning when getting the first page you should pass in number == 0| yes

```json
page : {
	pageSize: 100,
	pageNumber: 0
}
```

#### Sort

This is the `sort` property in the request body below. 

| Field | Description | Required | 
| -------- | ----------- | -------- |
| property   | the property to sort.  Align with filterable properties | yes 
| direction | "asc" for ascending and "desc" for descending | yes

```json
sort : {
	property: "grade",
	direction: "asc"
}
```

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
		"direction": "desc"
	},
	"page": {
		"size": 4,
		"number": 0
	}
}
```

### Response Body

The table below describes the page information included in the response.

| Field | Description | 
| -------- | ----------- | 
| results | the data results |
| totalPages | The total number of pages.  Based on page size in request
| total | Total number of results |

```json
{
    "results": [
        {
            "id": "205238",
            "subject": "Math",
            "grade": "5",
            "workflowStatus": "Draft",
            "itemType": "mc",
            "depthOfKnowledge": "3",
            "createdBy": "A User",
            "createdAt": "2018-04-12T16:36:56Z",
            "itemDetail": null,
            "beingCreated": false,
            "organizationTypeId": "",
            "organizationName": "",
            "contentTaskModel": "123",
            "workflowStatusUpdatedAt": "2018-04-12T16:36:56Z",
            "primaryClaim": "2",
            "primaryAssessmentTarget": "Tearge",
            "primaryContentDomain": "",
            "primaryCommonCoreStandard": "",
            "secondaryClaim": "1",
            "secondaryAssessmentTarget": "",
            "secondaryContentDomain": "",
            "secondaryCommonCoreStandard": "",
            "tertiaryClaim": "",
            "tertiaryAssessmentTarget": "",
            "tertiaryContentDomain": "",
            "tertiaryCommonCoreStandard": "",
            "quaternaryClaim": "",
            "quaternaryAssessmentTarget": "",
            "quaternaryContentDomain": "",
            "quaternaryCommonCoreStandard": "",
            "daysInWorkflowStatus": 7
        }
    ],
    "last": true,
    "first": true,
    "totalPages": 1,
    "total": 1
}
```

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

`POST /v1/items/search`

### Request Body Description

#### Filters

The property name for this is "filters".  This is an array of `filter` JSON objects describing different filters to run.

Available filters can be found [here](Filters.md)

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
| direction | "ASC" for ascending and "DESC" for descending | yes

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
		"direction": "DESC"
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

# General Search

[Go Back](Item_Search_Service_API.md)

This page covers the API to search items

**Invalid or unsupported filters will result in empty responses**

### Supported Content Types

* `application/json`

### Supported Accept types

* `application/json`

### Search Request

Searches the imrt item bank for items.  Results are paged by default with a max page size of 1000 results.  Due to the size of search configurations searches leverage a POST.

The values within each filter are "OR"ed with each filter being "AND"ed together.  In the "Request Body" section below there is a discription of how this would work.

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
| pageSize   | The pageNumber of results per page. The current max page IMRT is 1000 items. | yes
| pageNumber | The page pageNumber.  This is 0 based meaning when getting the first page you should pass in pageNumber == 0| yes

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
	property: "intendedGrade",
	direction: "asc"
}
```

### Request Body

```json
{
	"filters": [
		{
			"type": "match",
			"property": "intendedGrade",
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
		"pageSize": 4,
		"pageNumber": 0
	}
}
```

### Response Body

The table below describes the page information included in the response.  The fields which have null values mean they are not yet available in IMRT.  They are placeholders which will be populated in future IMRT releases.

| Field | Description | 
| -------- | ----------- | 
| results | the data results |
| page | Object containing the pageNumber and pageSize as sent in the request |
| totalResults | Total number of results |

```json
{
    "results": [
        {
            "allowCalculator": null,
            "associatedItemCount": null,
            "closedCaptioningUploadedPriorToLastContentUpdate": null,
            "contentTaskModel": "",
            "createDate": "2018-04-13T01:38:52Z",
            "createdBy": "a user",
            "daysInWorkflowStatus": 10,
            "depthOfKnowledge": "",
            "englishContentLastUpdatedDate": null,
            "fieldTestDate": null,
            "id": "205249",
            "intendedGrade": "4",
            "isAslProvided": null,
            "isAslRequired": null,
            "isAslUploadedPriorToLastContentUpdate": null,
            "isBeingCreated": false,
            "isBrailleProvided": null,
            "isBrailleRequired": null,
            "isBrailleUploadedPriorToLastContentUpdate": null,
            "isClosedCaptioningProvided": null,
            "isClosedCaptioningRequired": null,
            "isTranslationProvided": null,
            "isTranslationRequired": null,
            "itemAuthor": "An Author",
            "itemDifficultyQuintile": null,
            "organizationName": "",
            "organizationTypeId": "",
            "performanceTask": null,
            "primaryAssessmentTarget": "ddd",
            "primaryClaim": "1",
            "primaryCommonCoreStandard": "Core?",
            "primaryContentDomain": "ReadingInformation",
            "quaternaryAssessmentTarget": "C",
            "quaternaryClaim": "1",
            "quaternaryCommonCoreStandard": "",
            "quaternaryContentDomain": "",
            "secondaryAssessmentTarget": "E",
            "secondaryClaim": "2",
            "secondaryCommonCoreStandard": "",
            "secondaryContentDomain": "",
            "stimulusId": null,
            "subject": "ELA",
            "tertiaryAssessmentTarget": "",
            "tertiaryClaim": "3",
            "tertiaryCommonCoreStandard": "",
            "tertiaryContentDomain": "",
            "testCategory": null,
            "totalExposures": null,
            "type": "mc",
            "workflowStatus": "Draft",
            "workflowStatusUpdatedDate": "2018-04-13T01:38:52Z",
            "writingPurpose": null
        }
    ],
    "totalResults": 1,
    "page": {
        "pageSize": 1000,
        "pageNumber": 0
    }
}
```

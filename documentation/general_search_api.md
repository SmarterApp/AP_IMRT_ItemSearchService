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

The table below describes the page information included in the response.  Values are currently all Strings except for dates.  Dates have the suffix `Date` on the property name.  Those can be null.  Any non date field that isn't supported will result in an empty String.

| Field | Description | 
| -------- | ----------- | 
| results | the data results |
| page | Object containing the pageNumber and pageSize as sent in the request |
| totalResults | Total number of results |

```json
{
    "results": [
        {
            "allowCalculator": "",
            "associatedItemCount": "",
            "calculatedExposuresCount": "",
            "calculatedFormCount": "",
            "contentTaskModel": "貓在樹上享受陽光Η γάτα είναι στο δέντρο απολαμβάνοντας τον ήλιοx255Chars_ThisIsALongerStringWith50CharsForTestingPurposesXxThisIsALongerStringWith50CharsForTestingPurposesXxThisIsALongerStringWith50CharsForTestingPurposesXxThisIsALongerStringWith50CharsForTestingPurposesXxThisStringHas40CharsForTestingPurposesX012345",
            "createDate": "2018-05-09T17:02:45Z",
            "createdBy": "Tess A",
            "daysInWorkflowStatus": "26",
            "depthOfKnowledge": "2",
            "englishContentLastUpdatedDate": null,
            "fieldTestDate": null,
            "id": "205461",
            "intendedGrade": "",
            "isAslProvided": "",
            "isAslRequired": "",
            "isAslUploadedPriorToLastContentUpdate": "",
            "isBeingCreated": "false",
            "isBrailleProvided": "",
            "isBrailleRequired": "",
            "isBrailleUploadedPriorToLastContentUpdate": "",
            "isClosedCaptioningProvided": "",
            "isClosedCaptioningRequired": "",
            "isClosedCaptioningUploadedPriorToLastContentUpdate": "",
            "isTranslationProvided": "",
            "isTranslationRequired": "",
            "itemAuthor": "",
            "itemDifficultyQuintile": "",
            "organizationName": "",
            "organizationTypeId": "",
            "performanceTask": "",
            "primaryClaim": "4",
            "primaryCommonCoreStandard": "",
            "primaryContentDomain": "",
            "primaryTarget": "",
            "quaternaryClaim": "",
            "quaternaryCommonCoreStandard": "",
            "quaternaryContentDomain": "",
            "quaternaryTarget": "",
            "scoringEngine": "",
            "secondaryClaim": "",
            "secondaryCommonCoreStandard": "",
            "secondaryContentDomain": "",
            "secondaryTarget": "",
            "stimulusId": "",
            "subject": "Math",
            "tertiaryClaim": "",
            "tertiaryCommonCoreStandard": "",
            "tertiaryContentDomain": "",
            "tertiaryTarget": "",
            "testCategory": "",
            "totalExposures": "",
            "type": "htqo",
            "workflowStatus": "Draft",
            "workflowStatusUpdatedDate": "2018-05-09T17:02:45Z",
            "writingPurpose": ""
        },
        {
            "allowCalculator": "",
            "associatedItemCount": "",
            "calculatedExposuresCount": "",
            "calculatedFormCount": "",
            "contentTaskModel": "tess",
            "createDate": "2018-05-16T21:48:23Z",
            "createdBy": "Tess A",
            "daysInWorkflowStatus": "19",
            "depthOfKnowledge": "4",
            "englishContentLastUpdatedDate": null,
            "fieldTestDate": null,
            "id": "205569",
            "intendedGrade": "",
            "isAslProvided": "",
            "isAslRequired": "",
            "isAslUploadedPriorToLastContentUpdate": "",
            "isBeingCreated": "false",
            "isBrailleProvided": "",
            "isBrailleRequired": "",
            "isBrailleUploadedPriorToLastContentUpdate": "",
            "isClosedCaptioningProvided": "",
            "isClosedCaptioningRequired": "",
            "isClosedCaptioningUploadedPriorToLastContentUpdate": "",
            "isTranslationProvided": "",
            "isTranslationRequired": "",
            "itemAuthor": "tessara",
            "itemDifficultyQuintile": "",
            "organizationName": "ACME",
            "organizationTypeId": "Member",
            "performanceTask": "",
            "primaryClaim": "4",
            "primaryCommonCoreStandard": "tess",
            "primaryContentDomain": "tess",
            "primaryTarget": "",
            "quaternaryClaim": "4",
            "quaternaryCommonCoreStandard": "tess",
            "quaternaryContentDomain": "tess",
            "quaternaryTarget": "",
            "scoringEngine": "",
            "secondaryClaim": "3",
            "secondaryCommonCoreStandard": "tess",
            "secondaryContentDomain": "tess",
            "secondaryTarget": "",
            "stimulusId": "",
            "subject": "Math",
            "tertiaryClaim": "2",
            "tertiaryCommonCoreStandard": "tess",
            "tertiaryContentDomain": "tess",
            "tertiaryTarget": "",
            "testCategory": "",
            "totalExposures": "",
            "type": "ms",
            "workflowStatus": "Draft",
            "workflowStatusUpdatedDate": "2018-05-16T21:48:23Z",
            "writingPurpose": ""
        },
        {
            "allowCalculator": "",
            "associatedItemCount": "",
            "calculatedExposuresCount": "",
            "calculatedFormCount": "",
            "contentTaskModel": "",
            "createDate": "2018-05-08T16:36:13Z",
            "createdBy": "Jeff Melin",
            "daysInWorkflowStatus": "27",
            "depthOfKnowledge": "",
            "englishContentLastUpdatedDate": null,
            "fieldTestDate": null,
            "id": "205434",
            "intendedGrade": "",
            "isAslProvided": "",
            "isAslRequired": "",
            "isAslUploadedPriorToLastContentUpdate": "",
            "isBeingCreated": "true",
            "isBrailleProvided": "",
            "isBrailleRequired": "",
            "isBrailleUploadedPriorToLastContentUpdate": "",
            "isClosedCaptioningProvided": "",
            "isClosedCaptioningRequired": "",
            "isClosedCaptioningUploadedPriorToLastContentUpdate": "",
            "isTranslationProvided": "",
            "isTranslationRequired": "",
            "itemAuthor": "JM QA",
            "itemDifficultyQuintile": "",
            "organizationName": "",
            "organizationTypeId": "",
            "performanceTask": "",
            "primaryClaim": "3",
            "primaryCommonCoreStandard": "",
            "primaryContentDomain": "",
            "primaryTarget": "",
            "quaternaryClaim": "",
            "quaternaryCommonCoreStandard": "",
            "quaternaryContentDomain": "",
            "quaternaryTarget": "",
            "scoringEngine": "",
            "secondaryClaim": "",
            "secondaryCommonCoreStandard": "",
            "secondaryContentDomain": "",
            "secondaryTarget": "",
            "stimulusId": "",
            "subject": "Math",
            "tertiaryClaim": "",
            "tertiaryCommonCoreStandard": "",
            "tertiaryContentDomain": "",
            "tertiaryTarget": "",
            "testCategory": "",
            "totalExposures": "",
            "type": "stim",
            "workflowStatus": "Draft",
            "workflowStatusUpdatedDate": "2018-05-08T16:36:13Z",
            "writingPurpose": ""
        },
        {
            "allowCalculator": "",
            "associatedItemCount": "",
            "calculatedExposuresCount": "",
            "calculatedFormCount": "",
            "contentTaskModel": "123456789",
            "createDate": "2018-05-09T18:00:05Z",
            "createdBy": "Tess A",
            "daysInWorkflowStatus": "26",
            "depthOfKnowledge": "2",
            "englishContentLastUpdatedDate": null,
            "fieldTestDate": null,
            "id": "205466",
            "intendedGrade": "",
            "isAslProvided": "",
            "isAslRequired": "",
            "isAslUploadedPriorToLastContentUpdate": "",
            "isBeingCreated": "false",
            "isBrailleProvided": "",
            "isBrailleRequired": "",
            "isBrailleUploadedPriorToLastContentUpdate": "",
            "isClosedCaptioningProvided": "",
            "isClosedCaptioningRequired": "",
            "isClosedCaptioningUploadedPriorToLastContentUpdate": "",
            "isTranslationProvided": "",
            "isTranslationRequired": "",
            "itemAuthor": "",
            "itemDifficultyQuintile": "",
            "organizationName": "",
            "organizationTypeId": "",
            "performanceTask": "",
            "primaryClaim": "3",
            "primaryCommonCoreStandard": "",
            "primaryContentDomain": "",
            "primaryTarget": "",
            "quaternaryClaim": "",
            "quaternaryCommonCoreStandard": "",
            "quaternaryContentDomain": "",
            "quaternaryTarget": "",
            "scoringEngine": "",
            "secondaryClaim": "",
            "secondaryCommonCoreStandard": "",
            "secondaryContentDomain": "",
            "secondaryTarget": "",
            "stimulusId": "205464",
            "subject": "Math",
            "tertiaryClaim": "",
            "tertiaryCommonCoreStandard": "",
            "tertiaryContentDomain": "",
            "tertiaryTarget": "",
            "testCategory": "",
            "totalExposures": "",
            "type": "gi",
            "workflowStatus": "Draft",
            "workflowStatusUpdatedDate": "2018-05-09T18:00:05Z",
            "writingPurpose": ""
        }
    ],
    "totalResults": 280,
    "page": {
        "pageSize": 4,
        "pageNumber": 0
    }
}
```

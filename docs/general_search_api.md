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

##### Item ID Specific Sort

This sort is different from standard sorting mechanics found in search.  This sort will sort the results in the order sent in the `id` MatchFilter.  The direction for this search must be `idOrder` and have an `id` search filter present in the request.  If either requirement is not met an invalid request response will be sent to the caller.

###### Example Search Request for Item ID Specific Sort
<pre>
{
    "filters": [
        {
            "property": "id",
            "values": ["207982", "207984", "181074"]
        }
    ],
    "sort": {
        "property": "id",
        "direction": "idFilterValues"
    },
    "page": {
        "pageSize": 150,
        "pageNumber": 0
    }
}
</pre>

### Example Request Body

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
		},
		{
			"property": "keywords",
			"value": "match && text",
			"isCaseSensitive": false
		},
		
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

### Example Response Body

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
            "id": "205585",
            "subject": "",
            "intendedGrade": "",
            "workflowStatus": "Draft",
            "type": "ebsr",
            "depthOfKnowledge": "",
            "createdBy": "DW Test",
            "createDate": "2018-05-17T22:10:37Z",
            "stimulusId": "",
            "organizationTypeId": "",
            "organizationName": "",
            "contentTaskModel": "",
            "workflowStatusUpdatedDate": "2018-05-17T22:10:37Z",
            "itemAuthor": "",
            "primaryClaim": "",
            "primaryTarget": "",
            "primaryContentDomain": "",
            "primaryCommonCoreStandard": "",
            "secondaryClaim": "",
            "secondaryTarget": "",
            "secondaryContentDomain": "",
            "secondaryCommonCoreStandard": "",
            "tertiaryClaim": "",
            "tertiaryTarget": "",
            "tertiaryContentDomain": "",
            "tertiaryCommonCoreStandard": "",
            "quaternaryClaim": "",
            "quaternaryTarget": "",
            "quaternaryContentDomain": "",
            "quaternaryCommonCoreStandard": "",
            "englishContentLastUpdatedDate": "2018-05-17T22:11:19.577Z",
            "spanishContentLastUpdatedDate": "2018-05-17T22:10:32.808Z",
            "updateDate": "2018-10-05T18:10:19.235Z",
            "fieldTestDate": null,
            "allowCalculator": "",
            "itemDifficultyQuintile": "",
            "performanceTask": "",
            "testCategory": "",
            "writingPurpose": "",
            "scoringEngine": "",
            "associatedItemCount": "0",
            "calculatedFormCount": "",
            "calculatedExposuresCount": "",
            "englishPassagesCount": "0",
            "spanishPassagesCount": "0",
            "currentUpdateNeedCreatedDate": null,
            "currentUpdateNeedResolutionDate": null,
            "currentUpdateNeedInternalResolutionDate": null,
            "currentUpdateNeedResolution": "",
            "currentUpdateNeedInternalResolution": "",
            "severeValidationResultCount": "5",
            "degradedValidationResultCount": "3",
            "tolerableValidationResultCount": "9",
            "benignValidationResultCount": "1",
            "keywordContent": "this is some matching text",
            "keywordSection": "Prompt / Stem",
            "primaryEnhancedId": "",
            "secondaryEnhancedId": "",
            "tertiaryEnhancedId": "",
            "quaternaryEnhancedId": "",
            "daysInWorkflowStatus": "145",
            "isAslRequired": "undetermined",
            "isBrailleRequired": "undetermined",
            "isClosedCaptioningProvided": "false",
            "isClosedCaptioningRequired": "undetermined",
            "isTranslationProvided": "false",
            "isTranslationRequired": "undetermined",
            "isSightTTSProvided": "false",
            "isVisualTTSProvided": "false",
            "isVisualTTSRequired": "undetermined",
            "isContentChangedAfterOperational": "false",
            "isEnglishGlossaryProvided": "false",
            "isIllustratedGlossaryProvided": "false",
            "isIllustratedGlossaryRequired": "undetermined",
            "isTranslatedGlossaryProvided": "false",
            "isTranslatedGlossaryRequired": "undetermined",
            "isBrailleProvided": "false",
            "isAslProvided": "false",
            "isBrailleUploadedPriorToLastContentUpdate": "false",
            "isClosedCaptioningUploadedPriorToLastContentUpdate": "false",
            "isBeingCreated": "false",
            "hasUnresolvedUpdateNeed": "false",
            "isAslUploadedPriorToLastContentUpdate": "false"
        },
        {
            "id": "205595",
            "subject": "",
            "intendedGrade": "",
            "workflowStatus": "Draft",
            "type": "ebsr",
            "depthOfKnowledge": "",
            "createdBy": "DW Test",
            "createDate": "2018-05-17T23:19:58Z",
            "stimulusId": "",
            "organizationTypeId": "",
            "organizationName": "",
            "contentTaskModel": "",
            "workflowStatusUpdatedDate": "2018-05-17T23:19:58Z",
            "itemAuthor": "",
            "primaryClaim": "",
            "primaryTarget": "",
            "primaryContentDomain": "",
            "primaryCommonCoreStandard": "",
            "secondaryClaim": "",
            "secondaryTarget": "",
            "secondaryContentDomain": "",
            "secondaryCommonCoreStandard": "",
            "tertiaryClaim": "",
            "tertiaryTarget": "",
            "tertiaryContentDomain": "",
            "tertiaryCommonCoreStandard": "",
            "quaternaryClaim": "",
            "quaternaryTarget": "",
            "quaternaryContentDomain": "",
            "quaternaryCommonCoreStandard": "",
            "englishContentLastUpdatedDate": "2018-05-17T23:20:16.917Z",
            "spanishContentLastUpdatedDate": "2018-05-17T23:19:52.066Z",
            "updateDate": "2018-10-05T18:09:47.355Z",
            "fieldTestDate": null,
            "allowCalculator": "",
            "itemDifficultyQuintile": "",
            "performanceTask": "",
            "testCategory": "",
            "writingPurpose": "",
            "scoringEngine": "",
            "associatedItemCount": "0",
            "calculatedFormCount": "",
            "calculatedExposuresCount": "",
            "englishPassagesCount": "0",
            "spanishPassagesCount": "0",
            "currentUpdateNeedCreatedDate": null,
            "currentUpdateNeedResolutionDate": null,
            "currentUpdateNeedInternalResolutionDate": null,
            "currentUpdateNeedResolution": "",
            "currentUpdateNeedInternalResolution": "",
            "severeValidationResultCount": "5",
            "degradedValidationResultCount": "3",
            "tolerableValidationResultCount": "9",
            "benignValidationResultCount": "1",
            "keywordContent": "this text content contains a match",
            "keywordSection": "Prompt / Stem",
            "primaryEnhancedId": "",
            "secondaryEnhancedId": "",
            "tertiaryEnhancedId": "",
            "quaternaryEnhancedId": "",
            "daysInWorkflowStatus": "145",
            "isAslRequired": "undetermined",
            "isBrailleRequired": "undetermined",
            "isClosedCaptioningProvided": "false",
            "isClosedCaptioningRequired": "undetermined",
            "isTranslationProvided": "false",
            "isTranslationRequired": "undetermined",
            "isSightTTSProvided": "false",
            "isVisualTTSProvided": "false",
            "isVisualTTSRequired": "undetermined",
            "isContentChangedAfterOperational": "false",
            "isEnglishGlossaryProvided": "false",
            "isIllustratedGlossaryProvided": "false",
            "isIllustratedGlossaryRequired": "undetermined",
            "isTranslatedGlossaryProvided": "false",
            "isTranslatedGlossaryRequired": "undetermined",
            "isBrailleProvided": "false",
            "isAslProvided": "false",
            "isBrailleUploadedPriorToLastContentUpdate": "false",
            "isClosedCaptioningUploadedPriorToLastContentUpdate": "false",
            "isBeingCreated": "false",
            "hasUnresolvedUpdateNeed": "false",
            "isAslUploadedPriorToLastContentUpdate": "false"
        }
    ],
    "totalResults": 1955,
    "page": {
        "pageSize": 2,
        "pageNumber": 0
    }
}
```

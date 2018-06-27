# IMRT Search Fields

[Go Back](Item_Search_Service_API.md)

This page covers the search result fields from IMRT.  It lists all the fields and their different usages in the IMRT application.  All fields currently come back as Strings as that is how they are stored within IAT's item.json. 

**This will be updated each time IMRT releases.  Something not searchable in a release may become searchable in the following release**

### Table Legend

| Column | Description |
| ------ | ----------- |
| Field Name | The field name in the search results.  This will always be the canonical name though casing may differ. |
| Is Filterable | Yes/No based on if the field can be used as a filter |
| Is Result Column | Yes/No based on if the field will be populated in the results  | 
| Is Count Supported | Yes/No based on if the field can be used in a count |
| Filter Type | The type of the filter based on the list of [filters](Filters.md) |


## IMRT Supported Fields

| Field Name | Is Filterable | Is Result Column | Is Count Supported | Filter Type |
| ---------- | ---------- | ------------- | --------------- | ----------- | 
| allowCalculator | No | No | No | n/a |
| associatedItemCount | No | No | No | n/a | 
| calculatedExposuresCount | Yes | Yes | No | Integer Range |
| calculatedFormCount | Yes | Yes | No | Integer Range |
| contentTaskModel | Yes | Yes | No | Match |
| createDate | Yes | Yes | No | Date Range |
| createdBy | Yes | Yes | No | contains | 
| daysInWorkflowStatus | Yes | Yes | No | IntegBooleaner Range |
| depthOfKnowledge | Yes | Yes | Yes | Match | 
| englishContentLastUpdatedDate | No | No | No | n/a |
| fieldTestDate | No | No | No | n/a |
| formType | Yes | No | No | Match |
| assessmentType | Yes | No | No | Match | 
| id | Yes | Yes | No | Match |
| intendedGrade | Yes | Yes | Yes | Match | 
| isAslProvided | Yes | Yes | No | Match |
| isAslRequired | Yes | Yes | No | Match |
| isAslUploadedPriorToLastContentUpdate | No | No | No | n/a |
| isBeingCreated | Yes | Yes | No | Boolean | 
| isBrailleProvided | Yes | Yes | No | Match |
| isBrailleRequired | Yes | Yes | No | Match |
| isBrailleUploadedPriorToLastContentUpdate | No | No | No | n/a |
| isClosedCaptioningProvided | Yes | Yes | No | Match |
| isClosedCaptioningRequired | Yes | Yes | No | Match |
| isClosedCaptioningUploaded PriorToLastContentUpdate | No | No | No | n/a |
| isTranslationProvided | Yes | Yes | No | Match |
| isTranslationRequired | Yes | Yes | No | Match |
| itemAuthor | Yes | Yes | Yes | contains |
| itemDifficultyQuintile | Yes | Yes | Yes | Integer Range |
| organizationName | Yes | Yes | Yes | contains |
| organizationTypeId | Yes | Yes | Yes | Match | 
| performanceTask | No | No | No | n/a |
| primaryClaim | Yes | Yes | Yes | Match |
| primaryCommonCoreStandard | No | Yes | No | n/a |
| primaryContentDomain | No | Yes | No | n/a |
| primaryTarget | Yes | Yes | Yes | Match |
| quaternaryClaim | Yes | Yes | No | Match |
| quaternaryCommonCoreStandard | No | Yes | No | n/a |
| quaternaryContentDomain | No | Yes | No | n/a | 
| quaternaryTarget | Yes | Yes | Yes | n/a |
| scoringEngine | No | No | No | n/a |
| secondaryClaim | Yes | Yes | No | Match |
| secondaryCommonCoreStandard | No | Yes | No | n/a |
| secondaryContentDomain | No | Yes | No | n/a |
| secondaryTarget | Yes | Yes | No | Match |
| stimulusId | Yes | Yes | No | Match |
| subject | Yes | Yes | Yes | Match |
| tertiaryClaim | No | Yes | No | n/a |
| tertiaryCommonCoreStandard | No | Yes | No | n/a |
| tertiaryContentDomain | No | Yes | No | n/a |
| tertiaryTarget | Yes | Yes | No | n/a |
| testCategory | No | No | No | n/a |
| type | Yes | Yes | Yes | Match |
| workflowStatus | Yes | Yes | Yes | Match |
| workflowStatusUpdatedDate | Yes | Yes | No | Date Range |
| writingPurpose | No | No | No | n/a |

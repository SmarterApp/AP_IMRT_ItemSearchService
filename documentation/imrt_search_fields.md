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
| calculatedExposuresCount | Yes | Yes | No | integerRange |
| calculatedFormCount | Yes | Yes | No | integerRange |
| contentTaskModel | Yes | Yes | No | match |
| createDate | Yes | Yes | No | dateRange |
| createdBy | Yes | Yes | No | contains |
| daysInWorkflowStatus | Yes | Yes | No | integerRange |
| depthOfKnowledge | Yes | Yes | Yes | match | 
| createdBy | Yes | Yes | Yes | contains | 
| englishContentLastUpdatedDate | Yes | Yes | No | dateRange |
| fieldTestDate | No | No | No | n/a |
| id | Yes | Yes | Yes | match |
| intendedGrade | Yes | Yes | Yes | match |
| isAslProvided | Yes | Yes | Yes | match |
| isAslRequired | Yes | Yes | Yes | match |
| isAslUploadedPriorToLastContentUpdate | No | No | No | No |
| isBeingCreated | Yes | Yes | No | booleanFlag | 
| isBrailleProvided | Yes | Yes | Yes | match |
| isBrailleRequired | Yes | Yes | Yes | match |
| isBrailleUploadedPriorToLastContentUpdate | No | No | No | No |
| isClosedCaptioningProvided | Yes | Yes | Yes | match |
| isClosedCaptioningRequired | Yes | Yes | Yes | match |
| isClosedCaptioningUploadedPriorToLastContentUpdate | No | No | No | No |
| isTranslationProvided | Yes | Yes | Yes | match |
| isTranslationRequired | Yes | Yes | Yes | match |
| itemAuthor | Yes | Yes | Yes | contains |
| itemDifficultyQuintile | Yes | Yes | Yes | integerRange |
| organizationName | Yes | Yes | No | contains | 
| organizationTypeId | Yes | Yes | No | match |
| performanceTask | No | No | No | n/a |
| primaryClaim | Yes | Yes | No | match |
| primaryCommonCoreStandard | No | Yes | No | n/a |
| primaryContentDomain | No | No | No | n/a |
| primaryTarget | Yes | Yes | Yes | match |
| quaternaryClaim | No | Yes | No | n/a |
| quaternaryCommonCoreStandard | Yes | Yes | No | n/a |
| quaternaryContentDomain | No | Yes | No | n/a |
| quaternaryTarget | No | Yes | No | n/a |
| scoringEngine | No | No | No | n/a |
| secondaryClaim | No | Yes | No | n/a |
| secondaryCommonCoreStandard | Yes | Yes | No | n/a |
| secondaryContentDomain | No | Yes | No | n/a |
| secondaryTarget | No | Yes | No | n/a |
| testCategory | No | No | No | n/a |
| type | Yes | Yes | Yes | match |
| workflowStatus | Yes | Yes | Yes | match |
| workflowStatusUpdatedDate | Yes | Yes | Yes | dateRange |
| writingPurpose | No | No | No | n/a |

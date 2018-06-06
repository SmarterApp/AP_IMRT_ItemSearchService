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
| englishContentLastUpdatedDate | No | No | No | n/a |
| fieldTestDate | No | No | No | n/a |
| formType | No | No | No | n/a |
| assessmentType | No | No | No | n/a |
| id | Yes | Yes | No | match |
| intendedGrade | Yes | Yes | Yes | match |
| isAslProvided | Yes | Yes | No | match |
| isAslRequired | Yes | Yes | No | match |
| isAslUploadedPriorToLastContentUpdate | No | No | No | n/a |
| isBeingCreated | Yes | Yes | No | booleanFlag | 
| isBrailleProvided | Yes | Yes | No | match |
| isBrailleRequired | Yes | Yes | No | match |
| isBrailleUploadedPriorToLastContentUpdate | No | No | No | n/a |
| isClosedCaptioningProvided | Yes | Yes | No | match |
| isClosedCaptioningRequired | Yes | Yes | No | match |
| isClosedCaptioningUploadedPriorToLastContentUpdate | No | No | No | n/a |
| isTranslationProvided | Yes | Yes | No | match |
| isTranslationRequired | Yes | Yes | No | match |
| itemAuthor | Yes | Yes | Yes | contains |
| itemDifficultyQuintile | Yes | Yes | Yes | integerRange |
| organizationName | Yes | Yes | Yes | contains | 
| organizationTypeId | Yes | Yes | Yes | match |
| performanceTask | No | No | No | n/a |
| primaryClaim | Yes | Yes | Yes | match |
| primaryCommonCoreStandard | No | Yes | No | n/a |
| primaryContentDomain | No | Yes | No | n/a |
| primaryTarget | Yes | Yes | Yes | match |
| quaternaryClaim | No | Yes | No | n/a |
| quaternaryCommonCoreStandard | No | Yes | No | n/a |
| quaternaryContentDomain | No | Yes | No | n/a |
| quaternaryTarget | No | Yes | No | n/a |
| scoringEngine | No | No | No | n/a |
| secondaryClaim | No | Yes | No | n/a |
| secondaryCommonCoreStandard | No | Yes | No | n/a |
| secondaryContentDomain | No | Yes | No | n/a |
| secondaryTarget | No | Yes | No | n/a |
| stimulusId | Yes | Yes | No | match |
| subject | Yes | Yes | Yes | match |
| tertiaryClaim | No | Yes | No | n/a |
| tertiaryCommonCoreStandard | No | Yes | No | n/a |
| tertiaryContentDomain | No | Yes | No | n/a |
| tertiaryTarget | No | Yes | No | n/a |
| testCategory | No | No | No | n/a |
| type | Yes | Yes | Yes | match |
| workflowStatus | Yes | Yes | Yes | match |
| workflowStatusUpdatedDate | Yes | Yes | No | dateRange |
| writingPurpose | No | No | No | n/a |

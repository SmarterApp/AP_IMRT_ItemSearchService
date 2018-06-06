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

| Field Name | Is Filterable | Is Result Column | Is Count Supported | Filter Type | Is Sort Supported |
| ---------- | ---------- | ------------- | --------------- | ----------- | ----------- |
| allowCalculator | No | No | No | n/a | No |
| associatedItemCount | No | No | No | n/a | No |
| calculatedExposuresCount | Yes | Yes | No | integerRange | Yes |
| calculatedFormCount | Yes | Yes | No | integerRange | Yes |
| contentTaskModel | Yes | Yes | No | match | Yes |
| createDate | Yes | Yes | No | dateRange | Yes |
| createdBy | Yes | Yes | No | contains | Yes |
| daysInWorkflowStatus | Yes | Yes | No | integerRange | Yes |
| depthOfKnowledge | Yes | Yes | Yes | match |  Yes |
| englishContentLastUpdatedDate | No | No | No | n/a | No |
| fieldTestDate | No | No | No | n/a | No |
| formType | No | No | No | n/a | No |
| assessmentType | No | No | No | n/a | No |
| id | Yes | Yes | No | match | Yes |
| intendedGrade | Yes | Yes | Yes | match | Yes |
| isAslProvided | Yes | Yes | No | match | Yes |
| isAslRequired | Yes | Yes | No | match | Yes |
| isAslUploadedPriorToLastContentUpdate | No | No | No | n/a | No |
| isBeingCreated | Yes | Yes | No | booleanFlag |  Yes |
| isBrailleProvided | Yes | Yes | No | match | Yes |
| isBrailleRequired | Yes | Yes | No | match | Yes |
| isBrailleUploadedPriorToLastContentUpdate | No | No | No | n/a | No |
| isClosedCaptioningProvided | Yes | Yes | No | match | Yes |
| isClosedCaptioningRequired | Yes | Yes | No | match | Yes |
| isClosedCaptioningUploaded PriorToLastContentUpdate | No | No | No | n/a | No |
| isTranslationProvided | Yes | Yes | No | match | Yes |
| isTranslationRequired | Yes | Yes | No | match | Yes |
| itemAuthor | Yes | Yes | Yes | contains | Yes |
| itemDifficultyQuintile | Yes | Yes | Yes | integerRange | Yes |
| organizationName | Yes | Yes | Yes | contains |  Yes |
| organizationTypeId | Yes | Yes | Yes | match | Yes |
| performanceTask | No | No | No | n/a | No |
| primaryClaim | Yes | Yes | Yes | match | Yes |
| primaryCommonCoreStandard | No | Yes | No | n/a | No |
| primaryContentDomain | No | Yes | No | n/a | No |
| primaryTarget | Yes | Yes | Yes | match | Yes |
| quaternaryClaim | Yes | Yes | No | match | Yes |
| quaternaryCommonCoreStandard | No | Yes | No | n/a | No |
| quaternaryContentDomain | No | Yes | No | n/a | No |
| quaternaryTarget | Yes | Yes | Yes | n/a | No |
| scoringEngine | No | No | No | n/a | No |
| secondaryClaim | Yes | Yes | No | match | Yes |
| secondaryCommonCoreStandard | No | Yes | No | n/a | No |
| secondaryContentDomain | No | Yes | No | n/a | No |
| secondaryTarget | Yes | Yes | No | match | Yes |
| stimulusId | Yes | Yes | No | match | Yes |
| subject | Yes | Yes | Yes | match | Yes |
| tertiaryClaim | No | Yes | No | n/a | No |
| tertiaryCommonCoreStandard | No | Yes | No | n/a | No |
| tertiaryContentDomain | No | Yes | No | n/a | No |
| tertiaryTarget | Yes | Yes | No | n/a | Yes |
| testCategory | No | No | No | n/a | No |
| type | Yes | Yes | Yes | match | Yes |
| workflowStatus | Yes | Yes | Yes | match | Yes |
| workflowStatusUpdatedDate | Yes | Yes | No | dateRange | Yes |
| writingPurpose | No | No | No | n/a | No |

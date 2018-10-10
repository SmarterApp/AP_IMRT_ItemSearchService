# IMRT Search Fields

[Go Back](Item_Search_Service_API.md)

This page covers the search result fields from IMRT.  It lists all the fields and their different usages in the IMRT application.  All fields currently come back as Strings as that is how they are stored within IAT's item.json. 

### Table Legend

| Column | Description |
| ------ | ----------- |
| Field Name | The field name in the search results.  What each value represents can be found in the Item Data Dictionary provided by Smarter Balanced |
| Is Count Supported | Yes/No based on if the field can be used in a count |
| Filter Type | The type of the filter based on the list of [filters](Filters.md) |


## IMRT Supported Fields

| Field Name | Is Count Supported | Filter Type |
| ---------- | --------------- | ----------- | 
| allowCalculator | No | [Match](Filters.md#match-filter) |
| associatedItemCount | No | [Integer Range](Filters.md#integer-range-filter) | 
| benignValidationResultCount | No | [Integer Range](Filters.md#integer-range-filter) | 
| calculatedExposuresCount | No | [Integer Range](Filters.md#integer-range-filter) |
| calculatedFormCount | No | [Integer Range](Filters.md#integer-range-filter) |
| contentTaskModel | No | [Match](Filters.md#match-filter) |
| createDate | No | [Date Range](Filters.md#date-range-filter) |
| createdBy | No | [Contains](Filters.md#contains-filter) | 
| currentUpdateNeedCreatedDate | No | [Date Range](Filters.md#date-range-filter) | 
| currentUpdateNeedInternalResolution | No | [Match](Filters.md#match-filter) | 
| currentUpdateNeedInternalResolutionDate | No | [Date Range](Filters.md#date-range-filter) | 
| currentUpdateNeedResolution | No | [Match](Filters.md#match-filter) |
| currentUpdateNeedResolutionDate | No | [Date Range](Filters.md#date-range-filter) |
| daysInWorkflowStatus | No | [Integer Range](Filters.md#integer-range-filter) |
| depthOfKnowledge | Yes | [Match](Filters.md#match-filter) | 
| degradedValidationResultCount | No | [Integer Range](Filters.md#integer-range-filter) |
| englishContentLastUpdatedDate | No | [Date Range](Filters.md#date-range-filter) |
| englishPassagesCount | No | [Integer Range](Filters.md#integer-range-filter) | 
| formType | No | [Match](Filters.md#match-filter) |
| assessmentType |  No | [Match](Filters.md#match-filter) |
| id |  No | [Match](Filters.md#match-filter) |
| intendedGrade | Yes | [Match](Filters.md#match-filter) |
| isAslProvided | No | [Match](Filters.md#match-filter) |
| isAslRequired | No | [Match](Filters.md#match-filter) |
| isAslUploadedPriorToLastContentUpdate | No |  |
| isBeingCreated | No | [Boolean](Filters.md#boolean-filter) | 
| isBrailleProvided | No | [Match](Filters.md#match-filter) |
| isBrailleRequired | No | [Match](Filters.md#match-filter) |
| isBrailleUploadedPriorToLastContentUpdate | No | |
| isClosedCaptioningProvided | No | [Match](Filters.md#match-filter) |
| isClosedCaptioningRequired | No | [Match](Filters.md#match-filter) |
| isClosedCaptioningUploadedPriorToLastContentUpdate | No |  |
| isContentChangedAfterOperational | No |[Boolean](Filters.md#boolean-filter) | 
| isEnglishGlosaryProvided | No |[Boolean](Filters.md#boolean-filter) | 
| isIllustratedGlossaryProvided | No |[Boolean](Filters.md#boolean-filter) | 
| isIllustratedGlossaryRequired | No | [Match](Filters.md#match-filter) |
| isTranslatedGlossaryProvided | No |[Boolean](Filters.md#boolean-filter) | 
| isTranslatedGlossaryRequired | No | [Match](Filters.md#match-filter) |
| isTranslationProvided | No | [Match](Filters.md#match-filter) |
| isTranslationRequired | No | [Match](Filters.md#match-filter) |
| itemAuthor | Yes | [Contains](Filters.md#contains-filter) | 
| itemDifficultyQuintile | Yes | [Integer Range](Filters.md#integer-range-filter) |
| hasUnresolvedUpdateNeed | No |[Boolean](Filters.md#boolean-filter) | 
| organizationName | Yes | [Contains](Filters.md#contains-filter) | 
| organizationTypeId | Yes | [Match](Filters.md#match-filter) | 
| performanceTask | No | [Match](Filters.md#match-filter) |
| primaryClaim | Yes | [Match](Filters.md#match-filter) | 
| primaryCommonCoreStandard | No | [Contains](Filters.md#contains-filter) | 
| primaryContentDomain | No | [Contains](Filters.md#contains-filter) | 
| primaryTarget | Yes | [Match](Filters.md#match-filter) | 
| quaternaryClaim | Yes | [Match](Filters.md#match-filter) | 
| quaternaryCommonCoreStandard | No | [Contains](Filters.md#contains-filter) | 
| quaternaryContentDomain | No | [Contains](Filters.md#contains-filter) | 
| quaternaryTarget | Yes | [Match](Filters.md#match-filter) | 
| scoringEngine | No | [Match](Filters.md#match-filter) | 
| secondaryClaim | Yes | [Match](Filters.md#match-filter) | 
| secondaryCommonCoreStandard | No | [Contains](Filters.md#contains-filter) | 
| secondaryContentDomain | No | [Contains](Filters.md#contains-filter) | 
| secondaryTarget | Yes | [Match](Filters.md#match-filter) | 
| severeValidationResultCount | No |[Integer Range](Filters.md#integer-range-filter)|
| spanishPassagesCount | No | [Integer Range](Filters.md#integer-range-filter) |
| stimulusId | No | [Match](Filters.md#match-filter) | 
| subject | Yes | [Match](Filters.md#match-filter) | 
| tertiaryClaim | Yes | [Match](Filters.md#match-filter) | 
| tertiaryCommonCoreStandard | No | [Contains](Filters.md#contains-filter) | 
| tertiaryContentDomain | No | [Contains](Filters.md#contains-filter) | 
| tertiaryTarget | Yes | [Match](Filters.md#match-filter) | 
| testCategory | No | [Match](Filters.md#match-filter) | 
| tolerableValidationResultCount | No | [Integer Range](Filters.md#integer-range-filter) |
| type | Yes | [Match](Filters.md#match-filter) | 
| workflowStatus | Yes | [Match](Filters.md#match-filter) | 
| workflowStatusUpdatedDate | No | [Date Range](Filters.md#date-range-filter) |
| writingPurpose | No | [Match](Filters.md#match-filter) | 

## Derived Fields
Therre are a few fields that are not in the Item Data Dictionary nor the item.  These are fields that are either derived by IMRT or retrieved from another system (example, Item Content Tabulator Validation Results).  The table lists out those fields and how they're derived.

| Field | Source | Description |
| ----- | ------ | ----------- |
| benignValidationResultCount | Item Content Tabulator | Total count of benign errors reported for the item|
| tolerableValidationResultCount | Item Content Tabulator | Total count of benign errors reported for the item |
| degradedValidationResultCount | Item Content Tabulator | Total count of benign errors reported for the item|
| severeValidationResultCount| Item Content Tabulator | Total count of sever errors reported for the item|
| daysInWorkflowStatus | Derived by IMRT | The number of days since the workflow status has changed  |
| hasUnresolvedUpdateNeed | Dervied by IMRT | This will be true if any of the content update needs do not have a resolution value |
| isContentChangedAfterOperational | Derived by IMRT | The will be set to true if any of the english or spanish content has changed after an item has been marked operational. |







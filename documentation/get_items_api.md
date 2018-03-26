# Get Items

[Go Back](Item_Search_Service_API.md)

This page covers the API to multiple items by their ids.  The ids are the item's ids as definied within the item.json in the itembank.

### Supported Content Types

* `application/json`

### Get Items

`GET /items?ids={list of item ids}`

| Variable | Description | Sample Value |
| -------- | ----------- | ------------ |
| ids   | Unique item ids for the items. | 205160

**Example** : `items?ids=205160,206111`

#### Success Responses

##### HTTP 200 - Success

**Response Body**

```
[
   {
      "createdAt":"2018-03-22T03:09:22.380Z",
      "updatedAt":"2018-03-22T03:09:22.380Z",
      "updatedBy":"tbd author",
      "key":3,
      "id":"205033",
      "subject":"",
      "grade":"",
      "workflowStatus":"ParkingLot",
      "itemType":"sa",
      "depthOfKnowledge":"",
      "itemCreatedBy":"tbd author",
      "itemCreatedAt":"2018-03-22T03:09:22.358Z",
      "itemJson":{
         "id":"205033",
         "type":"sa",
         "version":"iat-5",
         "core":{
            "stimulusId":"205034",
            "enemyItems":[

            ],
            "metadata":{
               "accessibilityLanguageComplexity":"",
               "calculator":"",
               "claim2Category":"",
               "claim2SubCategory":"",
               "contentDomain":"",
               "contentTaskModel":"",
               "copyrightHolder":"",
               "copyrightHolderOther":"",
               "depthOfKnowledge":"",
               "grade":"",
               "algebraDescriptor1":"",
               "algebraDescriptor2":"",
               "itemPoint":"",
               "knowledgeDemands":"",
               "languageFeatures":"",
               "maxGrade":"",
               "meaningPurpose":"",
               "minGrade":"",
               "passageName":"",
               "performanceTask":"",
               "primaryAssessmentTarget":"",
               "primaryClaim":"",
               "primaryCommonCoreStandard":"",
               "primaryContentDomain":"",
               "quaternaryAssessmentTarget":"",
               "quaternaryClaim":"",
               "quaternaryCommonCoreStandard":"",
               "quaternaryContentDomain":"",
               "readabilityFleschKincaid":"",
               "readabilityLexile":"",
               "scoringEngine":"",
               "scoringPoints":"",
               "secondaryAssessmentTarget":"",
               "secondaryClaim":"",
               "secondaryCommonCoreStandard":"",
               "secondaryContentDomain":"",
               "stimulusFormat":"",
               "stimulusLength":"",
               "structure":"",
               "subject":"",
               "tertiaryAssessmentTarget":"",
               "tertiaryClaim":"",
               "tertiaryCommonCoreStandard":"",
               "tertiaryContentDomain":"",
               "testCategory":"",
               "wordCount":"",
               "writingPurpose":""
            },
            "en":{
               "prompt":"<p>SA Prompt</p>",
               "exemplarResponses":[

               ],
               "rubrics":[

               ],
               "isRequired":"true",
               "isProvided":true
            },
            "attachments":[

            ]
         },
         "asl":{
            "attachments":[

            ],
            "isAslRequired":"undetermined",
            "isAslProvided":false
         },
         "braille":{
            "attachments":[

            ],
            "isBrailleRequired":"undetermined",
            "isBrailleProvided":false
         },
         "cc":{
            "attachments":[

            ],
            "isCcRequired":"undetermined",
            "isCcProvided":false,
            "itemCcAudioAssociations":[

            ]
         },
         "images":{
            "imageResources":[

            ]
         },
         "audio":{
            "audioResources":[

            ]
         },
         "textToSpeech":{
            "isVisualTTSRequired":"undetermined",
            "isVisualTTSProvided":false,
            "isSightTTSProvided":false
         },
         "workflow":{
            "workflowStatusCode":"ParkingLot"
         },
         "translations":{
            "esp":{
               "prompt":"",
               "exemplarResponses":[

               ],
               "rubrics":[

               ],
               "isRequired":"undetermined",
               "isProvided":false
            }
         }
      }
   }
]
```

#### Error Responses

* 500 - an unhandled error on the server
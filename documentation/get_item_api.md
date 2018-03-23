# Get Item

This page covers the API 

### Supported Content Types

* `application/json`

### Get an Item

Get a single IMRT item.  The item is a representation of an item within the itembank.

`GET /items/{itemId}`

| Variable | Description | Sample Value |
| -------- | ----------- | ------------ |
| itemId   | The item's unique id as stored in the itembank. | 205160

**Example** : `items/123/`

#### Success Responses

##### HTTP 200 - Success

**Response Body**

```
{  
   "createdAt":"2018-03-14T17:38:46.197Z",
   "updatedAt":"2018-03-14T17:38:46.197Z",
   "updatedBy":"tbd author",
   "key":2,
   "id":"205080",
   "subject":"Math",
   "grade":"5",
   "workflowStatus":"Draft",
   "itemType":"sa",
   "depthOfKnowledge":"2",
   "itemCreatedBy":"tbd author",
   "itemCreatedAt":"2018-03-14T17:38:46.195Z",
   "itemJson":{  
      "id":"205080",
      "type":"sa",
      "version":"iat-6",
      "core":{  
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
            "depthOfKnowledge":"2",
            "grade":"5",
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
            "primaryAssessmentTarget":"primary target",
            "primaryClaim":"3",
            "primaryCommonCoreStandard":"",
            "primaryContentDomain":"p cont dom",
            "quaternaryAssessmentTarget":"",
            "quaternaryClaim":"",
            "quaternaryCommonCoreStandard":"qcc",
            "quaternaryContentDomain":"",
            "readabilityFleschKincaid":"",
            "readabilityLexile":"",
            "scoringEngine":"",
            "scoringPoints":"",
            "secondaryAssessmentTarget":"",
            "secondaryClaim":"3",
            "secondaryCommonCoreStandard":"",
            "secondaryContentDomain":"",
            "stimulusFormat":"",
            "stimulusLength":"",
            "structure":"",
            "subject":"Math",
            "tertiaryAssessmentTarget":"E",
            "tertiaryClaim":"",
            "tertiaryCommonCoreStandard":"",
            "tertiaryContentDomain":"",
            "testCategory":"",
            "wordCount":"",
            "writingPurpose":""
         },
         "en":{  
            "prompt":"<p>Adding a prompt</p>",
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
         "workflowStatusCode":"Draft"
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
```
#### Error Responses

* 404 - when an item cannot be found
* 500 - an unhandled error on the server
# Get Item

[Go Back](Item_Search_Service_API.md)

This page covers the API to retrieve a single item

### Supported Content Types

* `application/json`

### Get an Item

Get a single IMRT item.  The item is a representation of an item within the itembank.

`GET /items/{itemId}`
`GET /items/{itemId}?includeDetails={includeDetailsVal}`

| Variable | Description | Required | Sample Value |
| -------- | ----------- | -------- |------------ |
| itemId   | The item's unique id as stored in the itembank. | yes | 205160
| includeDetailsVal | Boolean to include the item.json from the itembank.  Defaults to false. | no | true/false 

**Examples** : 

* `items/123/`
* `items/123?includeDetails=true`

#### Success Responses

##### HTTP 200 - Success
**Response Body if Details Not Included**
<pre>
{
	"id": "205033",
	"subject": "",
	"grade": "",
	"workflowStatus": "ParkingLot",
	"itemType": "sa",
	"depthOfKnowledge": "",
	"createdBy": "iat_Draft TestUser",
	"createdAt": "2018-03-07T01:44:29Z",
	"standardIds": [],
	"itemDetail": null
}
</pre>


**Response Body if Details Included**

<pre>
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
</pre>

#### Error Responses

* 404 - when an item cannot be found
* 500 - an unhandled error on the server
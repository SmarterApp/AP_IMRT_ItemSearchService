# Get Items

[Go Back](Item_Search_Service_API.md)

This page covers the API to multiple items by their ids.  The ids are the item's ids as definied within the item.json in the itembank.

### Supported Content Types

* `application/json`

### Get Items

`GET /items?ids={list of item ids}`
`GET /items?ids={list of item ids}&includeDetails={includeDetailsVal}?

| Variable | Description | Required | Sample Value |
| -------- | ----------- | -------- |------------ |
| ids   | Unique item ids for the items. | yes | 205160
| includeDetailsVal | Boolean to include the item.json from the itembank.  Defaults to false. | no | true/false 

**Example**

* `items?ids=205160,206111`
* `items?ids=205160,206111&includeDetails=true`

#### Success Responses

##### HTTP 200 - Success

**Response Body if Details Not Included**
<pre>
[
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
]
</pre>

**Response Body if Details Included**
<pre>
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
</pre>

#### Error Responses

* 500 - an unhandled error on the server
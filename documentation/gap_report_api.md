# Gap Report API

[Go Back](./reports.md)

This page covers how to interact with the Gap Report API.

### Supported Content Types
The Gap Report API supports the following types in the `Content-Type` headers:

* `application/json`
* `application/vnd.openxmlformats-officedocument.spreadsheetml.sheet`

### Supported Accept Types
The Gap Report API supports the following types in the `Accept` headers:

* `application/json`
* `application/vnd.openxmlformats-officedocument.spreadsheetml.sheet`

### Gap Report Request
The Gap Report request computes the count of each Item Difficulty Qunitile level for items stored in the item bank.

A `POST` to the Gap Report endpoint will execute a query against the item bank database and produce a count of items for each of the various difficulty levels.  The `POST` to the Gap Report API endpoint will appear as follows:

`POST [Item Search Service domain]/v1/items/reports/gap`

### Request Body Description
The Gap Report request consists of two elements described below.  _**Both elements are required in the Gap Report request**_.

#### Filters
The **filters** element is an array of `Filter`s specifying how the user wants to limit which items should be counted.  the filters supplied in this request are the same [filters](./Filters.md) supported by the [General Search API](./general_search_api.md).  The `filters` element has the following rules:

* To run the report without any `filter`s, send a request with an empty `filters` array
  * This means all the items in the item bank will be aggregated

#### Groups
The **groups** element is an array of `String`s representing which fields should be displayed on the Gap Report and how the Item Difficulty Quintile counts should be aggregated.  The `groups` element has the following rules:

* The order in which the groups occur in the Gap Report request dictate the order in which the group columns will appear in the Gap Report
  * For example, if the **groups** property is set to `intendedGrade`, `subject` and `type`, the columns on the report will be **Intended Grade**, **Subject** and **Item Type**, followed by the calculation/quintile count fields  
* Only search properties that support counts (i.e. "group by properties") are allowed for use as groups.  The search properties that support counts can be found [here](./item_count_api.md).
  * Passing in a search property that does not support counts (e.g. `stimulusId`) will result in a `400 - Bad Request` response from the server

#### Example Gap Request Payload
Shown below is an example of a payload to `POST` to the Gap Report endpoint.  This request will:

* Filter results by subject and intended grade
* Group Item Difficulty Quintile counts by intended grade, item type, primary target and subject

```json
{
	"filters": [
		{
			"property": "subject",
			"values": ["ELA", "MATH"]
		},
		{
			"property": "intendedGrade",
			"values": ["3", "4"]
		}
	],
	"groups": [
		"intendedGrade",
		"type",
		"primaryTarget",
		"subject"
	]
}
```

### Response
The Gap Report response will contain an `xlsx` file containing the Gap Report results.  The `xlsx` file is returned as an attachment within the response.  Aside from the attachment, the Gap Report response does not have a body.

#### Success
A successful response from the Gap Report API will:

* Return an HTTP Status code of `200` (OK)
* Contain [at least] the following headers:
  * `Content-Type: application/vnd.openxmlformats-officedocument.spreadsheetml.sheet`
  * `Content-Disposition: attachment; filename=[the name of the Gap Report file]`
  * `Content-Length=[the size of the Gap Report file]`

The Gap Report file will be included as an attachment to the response.  Tools such as `curl` or [PostMan](https://www.getpostman.com/) can download the attached file.

#### Failure
When a request to the Gap Report API fails (e.g. the request contains invalid filter and/or group parameters, the report file could not be generated, etc.), the response body will:

* Contain [at least] the following headers:
  * `Content-Type: application/json`
* Contain JSON in the following format:
  * `message`:  A brief error message describing the error that was encountered
  * `code`:  The HTTP Status code

### Example Usage
Shown below is an example `curl` call for fetching a Gap Report:

```bash
curl -O -J -X POST \
  http://localhost:9080/v1/items/reports/gap \
  -H 'Accept: */*' \
  -H 'Authorization: Bearer [redacted]' \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -d '{
    "filters": [
        {
            "property": "subject",
            "values": ["ELA", "MATH"]
        },
        {
            "property": "intendedGrade",
            "values": ["3", "4"]
        }
    ],
    "groups": [
        "intendedGrade",
        "type",
        "primaryTarget",
        "subject"
    ]
}'
```


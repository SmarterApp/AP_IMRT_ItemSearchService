# Item Count

[Go Back](Item_Search_Service_API.md)

This page covers the API to group counts of items by a specific item property.

**Invalid or unsupported filters or group by will result in empty responses**

### Supported Content Types

* `application/json`

### Supported Accept types

* `application/json`

### Count Request

Count requests will get the counts grouped by a supported item property after applying filters to the data.  

The values within each filter is "OR"ed with each filter being "AND"ed together.  In the "Request Body" section below there is a discription of how this would work.

`POST /v1/items/count`

### Request Body Description

The table below lists the fields which must be within the 

| Field | Description | Required | 
| -------- | ----------- | -------- |
| groupBy   | The property to group items | yes
| fitlers | The filters to apply to the results prior to gather counts| yes

#### Filters

The property name for this is "filters".  This is an array of `filter` JSON objects describing different filters to run.

Available filters can be found [here](Filters.md).  The fields that support count can be found on the [Search Fields page](imrt_search_fields.md).


#### Request Body Example
```json
{
	"filters": [
		{
            "type": "match",
            "property": "subject",
            "values":["ELA"]
        }
	],
	"groupBy": "grade"
}
```

### Response Body Description

The table below describes the page information included in the response.  Property values are the exact values stored within the item.json.  

| Field | Description | 
| -------- | ----------- | 
| groupBy | The property used to generate the counts.  Same as in the request |
| totalCount | The total count |
| counts | An array of count objects with the value being the groupBy property value and count being the number of items with the groupBy value |

#### Response Body
```json
{
    "groupBy": "intendedGrade",
    "totalCount": 3,
    "counts": [
        {
            "value": "4",
            "count": 1
        },
        {
            "value": "5",
            "count": 2
        }
    ]
}
```




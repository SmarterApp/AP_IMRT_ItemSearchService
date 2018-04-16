# Item Count

[Go Back](Item_Search_Service_API.md)

This page covers the API to group counts of items by a specific item property.

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
| groupByProperty   | The property to group items | yes
| fitlers | The filters to apply to the results prior to gather counts| yes

#### Filters

The property name for this is "filters".  This is an array of `filter` JSON objects describing different filters to run.

Available filters can be found [here](Filters.md)

#### Group by Property

Supported properties

| Property | Description | 
| -------- | ----------- |
| subject | Breaks down item counts by items' subject |
| grade | Breaks down item counts by items' grade | 
| organizationType | Breaks down the items' counts by organization type |
| organizationName | Breaks down the items' counts by organization name |
| workflowStatus | Breaks down the items' counts by workflow status |
| user | Breaks down the items' counts by the user who created the item |

#### Request Body
```json
{
	"filters": [
		{
            "type": "match",
            "property": "subject",
            "values":["ELA"]
        }
	],
	"groupByProperty": "grade"
}
```

### Response Body Description

The table below describes the page information included in the response.  Property values are the exact values stored within the item.json.  

| Field | Description | 
| -------- | ----------- | 
| groupByProperty | The property used to generate the counts.  Same as in the request |
| counts | A Map of counts.  They key is the value as stored on the item with the value representing the count of items that have the value. |

#### Response Body
```json
{
    "groupByProperty": "grade",
    "counts": {
        "3": 3,
        "4": 2,
        "5": 5,
        "6": 2,
        "7": 1,
        "8": 2,
        "11": 3,
        "": 82
    }
}
```


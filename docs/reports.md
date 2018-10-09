# Item Search Service Report API
[Go Back](../README.md)

In addition to providing an API for finding items in the item bank, the [Item Search Service](https://github.com/SmarterApp/AP_IMRT_ItemSearchService) provides reports with data the search API is not well-suited to provide.  A list of the available reports can be fownd below.

## Authentication
Like the search API, the reporting endpoints implement OAauth2 Authentication against a configurable OpenAM server.  Refer to the [Item Search Service API](Item_Search_Service_API.md) documentation for additional details on how to use `curl` to compose an authentication request.

## Reports

* [Gap Report](gap_report.md)
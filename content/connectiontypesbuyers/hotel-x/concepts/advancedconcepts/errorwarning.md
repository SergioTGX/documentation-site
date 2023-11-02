+++
title = "Errors and Warnings"
pagetitle = "Errors and Warnings"
description = "List of errors and warnings in HotelX"
icon = "fa-exclamation-triangle"
weight = 4
alwaysopen = false
+++


In this chapter we will list the errors and warnings of HotelX booking flow and content.
# Booking flow
## Error list
In the table below, we have structured a relation of all the **Errors** that can be returned in HotelX booking flow

|         Code         |       Type       |            Description            | Explanation  |
| :------------------: | :--------------: | --------------------------------- |-------------- |
|     ACCESS_ERROR     | VALIDATION_ERROR | No valid accesses found           | The access is not found or it has no permission, or you are using a test access and you need to add the testMode.|
|    MISSING_FIELD     | VALIDATION_ERROR | *According to the case*           | Some mandatory fields are missing in input|
|    INTERNAL_ERROR    |    API_ERROR     | *According to the case*           | Covers any unexpected error or errors due to **internal** service|
| ALL_PROCESSES_FAILED |  PROCESS_ERROR   | See warnings for more information | This occurs when no options are returned for all accesses after applying a plugin (blacklist, filter, mapping code),  commission, etc., it may also be caused by a wrong default setting, In the warning node you will find detailed information about the cause.|
|       TIMEOUT        | CONNECTION_ERROR | *According to the case*           | This occurs due to a connection timeout|
| REFERENCE_NOT_EXISTS |  BOOKING_ERROR   | *According to the case*           | This occurs when the booking reference provided is not available in the supplier system|


## Warning list

In this section we will expand on all the **Warnings** that can be returned in HotelX booking flow. There are two types of warnings, **HotelX warnings** and **Connection warnings**.

### HotelX warnings

In the table below, we have structured a relation of all the **Warnings** that can be returned in HotelX.

|                Code                | Type  |       Description       | Explanation                  |
| :--------------------------------: | :---: | ----------------------- | ---------------------------- |
|     WRONG_FIELD      | VALIDATION_ERROR | *According to the case* | A field or fields in the request are not correct|
|    INTERNAL_ERROR    |  MAPPING_ERROR   | *According to the case* | Error produced when mapping codes, it usually happens regarding hotel mapping|
| COMMISSION_NOT_FOUND |    API_ERROR     | *According to the case* | This occurs when the options are discarded because the supplier returns options with a negative commission that does not allow the calculation of the net price. You need to upload the commission file to solve it|
|     WRONG_FIELD      |   PLUGIN_ERROR   | *According to the case* | It occurs when the input of the plugin is misintroduced or misconstructed|
|      BLACKLIST       |   PLUGIN_ERROR   | *According to the case* | It occurs when the hotels or accesses are blacklisted|

#### Error 204 - No Results Found
Error “204 No results found” is a common error that you can receive in the Search Query response. This error means that the product you are trying to obtain is not available.

There are several potential reasons as to why this error occurs:

* The product is not available for the dates in the request.
* The product is not available for the number of passengers selected in the request.
* The product is not available for the destination selected in the request.
* The product has been filtered by criteria applied in the pluggins.

In case an error of this type is received, you should first contact the supplier directly on a commercial level and check with them whether there should be availability for the product you are trying to obtain with the specific search criteria (dates, passenger quantity, passenger age, destination you have chosen, etc.). In case the supplier confirms that there should be availability but you are still not obtaining it, you should review the criteria set out in the pluggins you may be using, if you still can't find the problem please you should contact our Customer Care department.

### Connection warnings

This type of warnings contains the supplier original error codes. This type of error codes are classified as warning codes because whenever more than 1 supplier is requested, some of those suppliers may return an error while others may return the response, accordingly. In those cases, if at least one of the suppliers returns results an error cannot be returned, hence those results will be displayed in the response, and for those accesses which have not returned results a warning will be returned.

[See list of supplier error codes](https://docs.travelgatex.com/legacy/hotel/methods/messages/listsdata/#error-codes)

# Content
## Error List
In the table below, we have structured a relation of all the **Errors** that can be returned in HotelX content

|         Code         |            Description            | Explanation  |
| :------------------: | --------------------------------- |-------------- |
|    11204      | *According to the case*           | This occurrs when no results found|
|    11400      | *According to the case*           | A field or fields in the request are missing or not correct|
|    22401      | *According to the case*           | This occurs when the request lacks valid authentication credentials for the requested resource|
|    22500      | *According to the case*           | Covers any unexpected error or errors due to **internal** service|
|    22512      | *According to the case*           | This occurs when there is insufficient data to return due to internal error service|


## Warnings

In the table below, we have structured a relation of all the **Warnings** that can be returned in HotelX content.

|                Code                |       Description       | Explanation                  |
| :--------------------------------: | ----------------------- | ---------------------------- |
|    21500      | *According to the case* | This occurrs when there is an unexpected error retrieving mapping codes|
|    22600      | *According to the case* | This occurrs when no mapping is found.|
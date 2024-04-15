# How can I filter a call log by action and result?

**Question**

I am retrieving the call log for a user by sending a GET request via cURl in php. I have had no issue retrieving these logs and adjusting inputs such as perPage or dateFrom.

An example of a successful call(Sandbox):

https://platform.devtest.ringcentral.com/restapi/v1.0/account/~/call-log?view=Simple&dateFrom=20....

However, while viewing the doc found here:

https://developer.ringcentral.com/api-explorer/latest/index.html#/!/Call_Log/loadExtensionCallLog

I do not see how to specify action and result under the 

`GET /v1.0/account/{accountId}/extension/{extensionId}/call-log`

I would like to filter the call log by the action of "Phone Call" and result of "Missed".

Is this possible with a GET request or will it have to be done after the records are retrieved?

**Answer**

There are a few additional query parameters which will get you "closer" to where you want to be (I'll show some URL examples below). The only part that you should need to filter the response data for (based on the criteria you've provided) is "result" === "Missed". I've submitted a suggestion to our API Product Management team to consider adding the ability to filter on some of the Call Log Record data in the call-log requests as well. If I learn there is a way to filter by result=Missed, I will update this documentation.

Here are the query parameters you can use to filter call-logs:

* Filter by Phone Number (cannot be used with extensionNumber query param simultaneously)
* Param Name === phoneNumber
* Value Format === E.164 number, `<countryCode><areaCode><exchangeCode><identifier>`
  * Example === 13215551212

Filter by Extension Number (cannot be used with phoneNumber query param simultaneously)
Param Name === extensionNumber
Value Format === Number, <extensionNumber> // Note, this is NOT the extension ID
Example === 104

Filter by Voice (Phone Call)
Param Name === type
Value Format === String, One of the valid Call Types, either "Voice" -or- "Fax"
Example === Voice

Filter by Direction
Param Name === direction
Value Format === String, One of the valid Call Direction strings, either "Inbound" -or- "Outbound"
Example === Inbound
Here is a cURL example using all of these together (except extensionNumber since we cannot use that and phoneNumber together in same query):

https://platform.devtest.ringcentral.com/restapi/v1.0/account/~/call-log?type=Voice&phoneNumber=13215551212&direction=Inbound

The results of these calls will contain the appropriately time-based range (as defined by the default of last 24 hours, or by using the dateFrom and dateTo query params). Each record will have a "result" property, you will just need to filter out the results by the value "Missed" to get the records you want.

Let me know if you'd like some example code for filtering these results.

If I understood your response correctly there is no current way to add "result" as a query param while requesting a Call Log record. This is the exact information I was looking for. 

Yes, that is correct. To filter for result = "Missed", you would need to do that post-response.


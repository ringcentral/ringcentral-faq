# Call-Log FAQ

### How to retrieve call logs using API

https://devcommunity.ringcentral.com/ringcentraldev/topics/a-question-on-retrieving-call-logs-using-the-api

### How do we identify which extension picked up the Call through our API ?

In-order to identify the extension who picked up the call you would need to retrieve the Account Call-Logs :
API Endpoint :  /v1.0/account/{accountId}/call-log
Parameters : 'view' = 'Detailed'

An example of the API response containing the legs would be as below :
"legs": [
            {
                "startTime": "2016-05-13T18:13:20.000Z",
                "duration": 53,
                "type": "Voice",
                "direction": "Inbound",
                "action": "Phone Call",
                "result": "Accepted",
                "to": {
                    "phoneNumber": "+11234567890",
                    "name": "Sample Digital Line Only"
                },
                "from": {
                    "phoneNumber": "+11212121212",
                    "name": "Sample Company Number",
                    "location": "Millbrae, CA"
                },
                "transport": "PSTN",
                "legType": "Accept",
                "extension": {
                    "uri": "https:\/\/platform.ringcentral.com\/restapi\/v1.0\/account\/665427020\/extension\/734191020",
                    "id": 734191020
                }
            }
         ]

For more information on the Account level Call Log Endpoint, please take a look at our API Explorer :
https://developer.ringcentral.com/api-explorer/latest/index.html#/!/Call_Log/loadExtensionCallLog
Please be reminded the endpoint would be /v1.0/account/{accountId}/call-log
From above the Account level Call-Logs would return the legs within the Detailed view which would contain the "to" information about the extension which picked up the Call.
At the moment, our API response would contain the name of the extension who picked up the call using which we could map it to the extension number ( the extension number ( xxx - xxxxx ) assigned to the extension.
The name parameter returned in the API response is the 'First Name' + space + 'Last Name' which is assigned to the extension in the Service Web ( https://service.ringcentral.com/ )

name = ( string ) 'First Name' + space + 'Last Name'

Take a look at our tutorial on adding / creating extensions : http://success.ringcentral.com/RCSupportPortalLearningCenter?LCtabId=settings_0#


### How to filter a call-log by action and result ?

https://devcommunity.ringcentral.com/ringcentraldev/topics/how-to-filter-a-call-log-by-action-and-result


# Voice FAQ

### How can I make an outgoing call through the API?

An outgoing call can be made using RingCentral's RingOut API and using WebRTC.


The RingCentral API can be accessd using OAuth 2.0 for authentication and authorization with REST for access to API resources. From the user’s perspective it will work in a similar way as the RingOut feature on the RingCentral Web Site (more details about RingOut feature can be found here). The API accepts the phone number where caller wants to pick the call, the called party number and optionally a caller ID. More details and examples can be found in the RingCentral API documentation.

### What is Ringout?

The RingOut capability enables users to make calls connecting two phone numbers using a RingCentral account, one for the user and another for the number being called. Form an API perspective, RingOut is useful when you want to connect any two phones without any programmability for the phones themselves. When using a web browser, WebRTC is a useful alternative. RingOut is designed to work with outside numbers (not RingCentral numbers) but has also been used with RingCentral numbers. In addition to the API, RingOut is supported in RingCentral's softphone, web and mobile applications.

### How can I ensure RingOut is working?

1. Make sure either a Digital Line or a Direct Number is associated with an extension.
1. To add a direct number to an extension see: https://www.youtube.com/watch?v=Uxv0KlnMZZM                 
1. To add a Digital Line to an extension see: http://success.ringcentral.com/articles/en_US/RC_Knowledge_Article/How-to-Assign-an-Existing-Digital-Line-to-a-different-extension
1. Please note that your sandbox number has been assigned the default extension (101) however you should assign either a direct / digital line inorder to make/receive a ringout call on the sandbox number.    
1. Login to the extension on the “RingCentral for Desktop” application before you initiate a RingOut.
1. If the extension is a “From” number then during the first leg of the ringout the “To” number would be displayed and once you dial `1` the second leg of the call would be initiated.
1. The same is the case if the extension is a “To” number. 

### How can I check the status of a RingOut in progress?

To check the current status of a 2-Legged RingOut, make a `GET` request to the endpoint:

* `v1.0/account/{accountId}/extension/{extensionId}/ringout/{ringoutId}`

where the `accountId` and `extensionId` could be `~` to refer to the authorized extension and the `ringoutId` parameter is the one generated for the RingOut when the call is initiated. 

For more information please take a look at the API Explorer page here:

* [https://developer.ringcentral.com/api-explorer/latest/index.html#/!/RingOut/getRingOutCallStatus](https://developer.ringcentral.com/api-explorer/latest/index.html#/!/RingOut/getRingOutCallStatus)

### How can I cancel a RingOut?

A RingOut can be cancelled using an API call to the RingOut API endpoint using the `DELETE` method when the RingOut is `InProgress`.

* API Endpoint: `v1.0/account/{accountId}/extension/{extensionId}/ringout/{ringoutId}`

Deleting the RingOut is only available when the RingOut has been initiated and the call has not been connected. For example:

* If you initiate a RingOut and immediately call the `DELETE` RingOut API Endpoint, the call would get hangup as long as the RingOut between the two parties is not connected (first leg has not been established) 
* If the first leg of the call has been initiated, then the `DELETE` API will not hangup the call.

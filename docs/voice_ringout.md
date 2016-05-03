# Voice FAQ

### How can I make an outgoing call through the API?

The RingCentral API can be accessd using OAuth 2.0 for authentication and authorization with REST for access to API resources. From the user’s perspective it will work in a similar way as the RingOut feature on the RingCentral Web Site (more details about RingOut feature can be found here). The API accepts the phone number where caller wants to pick the call, the called party number and optionally a caller ID. More details and examples can be found in the RingCentral API documentation.

### What is Ringout ?

The RingOut option enables users to make a call from any other outside number (not a RingCentral number) by means of their RingCentral account, when it is not convenient for them to use the RingCentral number. This feature is available for softphone, web and mobile applications. The RingCentral API allows to make and get RingOut calls.

### How to make sure Ringout Works ?

* Make sure either a Digital Line / Direct Number is associated with an extension.
* To add a direct number to an extension: https://www.youtube.com/watch?v=Uxv0KlnMZZM                 
* To add a Digital Line to an extension: http://success.ringcentral.com/articles/en_US/RC_Knowledge_Article/How-to-Assign-an-Existing-Digital-Line-to-a-different-extension
* Kindly note that your sandbox number has been assigned the default extension (101) however you should assign either a direct / digital line inorder to make/receive a ringout call on the sandbox number.    
* Login to the extension on the “RingCentral for Desktop” application before you initiate a Ringout.
* If the extension is a “From” number then during the first leg of the ringout the “To” number would be displayed and once you dial “1” the second leg of the call would be initiated.
* The same is the case if the extension is a “To” number. 

### How do you check the status of a ringout inProgress ?

To check the current status of a 2-Legged RingOut, make a GET request to the endpoint:
/v1.0/account/{accountId}/extension/{extensionId}/ringout/{ringoutId}

where the accountId and extensionId could be ~ to refer to the current accountId and the extensionId while the ringoutId is a parameter generated for the ringout when the RingOut is initiated. 

For more information please take a look at the API Explorer page here :  
https://developer.ringcentral.com/api-explorer/latest/index.html#/!/RingOut/getRingOutCallStatus


### How does delete RingOut work ?

To Delete a RingOut , you would need to provide the ringoutId as the parameter to cancel out the ringout which is "InProgress" .

API Endpoint : /v1.0/account/{accountId}/extension/{extensionId}/ringout/{ringoutId}

However, DEL works only when the ringout has been initiated and the call has not been connected.

Lets say you initiate a ringout and immediately call the DEL RingOut API Endpoint , the call would get hangup as long as the ringout between the two parties is not connected ( first leg has not been established ) 

If the first leg of the call has been initiated, then the DEL ringout would not hangup the call.
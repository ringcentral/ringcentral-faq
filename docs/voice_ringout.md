# Voice - RingOut FAQ

### How can I make an outgoing call through the API?

An outgoing call can be made programmatically using the RingOut API and WebRTC.

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

### How do CRM applications integrate with RingCentral to display contact names in the caller ID?

This depends upon which direction the call is going, either **inbound** (a customer is calling one of your company numbers) or **outbound** (an agent is calling the customer).

* Inbound - CRM applications will use a `screenpop` which will load the appropriate contact information as defined by the inbound voice call event. There are several ways this could be resolved, but here are the most common:
    * The most common method is to set the URL within a RingCentral SoftPhone. Read the [RC for Desktop User Guide](http://netstorage.ringcentral.com/guides/rc_for_desktop_user_guide.pdf). This enables an agent logged into their RingCentral Soft Phone and the defined URL to cause a `screenpop` in the application with the appropriate contact information.
    * Developers can use the [Push Notification](https://developers.ringcentral.com) API resource to receieve presence events for monitored extensions and then lookup the contact data from within the CRM. Read the community article about how to [Get caller number through URL using GET](https://devcommunity.ringcentral.com/ringcentraldev/topics/get-caller-number-through-url-using-get-command?topic-reply-list%5Bsettings%5D%5Bfilter_by%5D=all&topic-reply-list%5Bsettings%5D%5Breply_id%5D=16178945#reply_16178945)
* Outbound - The caller ID which is displayed to the receiver of an agent RingOut is set within the [RingCentral Online Account Portal](https://service.ringcentral.com). The CRM application will integrate the RingCentral 3-Legged OAuth which will scope the application that the caller ID is set to the currently authenticated user's phone number defined in the Online Account Portal. The only alternative to this is to use our WebRTC service to establish the outbound call which allows configuring the outbound caller ID to be any one of the company approved extension numbers.

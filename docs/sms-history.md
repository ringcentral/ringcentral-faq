# How do I audit the SMS messages I have sent?

There are many ways the RingCentral API can be used to access your communication history. The specific API endpoint you call depends upon the communication medium you are specifically looking for. 

## Auditing past phone calls

To access a history of your company's phone calls, please consult the [Call Log API](https://developers.ringcentral.com/guide/voice/call-log). The RingCentral Call Log is a detailed accounting of every inbound and outbound call received in your account, and can be used to trace a phone call as it is routed from extension to extension. 

## Auditing SMS, voicemail and fax messages

The [RingCentral Message Store](https://developers.ringcentral.com/guide/messaging/message-store/working-with-message-store) is a service and API that keeps track of every telephony-based messages that is sent or received. This includes the following:

* SMS messages
* Voicemail messages
* Faxes
* Pager messages

!!! hint "Pager messages are now very rare"
    Pager messages is like a private SMS message. They can be sent from extension to extension, and never get processed by a carrier. While pager messages are still supported, they are rarely used. RingCentral recommends internal messaging to be done via the [Team Messaging product](https://www.ringcentral.com/teams/overview.html). 
	
## Auditing team chat or team messaging messages

Messages sent via our Team Messaging client, can be accessed using our [Team Messaging Compliance Export API](https://developers.ringcentral.com/guide/team-messaging/manual/compliance-export). This API provides a comprehensive dump of your entire communication history. The export can take some time to produce and therefore can only be called a few times per day.  

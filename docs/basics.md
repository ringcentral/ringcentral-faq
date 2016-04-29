# RingCentral Basics

## General

### What can I accomplish with your APIs?

The [RingCentral Platform](https://developers.ringcentral.com) offers a family of cloud APIs that integrate voice, SMS, and fax communications, as well as provides access to communications data. You can tightly integrate all business communications with your CRM application; send SMS messages and faxes straight from your business apps; seamlessly initiate phone calls and ring out from business applications; analyze call logs to create reports and feed dashboards. See the [RingCentral Developer Library](https://developer.ringcentral.com/api-and-docs.html) for further information.

### Where can I find SDKs, sample code and/or example apps for my language?

SDKs, sample code and example apps available from RingCentral and community authors are linked from the RingCentral Developer Portal SDK page ([https://developer.ringcentral.com/library/sdks.html](https://developer.ringcentral.com/library/sdks.html)). For all official resources, developers can also go the RingCentral GitHub organization page at [https://github.com/ringcentral/]()https://github.com/ringcentral/.

### How do I send text messages to other colleagues within my company using RingCentral through the API?

If you are interested in sending text messages to your internal employees you can take advantage of using company-pager API to send text messages to other users, and use the RingCentral iOS/Android [mobile application](http://www.ringcentral.com/office/features/rcmobile/overview.html) or [RingCentral for Desktop](http://www.ringcentral.com/office/features/desktop-apps/overview.html) to receive them. Through the Advanced Messaging APIs your business application can send unlimited amount of messages. Get more details on how to create pager for your company here.

### How many API calls am I allowed to make per a time period?

There are certain API usage plans which are applied to 3rd party applications which use the RingCentral API. These plans can vary depending on a particular API or a user’s current service plan. But in most cases our servers will reject API requests from a particular application if the request rate exceeds 30 API requests per minute. In this case the client will get an HTTP error with status code 429 “too many requests”.

### Can I give someone access to development with an account in our sandbox account or is a production account required?

There are two basic scenarios:

1. If you want the developer to have full access to the Developer Portal ([https://developers.ringcentral.com](https://developers.ringcentral.com)) to create and configure apps, view analytics, submit for graduation, then the user needs a production account that can be used to log into ([https://service.ringcentral.com](https://service.ringcentral.com)).
2. If you want a developer to have access to the APIs for development and testing, but not have access to the Developer Portal, you can create a user on the sandbox account ([https://service.devtest.ringcentral.com](https://service.devtest.ringcentral.com)) and provide the developer a pre-created app key and app secret to perform development. The sandbox account user will not have access to the production Online Account Portal ([https://service.ringcentral.com](https://service.ringcentral.com)).


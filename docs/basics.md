# RingCentral Basics

## General

### What can I accomplish with your APIs?

The [RingCentral Platform](https://developers.ringcentral.com) offers a family of cloud APIs that integrate voice, SMS, and fax communications, as well as provides access to communications data. You can tightly integrate all business communications with your CRM application; send SMS messages and faxes straight from your business apps; seamlessly initiate phone calls and ring out from business applications; analyze call logs to create reports and feed dashboards. See the [RingCentral Developer Library](https://developer.ringcentral.com/api-and-docs.html) for further information.

### How do I send text messages to other colleagues within my company using RingCentral through the API?

If you are interested in sending text messages to your internal employees you can take advantage of using company-pager API to send text messages to other users, and use the RingCentral iOS/Android [mobile application](http://www.ringcentral.com/office/features/rcmobile/overview.html) or [RingCentral for Desktop](http://www.ringcentral.com/office/features/desktop-apps/overview.html) to receive them. Through the Advanced Messaging APIs your business application can send unlimited amount of messages. Get more details on how to create pager for your company here.

### How many API calls am I allowed to make per a time period?

There are certain API usage plans which are applied to 3rd party applications which use the RingCentral API. These plans can vary depending on a particular API or a user’s current service plan. But in most cases our servers will reject API requests from a particular application if the request rate exceeds 30 API requests per minute. In this case the client will get an HTTP error with status code 429 “too many requests”.

### Can I give someone access to all the development information with an account in our dev sandbox?

There two developer resources of note, the Developer Portal ([https://developers.ringcentral.com](https://developers.ringcentral.com)) that allows you to create and manage apps, and the Sandbox Online Account Portal [https://service.devtest.ringcentral.com](https://service.devtest.ringcentral.com) that allows you to set up accounts for testing purposes. It's possible for a developer to perform development and testing using a Sandbox Online Account Portal account along with a provided application key and application secret. However, this does not provide access to the Developer Portal which enables app creation, configuration and analytics. To login to the Developer Portal, an account on the Production Online Account Portal [https://service.ringcentral.com](https://service.ringcentral.com) is necessary and the same account is used to login to the Developer Portal.

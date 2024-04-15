# Sending group SMS messages via the API

**Question**

I am using PHP SDK to send SMS. When I send to one number it works fine but when I try to send to two numbers I get following error:

    Business operation is not supported

I am currently on sandbox environment so not sure if this is environment specific issue. 

**Answer**

Only a single SMS recipient is currently allowed in order to help prevent unsolicited SMS messages. This is shown in the request example below:

https://developers.ringcentral.com/api-docs/latest/index.html#!#RefSMSMessages.html

For internal company messages sent directly to user extensions, you can use the pager functionality to send to multiple users in a single API call. This is shown in the request example below:

https://developers.ringcentral.com/api-docs/latest/index.html#!#RefPagerMessages.html


# SMS FAQ

## Features

### What is the maximum length of a SMS message?

RingCentral's service sends individual messages up to 160 characters and can concatenate longer messages up to 1000 characters. Longer messages require the receiving carrier to be able to process and combine the messages. Many carriers can do this, however there are a few that do not have this capability yet.

### Is Unicode supported for SMS?

Yes. RingCentral's SMS service supports Unicode and can send SMS in any or multiple languages that are supported.

### What is the rate limit for sending SMS?

Sending SMS via the API is covered by our [Rate Limit Usage Plan](https://developer.ringcentral.com/api-docs/latest/index.html#!#APIRateLimits.html) for the *Medium* API group. There is also a current maximum rate of 50 SMS / extension per minute. To send more than this limit, you can set up multiple extensions, each with its own SMS-enabled phone number, either as a direct number or a digital line.

In addition to the API rate limit, phone number use is governed by the FCC. Currently, RingCentral provides local phone numbers, aka long codes, for SMS and are typically used for non-marketing person-to-person and small-group text use cases. Based on our experience, we recommend sending up to 500 SMS text per long code per day. If you wish to send more than this, contact us our support team to discuss your use case.

### Can I send SMS as the main company phone number?

Yes. To do this, authorize your app using the Operator Extension, `101` by default and then call the API to send an SMS messsage.

### Can I send a SMS message from another extension?

You can only send SMS messages for the extension that has authorized your app.

### Can I send SMS from the main company number and also have multiple users respond to that number?

Yes. To do send the SMS, authorized as the Operator Extension. To have multiple users receive inbound requests, configure the Operator Extension to point to a Call Queue with the users desired.

### Can I send an SMS from a toll-free number?

Yes. Now RingCentral also Supports SMS from a Toll-Free Number.

### What is the maximum number of recipients allowed for MMS?

According to https://developer.ringcentral.com/api-docs/latest/index.html#!#RefSMSMessages.html

> Sending MMS to multiple recipients is supported via Batch request. The number of recipients is limited to 10

## Technical Questions

### How can I get a list of phone numbers that are SMS capable?

First, retrieve a list of phone numbers from the authorized extension by making an API call to the `phone-number` endpoint, for example `account/~/extension/~/phone-number`. Then filter the resulting phone numbers against the `features` property for the value `SmsSender`.

### How can I check SMS history?

You can invoke the Message List API https://developer.ringcentral.com/api-docs/latest/index.html#!#RefMessageList.html with filter `messageType=SMS`.

### What is the API endpoint for InternalMessages permission?

It is for POST `/restapi/v1.0/account/~/extension/~/company-pager`

Ref: https://developer.ringcentral.com/api-docs/latest/index.html#!#RefPagerMessages.html

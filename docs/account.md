# Account Info FAQ

## General

### How can I retrieve my accountId (Where could I lookup my Account ID)?

To retrieve the currently authorizing user's `accountId`, make an API call to the `/restapi/v1.0/account/~` API endpoint which will return the object for the user's account. The `accountId` will be located in the response `id` property value.

### How can I retrieve my extensionId (Where could I lookup my Extension ID)?

To retrieve the currently authorizing user's `extensionId`, make an API call to the `/restapi/v1.0/account/~/extension/~` API endpoint which will return the object for the user's extension. The `extensionId` will be located in the response `id` property value. This will indirectly return the user's `accountId` in the user's canonical URI which is in the response `uri` property value.

### What are the differences between my developer account and my sandbox account?

Your developer account is what you used to login https://developer.ringcentral.com/.

Your sandbox account could be found in "Sandbox Accounts" tab after you logged in https://developer.ringcentral.com/. It is normally in the form of a phone number.

### What do RingCentral account and extension mean, respectively?

In RingCentral API, we often see endpoints like `/restapi/v1.0/account/~/extension/~/...`. So what do RingCentral account and extension mean, respectively?

In RingCentral's terminology, an account normally means a company, an exenstion normally means an user in a company. It's by no means official definition but you can get the overall idea.

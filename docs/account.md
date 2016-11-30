# Account Info FAQ

## General

### How can I retrieve my accountId?

To retrieve the currently authorizing user's `accountId`, make an API call to the `account/~` API endpoint which will return the object for the user's account. The `accountId` will be located in the response `id` property value.

### How can I retrieve my extensionId?

To retrieve the currently authorizing user's `extensionId`, make an API call to the `account/~/extension/~` API endpoint which will return the object for the user's extension. The `extensionId` will be located in the response `id` property value. This will indirectly return the user's `accountId` in the user's canonical URI which is in the response `uri` property value.

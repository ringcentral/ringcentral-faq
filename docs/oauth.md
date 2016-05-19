# Authentication & Authorization FAQ

## General

### Why does OAuth return "unauthorized for this grant type" error?

The error "unauthorized for grant type" occurs when your application is attempting to use an OAuth grant type that it is not approved to use. This often happens when your app requires the Authorization Code Flow but is attempting to use the Password Flow. See below for information in implementing Authorization Code Flow. For more information see [this Developer Community article](https://devcommunity.ringcentral.com/ringcentraldev/topics/unauthorized-for-this-grant-type-error).

### Where can I find example code that implements Authorization Code Flow?

For information on the Authorization Code Flow, please see this [Developer Community post](https://devcommunity.ringcentral.com/ringcentraldev/topics/using-oauth-2-0-authorization-code-grant-to-access-ringcentral-apis).

We have sample demos in a few programming languages including JavaScript, C#, Python, Ruby, etc. in the [`ringcentral-demos-oauth` repo](https://github.com/grokify/ringcentral-demos-oauth).

### How many simultaneous OAuth sessions can my application support?

You can have up to 5 simultaneous OAuth sessions per user per application.

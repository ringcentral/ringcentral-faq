# Why does OAuth return "unauthorized for this grant type" error?

Are you receiving the following error when you call the /oauth/token API to authorize your application?

```js
{
  "error": "unauthorized_client",
  "error_description": "Unauthorized for this grant type"
}
```

There a couple of causes for this error:

* You are trying to use a grant type (e.g. auth token flow or JWT) that is not configured for your application.
* There is an error in your implementation of a given grant type.
* You are attempting to use a grant type that is no longer supported.

!!! hint "Password grant type no longer supported"
   RingCentral no longer supports the use of password auth. It is possible your application lost access to this grant type. Please update your application to JWT or another supported protocol. 

To resolve the problems above, please do the following:

* Consult your app's settings and confirm that your code is using the same auth method that your application is configured to support
* Use a RingCentral SDK to process an authorization request
* And if you have implemented the auth protocol manually, be sure you conform with its technical requirements

Learn more:
* [JWT grant type](https://developers.ringcentral.com/guide/authentication/jwt-flow)
* [Auth token grant type](https://developers.ringcentral.com/guide/authentication/auth-code-pkce-flow)

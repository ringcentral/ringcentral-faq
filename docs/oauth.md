# Oauth FAQ

## General

### Why do i get "unauthorized for this grant type" error, when i try to login using RingCentral oAuth endpoint ?

The error "UnAuthorized for grant type" is because your application is not following the Authorization Code Flow for logging in. 

We have a sample demo in a few Programming Languages like JS, C#, Python and Ruby etc. For more information, please do take a look at our developer community post to assist you more here : 
https://devcommunity.ringcentral.com/ringcentraldev/topics/using-oauth-2-0-authorization-code-grant-to-access-ringcentral-apis 
Here’s the link to the Oauth Demo’s to implement the Authorization Code Flow within your application : https://github.com/grokify/ringcentral-demos-oauth

Please take a look at our Developer Community Article for more information : https://devcommunity.ringcentral.com/ringcentraldev/topics/unauthorized-for-this-grant-type-error 

### Where could i find Demo application to implement Authorization Code Flow ?

For sample Demo's to implement Authorization Code flow within your application, kindly take a look at the repository below :
https://github.com/grokify/ringcentral-demos-oauth

### How many simultaneous oAuth sessions can my application support ?

You can have upto 5 simultaneous oAuth sessions ***Per User Per Application***


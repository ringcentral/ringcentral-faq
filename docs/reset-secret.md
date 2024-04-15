# How do I reset the client secret on the credentials of a production web app?

**Question**

I am receiving unexpected subscriptions created daily at 3AM (probably the result of a cron job) from an unknown source (but probably a previous developer). So I want to reset the client secret, without disrupting the production app. How can I do this? Alternatively, is it possible to identify the origin of where the subscriptions are being created?

**Answer**

There is not currently a way to reset an app's client secret. Therefore, in the above scenario, the recommended thing to do is to clone your existing application. This will result in a new client ID and secret being provisioned to your app. Switch your application that you know is functioning properly to this client ID/secret. Then suspend the old application. This result in new API calls being processed by the newly created app. Any app using the old credentials will now be rejected by our API.

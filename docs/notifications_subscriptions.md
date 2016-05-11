# Notifications & Subscriptions FAQ

## General

### Will I lose events when refreshing the OAuth access token?

No, you should not lose any events during a the OAuth access token refresh process. RingCentral subscriptions last for 15 minutes. To continue your subscription, simply make a `PUT` call to the subscription endpoint with an empty body before the subscription expires. In the event that your OAuth access token has expired, request a new access token using the refresh token or other manner and then make the `PUT` API call. The official RingCentral SDKs will automatically do this for you by updating your subscription every 10 minutes, automatically refreshing the access token if necessary.

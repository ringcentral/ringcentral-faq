# Notifications & Subscriptions FAQ

## PubNub Subscription

### Will I lose events when refreshing the OAuth access token?

No, you should not lose any events during a the OAuth access token refresh process. RingCentral PubNub subscriptions last for 15 minutes. To continue your subscription, simply make a `PUT` call to the subscription endpoint with an empty body before the subscription expires. In the event that your OAuth access token has expired, request a new access token using the refresh token or other manner and then make the `PUT` API call. There is no need to unsubscribe and resubscribe to the subscription during an OAuth refresh. The official RingCentral SDKs will automatically do this for you by updating your subscription every 10 minutes, automatically refreshing the access token if necessary.

## Webhooks

### How can I resolve the "Parameter [deliveryMode.address] value is invalid" error when creating a webhook?

The `Parameter [deliveryMode.address] value is invalid` error indicates that RingCentral cannot connect to the webhook URL properly. This can be for a number of reasons including timeout, invalid response, or SSL/TLS failure. The webhook URL must return within 1 second and respond with a 200 status code. When creating a webhook, the URL must return the `Validation-Token` response header using the value that was sent in the `Vaidation-Token` request header. Common TLS issues can include: TLS isn't enabled, TLS does not chain to a trusted CA certificate, TLS certificate chain is missing, TLS algorithm mismatch, etc.

### How can I verify if SSL/TLS is configured propery for my webhook?

There are a number of requirements for SSL/TLS to work properly including: must be enabled on web service, must change to a trusted CA certificate, must use supported algorithms, etc. To test your site, use the SSL Shopper SSL Checker service at: [https://www.sslshopper.com/ssl-checker.html](https://www.sslshopper.com/ssl-checker.html).

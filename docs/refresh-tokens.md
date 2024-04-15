# How to generate an access and refresh token and how to use them efficiently?

Most developers who implement OAuth will eventually encounter the need to keep auth tokens fresh, and to prevent them from expiring. This article will guide developers on the recommended techniques to keep authentication credentials valid and fresh.

## Using Access Tokens

An "access token" is what a developer presents to the API via an HTTP Authorization header to properly authentication to the API.

* Access tokens expire automatically after one hour (3600 seconds).
* Access tokens can be refreshed using "refresh tokens."

## Using Refresh Tokens

Renew access token and refresh token for every 1 hour. The expires_at time allows a developer to know when you need to refresh an access token and can signal the developer when they should proactively use the provided refresh token to generate a new access token prior to the access token expires. This will ensure that any access token you have stored on behalf of a customer will always be valid, and will not result in the RingCentral API returning an HTTP Status Code of "401 (Unauthorized)."

* Refresh tokens expire after 7 days.
* You can only use a refresh token to refresh an access token that has not expired.
* Immediately upon refreshing an access token, the older/previous token will be invalidated. In other words, there can only be one active access token at a time for user and app.

## Using Access tokens in implicit grant applications

If you are unable to store/persist auth tokens on the backend, and create an external process to keep them fresh, e.g. a stateless or single page app, we recommend you pass the refresh_token_ttl=0 parameter when you call the /oauth/token API so that refresh tokens are expired immediately after creation. This will prevent anyone else from intercepting the refresh token and keeping it alive without you knowing.

## Refresh Strategies

Access tokens last only one hour, while refresh tokens expire after 7 days. Given this, consider implementing a refresh strategy that minimizes the frequency of refreshing. For example:

Refresh access tokens on demand while the refresh token is still valid.
Create an offline service to refresh tokens once a week, and prior to the refresh token expiring.

## Using RingCentral SDKs to help refresh access tokens

We provide developers with SDKs for all major programming languages that automatically handle the reuse of tokens across instances.

# Can I set a localhost URL as an OAuth Redirect URI?

**Question**

Is it possible to set http://localhost/ringcentral/index.php as OAuth Redirect URI?

My app's authorization flows are:
* Authorization Code
* Refresh Access Token

I don't have a live and publicly accessible URL to set as an OAuth Redirect URI, so I don't know how to complete the OAuth process.

**Answer**

Yes, you can set a Redirect URI to your localhost. For OAuth, that is all that is needed because the OAuth redirect is processed by your browser which has access to localhost. 

However, webhook subscriptions, common to many applications, requires a publicly accessible URL to which to deliver events. The best way to achieve that is by using a "reverse proxy." A reverse proxy exposes a URL and then routes requests to that URL to your application via a tunnel. We recommend using [ngrok](https://ngrok.com), a favorite among developers. 

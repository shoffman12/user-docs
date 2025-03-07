# Set up the refresh token exchange

As the `access_token` will expire in a short time, the App will need to frequently request a new one using the `refresh_token`. This must be done while the `refresh_toke`**n** itself is still valid.

To exchange for a fresh `access_token`, make a POST request to the token endpoint (more details found in the [API documentation](https://snykoauth2.docs.apiary.io/#reference/apps/app-tokens/token-exchange-&-refresh)):

```
https://api.snyk.io/oauth2/token
```

with the following properties in a x-www-form-urlencoded formatted request body:

```
grant_type=refresh_token
&refresh_token=(refresh token from the previous step)
&client_id=(clientId from the app creation),
&client_secret=(clientSecret from the app creation)
```

The response to this call provides a new `access_token`, `refresh_token`, and expiry for each.

Be sure to store the new `refresh_token`, as the old one is now invalid.

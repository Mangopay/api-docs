# Authentication

There are two ways to authenticate and communicate with MANGOPAY:
* **Basic Access Authentication**: a fast way to implement our API, however this presents an average security level
* **OAuth 2.0**: simple to implement and a very high level of security

Note that the two methods and all communication with the API is only possible over HTTPS.

**All API communication should be done from your server directly to our server, and not from a user's browser - otherwise your security is easily compromised**

[alert type="info"]If you use [our official SDKs](/guide/sdk-kits), the authentication is handled automatically, and you therefore do not need to worry about this page[/alert]

## Basic Access Authentication

To connect to the API with a standard Basic Access Authentication, the client sends the server authentication credentials using the `Authorization` header. This is constructed as follows:

1. `ClientId` and `Passphrase` are combined into a string separated by a colon, eg "`ClientId`:`Passphrase`"
2. The resulting string is then encoded using [Base64](https://en.wikipedia.org/wiki/Base64) ([here](http://www.motobit.com/util/base64-decoder-encoder.asp) is an online tool to give you an example, but your favourite coding language will be able to do this programmatically)
3. The `Authorization` header is completed by adding "Basic " to the encoded string (please note the space between Basic and the string)

Please see the Wikipedia [article](https://en.wikipedia.org/wiki/Basic_access_authentication) for more info.

Here is an example:

| `ClientId` | `Passphrase` | String to encode in Base64 | Base64 encoded string | Authorization Header |
| -------- | -------- | -------- | -------- | -------- |
| Aladdin     | ghsiu6hjqQjj      | Aladdin:ghsiu6hjqQjj     | QWxhZGRpbjpnaHNpdTZoanFRamo=      | Basic QWxhZGRpbjpnaHNpdTZoanFRamo=     |

With this Authorization Header, you can communicate with our service.

**Security Level**
Using Basic Authentication represents unnecessary level of risk since the `Passphrase` is transmitted in each and every call. This is the reason why we want to limit its exposure by instead using the OAuth 2.0 Authorization method.


## OAuth 2.0 : Client Credentials Grant

To use this second method, you do a particular API call using an `Authorization` header with the Basic Access Authentication method that we just mentioned - this will give you a temporary token that you can use in all subsequent API calls until it expires.

**Once you have your Authorization Header, here is the request you should make to generate an OAuth token:**
> **POST**: https://api.mangopay.com/v2.01/oauth/token/ (change the subdomain to api.sandbox... to use the sandbox environment)
> 
> **Authorization**: Basic czZCaGRSa3F0MzpnWDFmQmF0M2JW
> 
> **Content-Type**: application/x-www-form-urlencoded
> 
> **Form data**:  grant_type=client_credentials


**You can see in the authorization field that we used the Authorization Header produced in the Basic Access method. Making this above request, we get the response:**

```
{
   "access_token": "67b036bd007c40378d4be5a934f197e6",
   "token_type": "Bearer",
   "expires_in": 3600
}
```

We have here in the body the `access_token` we were looking for - from the `expires_in` in this case, it is available for 3600 seconds (although this may vary and therefore you should react accourdingly). While it is available (ie it hasn't expired), you can communicate with our service by adding this token to the `Authorization` header in your HTTP requests in a similar way for the Basic method mentioned above, however instead of adding "Basic ", we add "Bearer " - for example:

```
Bearer 67b036bd007c40378d4be5a934f197e6
```

Once your token has expired, you can just repeat the above step to get a new one. Operating in this way means that you only transmit your very senstive credentials (the `Passphrase`) when you need a token, and not for every single API call. The rest of the time, it is your “tokenized temporary credentials” that are transmitted with every call you make.

[alert type="danger"]You **must not** create a token for every API call you do - only when your token has expired, and you need to replace it[/alert]
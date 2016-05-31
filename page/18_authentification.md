# Authentification

There are two ways to authenticate and communicate with MANGOPAY:
* **OAuth 2.0**: simple to implement, it has a very high level of security
* **Basic Access Authentification**, which is a fast way to implement our API. However, this presents an average security level

**Remark**: the two methods only work over HTTPS.


## Basic Access Authentification

To connect to the API with a standard Basic Access Authentification, the user sends the server authentification credentials thanks to the Authorization Header. The Authorization Header is constructed as follows:

1. Username and password are combined into a string « username:password »
2. The resulting [string](https://en.wikipedia.org/wiki/String_literal) is then encoded using [Base64](https://en.wikipedia.org/wiki/Base64)
3. The authorization method is given by adding “Basic “ to the encoded string (please note the space between Basic and the string)

Please see the Wikipedia [article](https://en.wikipedia.org/wiki/Basic_access_authentication) for more info.

Here is an example:

| Username | Password | String to encode in Base64 | String encoded | Authorization Header |
| -------- | -------- | -------- | -------- | -------- |
| Aladdin     | open sesame      | Aladdin:open sesame     | QWxhZGRpbjpvcGVuIHNlc2FtZQ==      | Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==     |

With this Authorization Header, you can communicate with our service.

**Security Level**
Using Basic Authentification represents unnecessary level of risk since the Passphrase is transmitted in each and every call. This is the reason why we want to limit its exposure by using the OAuth 2.0 Authorization method.

Resource: A base64 encoder : http://www.motobit.com/util/base64-decoder-encoder.asp



## OAuth 2.0 : Client Credentials Grant

To use this second method , you first need to setup the Authentification Header with the Basic Access Authentication method. You will then focus on obtaining a token with OAuth 2.0.

**Once you have your Authorization Header, here is the request you have to make:**
> **POST**: /v2/oauth/token
> 
> HTTP/1.1
> 
> **Host**: server.example.com
> 
> **Authorization**: Basic czZCaGRSa3F0MzpnWDFmQmF0M2JW
> 
> **Content-Type**: application/x-www-form-urlencoded
> 
> **Body**
> 
> grant_type=client_credentials


**You can see in the authorization field that we used the Authorization Header produced in the Basic Access method. Making this above request, we get in response:**

> HTTP/1.1 200 OK
> 
> **Content-Type**: application/json;charset=UTF-8
> 
> **Cache-Control**: no-store
> 
> **Pragma**: no-cache

```
{
"access_token":"67b036bd007c40378d4be5a934f197e6",
"token_type":"Bearer",
"expires_in":3600
}
```

We have here in the body the access_token we were looking for. It is available for 3600 sec. While it is available, you can communicate with our service by adding this “token Authorization Header” in your HTTP requests:
Bearer 67b036bd007c40378d4be5a934f197e6

Once your token has expired, you can get a new token with POST /v2/oauth/token.  Proceeding this way, you only transmit your credentials every 3600 seconds. The rest of the time, it is your “tokenized temporary credentials” that are transmitted with every call you make.
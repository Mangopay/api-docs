# Authentication

There are two ways to authenticate and communicate with MANGOPAY:
* **OAuth 2.0**: simple to implement, it has a very high level of security
* **Basic Access Authentication**, which is a fast way to implement our API. However, this presents an average security level

**Note that the two methods only work over HTTPS.**


## Basic Access Authentication

To connect to the API with a standard Basic Access Authentication, the client sends the server Authentication credentials using the `Authorization` header. This constructed as follows:

1. `ClientId` and `Passphrase` are combined into a string "`ClientId`:`Passphrase`"
2. The resulting string is then encoded using [Base64](https://en.wikipedia.org/wiki/Base64) ([here](http://www.motobit.com/util/base64-decoder-encoder.asp) is an online tool)
3. The authorization method is given by adding "Basic " to the encoded string (please note the space between Basic and the string)

Please see the Wikipedia [article](https://en.wikipedia.org/wiki/Basic_access_authentication) for more info.

Here is an example:

| `ClientId` | `Passphrase` | String to encode in Base64 | Base64 encoded string | Authorization Header |
| -------- | -------- | -------- | -------- | -------- |
| Aladdin     | ghsiu6hjqQjj      | Aladdin:ghsiu6hjqQjj     | QWxhZGRpbjpnaHNpdTZoanFRamo=      | Basic QWxhZGRpbjpnaHNpdTZoanFRamo=     |

With this Authorization Header, you can communicate with our service.

**Security Level**
Using Basic Authentication represents unnecessary level of risk since the `Passphrase` is transmitted in each and every call. This is the reason why we want to limit its exposure by instead using the OAuth 2.0 Authorization method.


## OAuth 2.0 : Client Credentials Grant

To use this second method , you first need to setup the Authentication Header with the Basic Access Authentication method. You will then focus on obtaining a token with OAuth 2.0.

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
# API overview
We provide two environments - one for your live production usage, and one fully functional and free sandbox environment for testing and integration usage:
* **Production:** https://api.mangopay.com
* **Sandbox:** https://api.sandbox.mangopay.com

### How to use the MANGOPAY REST API
We designed the Mangopay API in a very RESTful way, so that your user experience is simple and straightforward ([Wikipedia](https://en.wikipedia.org/wiki/Representational_state_transfer)). You are able to:

* Submit data requires an **HTTP POST** request
* Retrieve data requires an **HTTP GET** request
* Change data requires an **HTTP PUT** request

Requests must be sent using `Content-Type` "application/json". The request and response body encoding is always UTF-8.

## Formats used
**Dates**
All date and time values are displayed as integer numbers and represent the number of seconds since the Unix Epoch (January 1 1970 00:00:00 UTC), like [PHP time()](http://php.net/manual/en/function.time.php) function. The date/time property type in the specification is specified as “Time”, the actual JSON type is “Number”.

**Case Sensitive Parameters**
The field and parameter names in requests are case sensitive.

**ID**
All objects IDs are given as strings (even though their content is actually an integer).

**Amounts**
All monetary amounts are given as integer numbers in cents (by default eurocents).

**Currencies**
You can currently pay and wire funds in these currencies: EUR, USD, GBP, PLN, CHF, NOK, SEK, DKK

The [ISO_4217](https://en.wikipedia.org/wiki/ISO_4217) format is expected

## Response codes
The following HTTP codes are used by the API to respond to requests:

| Response code | Description |
| -------- | -------- | 
|200|Request successful|
|400|Any kind of logical error with your request (missing parameters, invalid operation, constraint violation etc.)|
|403|Access is forbidden (authentication or authorisation failure)|
|404|Object not found|
|405|HTTP method not allowed (for example if you try to update a read-only object)|
|411|Length Required (if the request body is empty for methods that require it)|
|500|Internal server error - we advise you to try again later, or contact support if the problem persists|

**Error Object**

You may get a detailed error description inside an `Error` object.

| Property | Type | Description and value |
| -------- | -------- | -------- |
| `Message` | string | Technical error description |
| `Id` | string | The Unique Tread ID of the error |
| `Date` | timestamp | The error date |
| `Type` | string | Error type. Can be : param_error, ressource_not_found, etc. |
| `errors` | array | The list of the issues which triggered the HTTP error |

**A JSON example**

```
{
  "Message": "One or several required parameters are missing or incorrect. An incorrect resource ID also raises this kind of error.",
  "Type": "param_error",
  "Id": "17c965a1-6cde-4730-910a-b6b02d79b765",
  "Date": 1440424344,
  "errors": {
    "Currency": "The code XPX cannot be found in the standard ISO 4217 : http://en.wikipedia.org/wiki/ISO_4217"
  }
}
```
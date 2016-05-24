The following HTTP codes are used by the API to respond to requests
> **200**: request successful

> **400**: any kind of logical error (missing parameters, invalid operation, constraint violation etc.)

> **403**: access is forbidden (authentication or authorisation failure)

> **404**: object not found

> **405**: HTTP method not allowed (for example if you try to update a read-only object)

> **411**: Length Required (if the request body is empty for methods that require it)

> **500**: internal server error

**Error Object**

You may get a detailed error description inside an «Error» object.

| Property | Type | Description and value |
| -------- | -------- | -------- |
| Message | string | Technical error description |
| Id | string | The Unique Tread ID of the error |
| Date | TimeStamp | The error date |
| Type | string | Error type. Can be : param_error, ressource_not_found, etc. |
| errors | string | The list of the issues which triggered the HTTP error |

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
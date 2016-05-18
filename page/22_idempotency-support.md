All API POST requests have idempotency support – this means you can add an « Idempotency-Key » and corresponding value (that you generate on your side) to your **request header**. This then gives you two clear advantages:

* If you use the same Idempotency Key within 24 hours, we’ll block all but the first one (ie you can rerun your same requests knowing that we’ll only ever treat them once in 24 hours) – this is particularly useful for direct payments
* In the event of a timeout or loss of connection, you can use your Idempotency Key to retrieve the missed API response to view the exact the response we gave for this Idempotency Key that you’d previously used. Remember that this call will only work in the 24 hours after the initial use of the Idempotency Key

You should know that the Idempotency Key must be between 16 and 36 characters and contain only alphanumeric characters or dashes. We strongly recommend using a GUID.

Remember that using an Idempotency Key is entirely optional – if you do not use it, you will simply not have the same duplication protection that it offers and the API will function as normal.
> **Method**: GET

> **URL**: /responses/{{Idempotency-Key}}/

**An example of using your Idempotency Key to view the response you received (An output JSON example)**
```
{
  "StatusCode": "200",
  "ContentLength": "471",
  "ContentType": "application/json; charset=utf-8",
  "Date": "Wed, 13 Jan 2016 22:25:56 GMT",
  "Resource": {
    "Id": "2241581",
    "Tag": null,
    "CreationDate": 1452723955,
    "AuthorId": "1397677",
    "CreditedUserId": null,
    "DebitedFunds": {
      "Currency": "EUR",
      "Amount": 110000
    },
    "CreditedFunds": {
      "Currency": "EUR",
      "Amount": 110000
    },
    "Fees": {
      "Currency": "EUR",
      "Amount": 0
    },
    "Status": "CREATED",
    "ResultCode": null,
    "ResultMessage": null,
    "ExecutionDate": null,
    "Type": "PAYOUT",
    "Nature": "REGULAR",
    "CreditedWalletId": null,
    "DebitedWalletId": "1397678",
    "PaymentType": "BANK_WIRE",
    "BankAccountId": "2241544",
    "BankWireRef": null
  }
}
```

**An example of doing a POST with an Idempotency Key you’ve already used in the last 24 hours (An output JSON example)**
```
{
  "Message": "A resource has already been created with this Idempotency Key",
  "Type": "idempotent_creation_conflict",
  "Id": "bf6cce22-4c12-454f-ac05-ca20c8683735#1452723935",
  "Date": 1452723944,
  "errors": null
}
```
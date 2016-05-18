**Send the request (An input JSON example)**
```
{
"AuthorId": "1208974",
"CardId": "1208983",
"DebitedFunds": {
"Currency": "EUR",
"Amount": 1000
},
"SecureMode": "FORCE",
"SecureModeReturnURL": "https://www.mysite.com/secure?preAuthorizationId=1209003",
}
```

**Get the reply (An output JSON example)**
```
{
"Id": "1209003",
"Tag": null,
"CreationDate": 1388653234,
"AuthorId": "1208974",
"DebitedFunds": {
"Currency": "EUR",
"Amount": 1000
},
"AuthorizationDate": 1388653377,
"Status": "SUCCEEDED",
"PaymentStatus": "VALIDATED",
"ExpirationDate": 1389258177,
"PayInId": "1209008",
"ResultCode": "000000",
"ResultMessage": "Success",
"SecureMode": "FORCE",
"CardId": "1208983",
"SecureModeReturnURL": "https://www.mysite.com/secure?preAuthorizationId=1209003",
"SecureModeRedirectURL": "https://api-test.mangopay.com:443/Redirect/ACSWithoutValidation?token=8139ca555fd74fbbba14a50b7151a3e9",
"SecureModeNeeded": true,
"PaymentType": "CARD",
"ExecutionType": "DIRECT"
}
```
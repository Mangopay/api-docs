**Request (An input JSON example)**

```
{
OwnerName: "Victor Hugo",
UserId: "1345678",
OwnerAddress: "1 rue des Misérables",
IBAN: "FR7618829754160173622224154",
BIC: "CMBRFR2BCME",
Tag: "custom tag"
}
```

**Reply (An output JSON example)**

```
{
"UserId": "1167502",
"Type": "IBAN",
"OwnerName": "Victor Hugo",
"OwnerAddress": "1 rue des Misérables",
"IBAN": "FR7618829754160173622224154",
"BIC": "CMBRFR2BCME",
"Id": "1169675",
"Tag": "custom tag",
"CreationDate": 1383561267
}
```
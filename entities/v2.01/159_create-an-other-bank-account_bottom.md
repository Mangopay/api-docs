**Request (An input JSON example)**

```
{
  	"OwnerName": "Victor Hugo",
	"UserId": "1345678",
  	"OwnerAddress": "1 rue des Misérables",
  	"Country": "MX",
  	"AccountNumber": "12345",
  	"BIC": "12345",
	"Tag": "custom tag"
}
```

**Reply (An output JSON example)**

```
{
  "OwnerAddress": "1 rue des Misérables",
  "AccountNumber": "12345",
  "BIC": "12345",
  "Country": "MX",
  "UserId": "1167502",
  "OwnerName": "Victor Hugo",
  "Type": "OTHER",
  "Id": "1169675",
  "Tag": "custom tag",
  "CreationDate": 1383561267,
  "Active": true
}
```
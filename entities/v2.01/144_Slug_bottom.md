**Request (An input JSON example)**

```
{
	"OwnerName": "Victor Hugo",
	"UserId": "1345678",
	"OwnerAddress": "1 rue des Misérables",
	"InstitutionNumber": "614",
	"BranchCode": "00152",
  	"AccountNumber": "4000860889",
  	"BankName": "My bank",
	"Tag": "custom tag"
}
```

**Reply (An output JSON example)**

```
{
  "OwnerAddress": "1 rue des Misérables",
  "AccountNumber": "4000860889",
  "InstitutionNumber": "614",
  "BranchCode": "00152",
  "BankName": "My bank",
  "UserId": "1167502",
 "OwnerName": "Victor Hugo",
  "Type": "CA",
  "Id": "1169675",
  "Tag": "custom tag",
  "CreationDate": 1383561267
  "Active": true
}
```
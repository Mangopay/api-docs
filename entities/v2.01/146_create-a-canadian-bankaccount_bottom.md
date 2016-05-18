**Request (An input JSON example)**

```
{
  	"OwnerName": "Victor Hugo",
	"UserId": "1345678",
  	"OwnerAddress": "1 rue des Misérables",
	"AccountNumber": "11696419",
	"SortCode": "010039",
	"Tag": "custom tag"
}
```

**Reply (An output JSON example)**

```
{
  "OwnerAddress": "1 rue des Misérables",
  "AccountNumber": "11696419",
  "SortCode": "010039",
  "UserId": "1167502",
  "OwnerName": "Victor Hugo",
  "Type": "GB",
  "Id": "1169675",
  "Tag": "custom tag",
  "CreationDate": 1383561267,
  "Active": true
}
```
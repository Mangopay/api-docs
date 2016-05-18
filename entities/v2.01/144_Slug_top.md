[alert type="info"]
In the case of CAD PayOut, the [textauthor](https://docs.mangopay.com/api-references/users/natural-users/) of the [textPayOut](https://docs.mangopay.com/api-references/pay-out-bank-wire/) should have their address (Address for Natural Users or HeaquartersAddress for Legal Users) completed in their User object.
[/alert]

| Property | Type | Description / Expected values |
| -------- | -------- | -------- |
| BankName *     | string      | (\w{1,50})     |
| InstitutionNumber *     | string      | (\d{3,4})     |
| BranchCode *     | string      | (\d{5})     |
| AccountNumber *     | string      | (\d{1,20})     |

*Required fields to create a CAD BankAccount
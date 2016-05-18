**Object Resources**
Here are all the *BankAccount object* resources.

[v2] OwnerAddress*string*The address of the owner (inferior to 255 chars)

| Property | Type | Description / Expected values |
| -------- | -------- | -------- |
| Tag     | string (inferior to 255 chars)      | Custom data     |
| Type *    | string      | « IBAN »
« GB »
« US »
« CA »
« OTHER »     |
| OwnerName *     | string (inferior to 255 chars)      | The owner of the Bank details     |
| [v2.01] OwnerAddress.AddressLine1 *     | string      | The first line of the user’s address (inferior to 255 chars)     |
| [v2.01] OwnerAddress.AddressLine2     | string      | The second line of the user’s address (optional, and inferior to 255 chars)   |
| [v2.01] OwnerAddress.City *     | string      | The city from the user’s address (inferior to 255 chars)   |
| [v2.01] OwnerAddress.Region     | string      | The region from the user’s address (inferior to 255 chars)   |
| [v2.01] OwnerAddress.PostalCode     | string      | The postal code from the user’s address (must be be alphanumeric – with no spaces)   |
| [v2.01] OwnerAddress.Country *    | string      | The country from the user’s address (Must be an ISO 3166-1 alpha-2 code – 
[textmore info](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) ) |
| UserId     | string      | The user ID of the owner of the bank account     |
| Id     | string      |  The Id of the Bank account details (used into the PayOut)     |
| CreationDate     | Timestamp      |      |
| [BankAccount Datas] *     | string      | Depends on BankAccount Type     |

*Required fields to create a BankAccount

**Required informations for IBAN type**
| Property | Type | Description / Expected values |
| -------- | -------- | -------- |
| IBAN *     | string      | IBAN Format expected     |
| BIC *     | string      | BIC Format expected. If no BIC is supplied, it will be automatically derived     |

**Required informations for GB type**
| Property | Type | Description / Expected values |
| -------- | -------- | -------- |
| AccountNumber *     | string      | (\d+)     |
| SortCode * | string      | (\d+)     |

**Required informations for US type**
[alert type="info"]
In the case of USD PayOut, the [textauthor](https://docs.mangopay.com/api-references/users/natural-users/) of the [textPayOut](https://docs.mangopay.com/api-references/pay-out-bank-wire/) should have their address (Address for Natural Users or HeaquartersAddress for Legal Users) completed in their User object.
[/alert]

| Property | Type | Description / Expected values |
| -------- | -------- | -------- |
| AccountNumber *     | string      | (\d+)     |
| ABA *     | string      | (\d{9})     |
| DepositAccountType     | string      | CHECKING (default) or SAVINGS)     |

**Required informations for CA type**
[alert type="info"]
In the case of CAD PayOut, the [textauthor](https://docs.mangopay.com/api-references/users/natural-users/) of the [textPayOut](https://docs.mangopay.com/api-references/pay-out-bank-wire/) should have their address (Address for Natural Users or HeaquartersAddress for Legal Users) completed in their User object.
[/alert]

| Property | Type | Description / Expected values |
| -------- | -------- | -------- |
| BankName *     | string      | (\w{1,50})     |
| InstitutionNumber *     | string      | (\d{3,4})     |
| BranchCode *     | string      | (\d{5})     |
| AccountNumber *     | string      | (\d{1,20})     |

**Required informations for OTHER type**

| Property | Type | Description / Expected values |
| -------- | -------- | -------- |
| Country *     | string      | The Country associate to the *BankAccount* [textISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) format is expected     |
| BIC *     | string      | Valid BIC format     |
| AccountNumber *     | string      | (\d+)     |
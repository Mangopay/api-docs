Bank Accounts is an item targeted by a Pay-out Bank wire request. This is required in order to process a Pay-out Bank wire, as it contains all bank accounts. It may also be linked to a user (UserId). The API accepts the following formats:
* BIC & IBAN
* [Local UK format](/endpoints/v2#entity_13)
* [Local US format](/endpoints/v2#entity_27)
* [Local CA format](/endpoints/v2#entity_12)
* Other local formats (unspecified but different from the previous).

Please pay special attention on the fact that even in sandbox mode you will need to put a real life existing valid BIC/IBAN since the Mangopay and banks tests are made on the validity of this one.

[alert type="info"]Note that if you are doing a PayOut to someone different from the AuthorId, you should not register the BankAccount under the same UserId – you must create a second UserId – please discuss with our support team if you are unsure about this point, as it is important and will cause your PayOuts to be rejected by our compliance team.[/alert]
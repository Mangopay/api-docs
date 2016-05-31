Bank Accounts is an item targeted by a PayOut Bank wire request. This is required in order to [entity_link entity="227"]process a PayOut Bank wire[/entity_link], as it contains all bank accounts. It may also be linked to a user (UserId). The API accepts the following formats:
* [entity_link entity="40"]BIC & IBAN[/entity_link]
* [entity_link entity="25"]Local UK format[/entity_link]
* [entity_link entity="26"]Local US format[/entity_link]
* [entity_link entity="11"]Local CA format[/entity_link]
* [entity_link entity="174"]Other local formats[/entity_link] (unspecified but different from the previous).

Please pay special attention on the fact that even in sandbox mode you will need to put a real life existing valid BIC/IBAN since the Mangopay and banks tests are made on the validity of this one.

[alert type="info"]Note that if you are doing a PayOut to someone different from the AuthorId, you should not register the BankAccount under the same UserId – you must create a second UserId – please discuss with our support team if you are unsure about this point, as it is important and will cause your PayOuts to be rejected by our compliance team.[/alert]
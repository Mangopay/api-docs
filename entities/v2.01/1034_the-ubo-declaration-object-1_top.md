[alert type="info"]This is a new functionality. All`LegalPersonType`  `BUSINESS` will need to provide their UBO information to have the regular validation. [/alert]

An  `UBO Declaration` is an electronic version of the previous KYC document "Shareholder Declaration", in order to declare all the Ultimate Beneficial Owners of a BUSINESS-typed legal `User` (ie the shareholders with >25% of capital or voting rights).

[alert type="info"] MANGOPAY maintains the possibility of requesting additional documents related to the Account Holder, the beneficial owners, or a specific Payment Operation; before opening an account and at any time during the term of the service usage (Contract article 4.2). If the ultimate beneficial owner (UBO) declared with the dedicated feature cannot be cross-referenced with an official document (Article of association/ registration proof), we will require additional documents (such as the shareholder declaration/share certificate or latest annual report mentioning the UBO) to validate the KYC of this user.[/alert]

Please note that we strongly advice you to start by collecting and sending the KYC documents before collecting the UBO. 
1. Create an UBO Declaration for your legal user.
2. Declare your [entity_link entity="208"]`UBOs`[/entity_link] (ie. Ultimate Beneficial Owner that owns more than 25% of this company or the legal respresentative in case of you don't have UBO). 
3. Edit the UBO Declaration object and set the `Status` field to "VALIDATION_ASKED" (instead of "CREATED")
4. Our team receive the request. Once processed, you will either get a:
								-  "VALIDATED" status: if all other required parameters and KYC documents are validated, the user will receive REGULAR  `KYCLevel` validation
								- "INCOMPLETE" status: complete the  `UBO Declaration` 
                                -  "REFUSED" status: Check the `Reason` and `Message` parameters for more information. You will need to create a new declaration to validate your user.


For any question or a request of switch,  please contact our [support team](https://support.mangopay.com/s/contactsupport?language=en_US)
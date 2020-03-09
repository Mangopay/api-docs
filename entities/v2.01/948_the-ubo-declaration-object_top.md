An `UBO Declaration` is an electronic version of the previous KYC document "Shareholder Declaration", in order to declare all the Ultimate Beneficial Owners of a BUSINESS-typed legal `User` (ie the shareholders with >25% of capital or voting rights).

1. Create each Ultimate Beneficial Owner as a Natural User, who must have a "DECLARATIVE" `Capacity`.
2. Create a new UBO Declaration for your legal user, and link every Ultimate Beneficial Owners created previously thanks to `DeclaredUBOs`. This list can be empty if your legal user has no Ultimate Beneficial Owner, or no eligible one (ie. no Ultimate Beneficial Owner that owns more than 25% of this company).
3. Edit the UBODeclaration object and set the `Status` field to "VALIDATION_ASKED" (instead of "CREATED")
4. The demand is received by our team and once processed, it will either get a "VALIDATED" status, or "REFUSED" with more information provided in the `RefusedReasonTypes` parameter

[alert type="info"]Note that UBO declarations are not **yet** a requirement for your user to be KYC verified and are optional at this stage[/alert]

NEW : 

[alert type="info"]This is a new functionality. You have to integrate it in order to validate the KYC of  your BUSINESS-typed legal `User`[/alert]


An  `UBO Declaration` is an electronic version of the previous KYC document "Shareholder Declaration", in order to declare all the Ultimate Beneficial Owners of a BUSINESS-typed legal `User` (ie the shareholders with >25% of capital or voting rights).

1. Create an UBO Declaration for your legal user.
2. Declare your [entity_link entity="208"]`UBOs`[/entity_link] (ie. Ultimate Beneficial Owner that owns more than 25% of this company or the legal respresentative in case of you don't have UBO). 
3. Edit the UBO Declaration object and set the `Status` field to "VALIDATION_ASKED" (instead of "CREATED")
4. The demand is received by our team and once processed, it will either get a
								 - "VALIDATED" status: if all other required parameters and KYC documents are validated, the user will pas on the `KYCLevel` REGULAR
								 - "INCOMPLETE" status: complete the  `UBO Declaration` or create a new one
								 -  "REFUSED" status with more information provided in the `Reason` and `Message` parameters


-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

As mentionned above, this is a new functionality that will soon be compulsory.  Here are the deadline for implementation:

**I. Sandbox functionality activation**
* For all new client created after 06/04
* By request anytime between 06/04 and 15/08
* All clients will be switch to this new functionality by 20/08

**II. Production functionality activation**
*  For all new client created after  30/04
* By request anytime between 06/04 and 15/10
* All clients will be switch to this new functionality by 15/10

For any question or a request of switch,  please contact our [support team](https://support.mangopay.com/s/)
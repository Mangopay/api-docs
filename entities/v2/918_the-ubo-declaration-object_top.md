An  `UBO Declaration` is an electronic version of the previous KYC document "Shareholder Declaration", in order to declare all the Ultimate Beneficial Owners of a BUSINESS-typed legal `User` (ie the shareholders with >25% ownership).

1. Create each Ultimate Beneficial Owner as a Natural User, who must have a "DECLARATIVE" `Capacity`.
2. Create a new UBO Declaration for your legal user, and link every Ultimate Beneficial Owners created previously thanks to `DeclaredUBOs`. This list can be empty if your legal user has no Ultimate Beneficial Owner, or no eligible one (ie. no Ultimate Beneficial Owner that owns more than 25% of this company).
3. Edit the UBODeclaration object and set the `Status` field to "VALIDATION_ASKED" (instead of "CREATED")
4. The demand is received by our team and once processed, it will either get a "VALIDATED" status, or "REFUSED" with more information provided in the `RefusedReasonTypes` parameter

[alert type="info"]Note that UBO declarations are not **yet** a requirement for your user to be KYC verified and are optional at this stage[/alert]
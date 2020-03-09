**The PreAuthorization Object** ensures the solvency of a registered card for 7 days. 
The overall process is as follows:
1. Register a card (CardRegistration)
2.  Create a PreAuthorization with the CardId. This allows you to charge an amount on a card
3.  Charge the card through the PreAuthorized `PayIn` object (Payins/preauthorized/direct)

How does PreAuthorization work?

* Once the `PreAuthorization` object is created the `Status` is "CREATED" until 3D secure validation.
* If the authorization is successful the status is "SUCCEEDED" if it failed the status is "FAILED".
* Once `Status` = "SUCCEEDED" and `PaymentStatus` = "WAITING" you can charge the card.
* The Pay-In amount has to be less than or equal to the amount authorized.

[alert type="info"]In Italy, Greece and Spain, the pre-authorization has a particular running. In fact, the pre-authorized amount is debited from the bank account. Pre-authorized funds are stored by the bank. The user will get his/her funds back within 7 days.
**This case appears on several Banks (we don’t have exhaustive list) in Spain, Italy and Greece. Mangopay recommends you to inform your users or only create €1.00 pre-authorizations in these countries.**[/alert]

**Note that a preauthorization is [entity_link entity="186"]automatically cancelled[/entity_link] after the `ExpirationDate` if you do not cancel it yourself, nor do a payin with it**
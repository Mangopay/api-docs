**Pre-authorized a card** before the Pay-In ensures the solvency of a registered card for 7 days. Beyond this period, it is still possible to charge the card (PayIns/Card/Direct) but funds are not guaranteed.

The overall process is as follows:
* Register a card (CardRegistration)
* Create a PreAuthorization with the CardId. This allow you to charge an amount on a card.
* Charge the card through the PreAuthorized PayIn object (Payins/preauthorized/direct).

How PreAuthorization + validation (Pay-In) works?

* Once the `PreAuthorization` object gets `Status` = "SUCCEEDED" and `PaymentStatus` = "WAITING" you can charge the card.
* The Pay-In amount has to be less than or equal to the amount authorized.
* The Preauthorization can be used only once, even if the payin amount is less than the preauthorized amount.

**Remember that you must include the "Powered by MANGOPAY" banner on your payment page - you can download it [here](https://www.mangopay.com/terms/powered-by-mangopay.png)**


[alert type="info"]In Italy, Greece and Spain, the PreAuthorization process is a little particular whereby the pre-authorized amount is actually debited from the bank account (the pre-authorized funds are stored by the bank). The user will get his/her funds back within 7 days.

This case appears on several Banks (we don’t have exhaustive list) in Spain, Italy and Greece. Mangopay recommends you to inform your users or only create €1.00 pre-authorizations in these countries.[/alert]

[alert type="info"]Note that some banks do not have the same limits for preauths as normal payins - some users may even need to contact their bank prior to preauthorising very large amounts[/alert]
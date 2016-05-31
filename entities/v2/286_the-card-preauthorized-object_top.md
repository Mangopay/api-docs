**Pre-authorized a card** before the Pay-In ensures the solvency of a registered card for 7 days. Beyond this period, it is still possible to charge the card (PayIns/Card/Direct) but funds are not guaranteed.

The overall process is as follows:
* Register a card (CardRegistration)
* Create a PreAuthorization with the CardId. This allow you to charge an amount on a card.
* Charge the card through the PreAuthorized PayIn object (Payins/preauthorized/direct).

How PreAuthorization + validation (Pay-In) works?

* Once the « PreAuthorization » object gets « Status » = « SUCCEEDED » and « PaymentStatus » = « WAITING » you can charge the card.
* The Pay-In amount has to be less than or equal to the amount authorized.
* The Preauthorization can be used only once, even if the payin amount is less than the preauthorized amount.

[alert type="info"]There is a KYC limit on Pay-Ins in order to fight fraud, money laundering and financing of terrorism. You have to send some documents through the API. [Please check the rules to go over the limits](http://demo.dev-app.net/guide/cashinout-limitations)[/alert]

[alert type="info"]In Italy, Greece and Spain, the pre-authorization has a particular running. In fact, the pre-authorized amount is debited from the bank account. Pre-authorized funds are stored by the bank. The user will get his/her funds back within 7 days.

This case appears on several Banks (we don’t have exhaustive list) in Spain, Italy and Greece. Mangopay recommends you to inform your users or only create €1.00 pre-authorizations in these countries.[/alert]
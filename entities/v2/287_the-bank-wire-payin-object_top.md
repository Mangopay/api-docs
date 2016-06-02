**A bank wire PayIn** is a request to process a payment by bank wire. The workflow is the following:
* Call the /payins/bankwire/direct object. You’ll receive MANGOPAY bank account details and a reference.
* Display this information to your user
* The user has to proceed a Bank wire to the display bank account with the reference
* Once MANGOPAY receive the payment the e-money is created and the targeted e-wallet is credited.

[alert type="info"]There is a KYC limit on Pay-Ins in order to fight fraud, money laundering and financing of terrorism. You have to send some documents through the API. [Please check the rules to go over the limits](/guide/kyc)[/alert]
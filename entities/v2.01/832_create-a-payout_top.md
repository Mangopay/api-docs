A few important things to note regarding payouts: 
* In the production environment BankWire PayOuts will have a "CREATED" `Status` until they are treated by our compliance team (which happens several times a day)
* In the sandbox environment BankWire PayOuts will be processed automatically (you must contact us if you need to test a FAILED payout)
* When you created the **production ClientId** you filled the field `Name` which will be used on your users bank statements
* A Bankwire could fail after it’s passed to "SUCCEEDED" – in this case, a refund of the PayOut will be made. More info is available [here](/guide/errors) under "Payout error codes"
* In the production environment, if you payout is stuck in "CREATED", this might be because you uploaded a KYC document for this user and it is pending processing
* If a user does not have the sufficient KYC level for this payout, it will automatically pass to "FAILED" - [more info](/blog/important-updated-payout-workflow)
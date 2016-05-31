A **PayIn Refund** is a request to reimburse a user on their payment card. The money which has already been paid will automatically go back to the user’s bank account.
* Minimum amount to refund is 1€.
* If you're doing a partial `Refund`, note that you can only refund the same amount on the same transaction once per day (this is to prevent unintended duplicate refunds). After 24h you can do another refund of the **same amount** on the same transaction. If it is a different amount on the same transaction, there is not this limit. 

[alert type="danger"]You CAN refund [entity_link entity="278"]Direct Payin[/entity_link], some [entity_link entity="269"]WEB Payins[/entity_link] and a [entity_link entity="279"]Preauthorization Payin[/entity_link].[/alert]

[alert type="info"]If you do not specify `DebitedFunds` and `Fees` parameters, it will automatically fully refund the `PayIn`. However if you *do* provide one or the other, you must provide both. Note that `Fees` must be negative if you wish to refund them - adding a positive value for the `Fees` is a way to charge your customers for the `Refund` (in the same way you might for a `PayIn`, `Transfer` or any other `Transaction`[/alert]
**A PayIn by direct debit with a mandate** is a request to process a payment to a wallet for a dedicated user.
* To use this payin method, you must have already created and submitted a [entity_link entity="230"]`Mandate`[/entity_link] (in a similar way to doing a direct card payin)
* Late failures: note that due to the nature of this payment method, it is possible to have a "late failure" which is when the payment Status is already "SUCCEEDED" but later on, the bank pulls back the funds and to reflect that in the API, we will create a [entity_link entity="176"]`Dispute`[/entity_link] (and hence `Repudiation`) with the DisputeReasonType being "LATE_FAILURE" which gives more information regarding the reason. In BACS (UK) **the majority** of late failures happen within 2/3 days. In SEPA, **all** late failures are within 5 days.
* Refunds **are** available for these PayIns, but you should know that a user can also dispute a payment and his bank will automatically refund it (for SEPA payments, this can be up to 8 weeks after the payment was made; for BACS, there is no time limit for a dispute) – there is no way to contest these decisions and we will create a normal [entity_link entity="176"]`Dispute`[/entity_link]
* Payment for direct debit payins is not taken instantly, and there will therefore be a delay before the transaction has the`Status` of "SUCCEEDED". In the majority of cases, the timing is as follows:

| Scheme | Payments with this mandat | Payment is created | User notified | Payment becomes "SUCCEEDED" |
| -------- | -------- | -------- | -------- | -------- |
| SEPA | 1st payment | D+0 | D+3 | D+8 |
| SEPA | 2nd+ payment | D+0 | D+0 | D+5 |
| BACS | 1st payment | D+0 | D+1 | D+6 |
| BACS | 2nd+ payment | D+0 | D+0 | D+5 |

* As with the submission of a mandate, we will notify the user of all upcoming payments on your behalf (the design of this email can be lightly customised – see [entity_link entity="200"]here[/entity_link])
* For testing payments, you should use a specific value for the FirstName of the user owning the mandate
1. "Successful" will result in a successful payment
2. "Penniless" will result in a failed payment due to lack of funds
3. "Fickle" will result in a successfull payment, which is disputed by the user and hence a dispute is created
* [entity_link entity="230"]Mandate[/entity_link] and direct debit payins are only available for certain business types, and is not activated by default – please contact your sales manager for more info
* Note that there is a limit of 2500EUR/GBP per direct debit payment – please contact your sales manager if you require a higher limit
* For BACS payments, you should know that the banks Natwest, RBS, HSBC, Metro and Nationwide will not show your client name with payments, and only "MANGOPAY" will be shown
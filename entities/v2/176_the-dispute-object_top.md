**The Dispute Object** is used when a `User` requests a chargeback of *transaction* to their bank – in turn, their bank withdraws the funds from us and we will then *repudiate* the required funds from your client *credit wallet*.

# Dispute process overview:

1. A [`PayIn`](http://demo.dev-app.net/guide/payment-methods-overview) is completed successfully
2. The end user contacts their bank to request a chargeback
3. The bank contacts us and withdraws the funds automatically
4. We create a “[entity_link entity="176"]`Dispute`[/entity_link]” object in the API – you will receive an email by default, and can also set up the usual [entity_link entity="246"]Hooks[/entity_link] if you like
5. Along with the Dispute, we will also [repudiate](http://demo.dev-app.net/endpoints/v2#e221_the-repudiation-object) the funds from your credit wallet (the amount in the original wallet will therefore remain unchanged which is different to the previous process)
6. If the Dispute is contestable, you are able to contest this Dispute and submit evidence to try to reverse the repudiation and reclaim the funds (note that you do not have to contest the full amount) – evidence might include a delivery note, a refund you’ve already done etc but will depend on the type of Dispute. The evidence is submitted as documents, just like for the current KYC process
7. Once we’ve verified the [Dispute documents](http://demo.dev-app.net/endpoints/v2#e214_the-dispute-document-object), we will pass them on to the relevant bank, and they will either:
* Accept the contest and refund the funds you had contested (we will then refund this amount to your credit wallet)
* Reject the contest – in which case the Dispute will be closed as you have lost
* Ask for further documents – in this case, we will reopen the Dispute and ask you to submit further evidence – check the StatusMessage field for more info
8. n the event you have credit following a Dispute (because you lost, or didn’t contest the full amount), you can do a [settlement transfer](http://demo.dev-app.net/endpoints/v2#e237_the-settlement-transfer-object) to transfer funds from the original wallet to the credit wallet if you wish – this is entirely optional and will depend on your workflow whether you want to impact the original wallet or not
9. Any credit in your credit wallet will be deducted from your fees when you are billed each month before we send you your usual invoice

![alt](http://demo.dev-app.net/uploads/medias/dispute_process.png)

# Important notes:
* You are strongly advised to use the available hooks to be notified (and therefore act on the changes from your side) of Dispute status changes (for example, in the case of a Dispute being reopened because more documents are required, you will not be notified by email – only via the hooks)
* All contestable disputes have a date by which they can be contested – after this time, no further action is permitted from your side
* Banks can sometimes issue a warning of a chargeback that may happen – in this case, we will still create a Dispute (with the DisputeType of “RETRIEVAL”) and require you to send various documents, however there will be no funds repudiated from your credit wallet in this case
* Some Disputes are not contestable (they’ll have the DisputeType of “NOT_CONTESTABLE” as opposed to “CONTESTABLE”) – this means they’ll be closed just after being created and no further action is possible from your side
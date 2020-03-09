# Dispute management
In a credit card or debit card account, a dispute is a situation in which a customer questions the validity of a transaction that was registered to the account. Customers dispute charges for a variety of reasons, including unauthorized charges, excessive charges, failure by the merchant to deliver merchandise, defective merchandise, dissatisfaction with the product(s) or service(s) received, or billing errors. 

## Dispute types:
* **Contestable dispute** This is the most commun type of disputes. It gives you the possibility to contest the chargeback by giving proofs to justify the original transaction. 
* **Not contestable dispute** This means they’ll be closed just after being created and no further action is possible from your side. You can still settle the funds.
* **Retrivial dispute** Banks can sometimes issue a warning of a chargeback that may happen – in this case, we will still create a Dispute (with the DisputeType of “RETRIEVAL”) and require you to send various documents, however there will be no funds repudiated from your credit wallet in this case.


## Dispute process overview:
**STEP 1. New dispute**
* After a successfull payment on your platform, an end user contacts his bank to request a chargeback. 
* The bank contacts us and withdraws the funds automatically
* We create a dispute and repudiate (withdraw) the funds from your credit wallet/repudiation wallet (the amount in the original wallet will therefore remain unchanged which is different to the previous process)

**STEP 2. Contest the dispute**
* If the dispute type is Contestable or Retrivial, you can either close the dispute (ackwnoledge the fraud) or contest the dispute by its full or partial amount. The bank defines a deadline to  contest the payment. 
* In this case we invite you to send [entity_link entity="214"]proofs[/entity_link] to justify the legality of the transaction. It can be a delivery proof, an invoice, a refund proof ect...
* Once we’ve verified the [entity_link entity="214"]Dispute documents[/entity_link], we will pass them on to the relevant bank, and they will either:
-  Accept the contest and refund the funds you had contested (we will then refund this amount to your credit wallet/repudiation wallet)
-  Reject the contest:  in which case the Dispute will be closed as you have lost
-  Ask for further documents :  in this case, we will reopen the Dispute and ask you to submit further evidence – check the StatusMessage field for more info

**STEP 3. Settle the funds**
1.  If the contest is accepted by the bank, we will automatically refund the amount to your credit wallet/repudiation wallet.  
2. If the contest is lost, partially won or of type NOT contestable you will still have credit on your credit wallet/repudiation wallet. You can then do a [entity_link entity="237"]settlement transfer[/entity_link] to transfer funds from the original wallet to the credit wallet if you wish – this is entirely optional and will depend on your workflow whether you want to impact the original wallet or not. 
NB: Any credit in your credit wallet will be deducted from your fees when you are billed each month before we send you your usual invoice.

## How to solve a dispute on the dashboard
[alert type="info"]Note you are able to see on the homepage of the dashboard the number of open dispute you have  [/alert]
You can access open dispute throught the dashboard homepage by clicking on the *dispute pending client* block. You can also click on *Payment disputes* on the  left side menu and then filter the Payment disputes with button *Pending client*.

**DASHBOARD Homepage**

![alt](/uploads/medias/Homedispute.png)


**Payment Dispute List**
On this list if you apply the *Pending client* filter, you will be able to see all the open/new disputes and the reopened one (when the bank ask for further documents)

![alt](/uploads/medias/Pendingdispute.png)


**Dispute details page**
On the dispute details page you can access all the details of the dispute.  Check the *pending action from you* block that will give you all the information you need to have about the next steps. On the top of this block you will be able to check the timeline.

![alt](/uploads/medias/Disputedetails.png)


**Dispute  responce pop-in**
Once you click on the *respond dispute* button you can either close the dispute (for next step go down to *How to settle the funds*) or contest the payment

![alt](/uploads/medias/Contestpopin.png)


**Contest amount pop-in**
You can choose to contest the full amount or a partial amount of the dispute.

![alt](/uploads/medias/Disputeamount.png)


**Upload document pop-in**
You need to upload proofs to justify the legality of the transaction:
1. Choose a type
2. Click in the doted box, choose one document, upload it. Renew this operation until you have uploaded all the pages of the proof.
3. Click on *Add this proof* 
Redo step 1,2,3 if you have multiple proof type. Ex: One delivery proof and an invoice
4. Press validate

![alt](/uploads/medias/Disputedocupload.png)

**Review step**

After that, Mangopay will review the document and then send it to the bank. The bank will then give an answer:
-  Accept the contest and refund the funds you had contested (we will then refund this amount to your credit wallet/repudiation wallet). No more action is required for you. 
-  Reject the contest:  in which case the Dispute will be closed as you have lost. For next step go down to *How to settle the funds*
-  Ask for further documents :  in this case, we will reopen the Dispute and ask you to submit further evidence – check the StatusMessage field in the dispute details page for more info.

In the meantime you can check the documents you uploaded by clicking on the number situated in the *documents* block on the right side of dispute details page. A popin will appear with all the info about the dispute documents. If you click on the eye, you will be able to see the documents.

![alt](/uploads/medias/Documentslist.png)

**Further info required**
[alert type="info"]Note you are able to see on the homepage of the dashboard the number of open dispute you have  [/alert]
You can access open dispute throught the dashboard homepage by clicking on the *dispute pending client* block. You can also click on *Payment disputes* on the right left side menu and then filter the Payment disputes with button *Pending client*.

* Click on the dispute. 
* On the dispute page, read the *Pending client action* block carrefully. And press *Respond dispute*. 
* A pop-in will appear. You can either close the dispute (for next step go down to *How to settle the funds*) or upload documents.
* You can upload documents as you did previously

![alt](/uploads/medias/Uploaddocu2.png)

## How to settle the funds
[alert type="info"]Note you are able to see on the homepage of the dashboard the number of dispute to settle  [/alert]
You can access  dispute to settle throught the dashboard homepage by clicking on the *To settle* block on the right. You can also click on *Payment disputes* on the  left side menu and then filter the Payment disputes with button *To settle*.


**DASHBOARD Homepage**

![alt](/uploads/medias/Homedispute.png)

**Payment Dispute List**
On this list if you apply the *To settle* filter, you will be able to see all the closed dispute that have not yet been settled.

![alt](/uploads/medias/Pendingdispute.png)

**Dispute details page**
On the dispute details page, on the right block *Pending action from you* you can press the button *settle funds*.
A popin will appear, you only have to validate and the funds will automatically transfer funds from the original wallet to the credit wallet if you wish.

![alt](/uploads/dispute_to_settle.png)

![alt](/uploads/medias/Settle.png)

## How to check your repudiation account details

1. Click on the top right icon, press account
2. Press account balance
3. Filter the list by pressing on the "repudiation account" filter

![alt](/uploads/repudiation_account.png)
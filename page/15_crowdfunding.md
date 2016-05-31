# Integrating MANGOPAY for a Crowdfunding platform
**I am developing a Crowdfunding platform. How to implement MANGOPAY?**

## Workflow
MANGOPAY highly recommends to use the following workflow for any crowdfunding businesses. If you have specific needs which are not mentioned here please [take a tour to our desk or contact the support team.](https://mangopay.desk.com/)

![alt](/uploads/medias/CF.png)

According to this diagram, here is the workflow you can use through your application.
* Once a Project owner account is created on your application side, your server says to MANGOPAY to create a User. One this user creates a project, your server creates and associate a Project e-wallet.
* Once a contributor account is created on your application side, your server says to MANGOPAY to create a User and to automatically associate a e-wallet.
* The User buyer pays into its own wallet. Funds are NOT escrowed there, they are directly transferred into the project e-wallet.
* If the project is funded you then can do a payout into the project owner’s bank account.
* If the project had failed you can refund everybody by first bringing the money back to their wallets then refund into their bank account

Let’s take an example:
* A user contributes 100€
* This user pays on the app
* 100€ arrives in the user’s wallet.
* You simultaneously transfer the money into the projet wallet.
* The funds stay there until the end of the project.
* If the project is funded
*  * The project owner received his/her funds into a Bank account minus your own fees.
*  * So you take your fees on this PAYOUT BankWire (withdrawal). Let’s say you take a 10% fee.
*  * The project owner will receive €90 on bank account.
* If the project FAILED
*  * All the payers/contributors are reimbursed. Here the user-payer gets the €100 back into his wallet. He/she can invest it into another project.
*  * Or you can reimburse the credit card.

## Create Contributors and Project owners
MANGOPAY do not distinguish Contributors and Project owners. They all are users through the solution so your application has to make the difference between them.

[entity_link entity="254"]Here is the dedicated documentation for a Natural user[/entity_link]

[entity_link entity="258"]Here is the dedicated documentation for a Legal user (Companies or organizations)[/entity_link]

For instance, create a Natural-User-request with the following info:
```
{
"FirstName": "William",
"LastName": "Shakespeare",
"Address": "",
"Birthday": 1300186358,
"Nationality": "GB",
"CountryOfResidence": "GB",
"Occupation": "",
"IncomeRange": "",
"ProofOfIdentity": null,
"ProofOfAddress": null,
"PersonType": "NATURAL",
"Email": "victor@hugo.com",
"Tag": "",
}
```

[alert type="info"]You can add a tag to make comparisons with your data like : « Contributor – internalID: 12345678 »[/alert]

## Update a User profile
A user can update its profile information. Technically, the backend method is a PUT request on the User ID. Regarding the KYC rules, users might have to upload some proof of identity.

[entity_link entity="204"]All about KYC technical methods is here[/entity_link]

Here is a summary for the KYC management. Let’s take a Natural User case:

**1. Create a Document.**
* Method: POST
* URL: /users/{UserId}/KYC/documents/
```
{Type: "IDENTITY_PROOF", Tag: "custom tag",}
```

**2.Post Base64 page.**
* Method: POST
* URL: /users/{UserId}/KYC/documents/{documentsId}/pages
```
{"File": "/9j/4AAQSkZJRgABAgEASABIAAD/AAABDAEyAAIAAAAUAAABKAE7AAIAAAAT…(truncate example) }
```

**3. Update the status of the created doc**
* Method: POST
* URL: /users/{UserId}/KYC/documents/{document_id}
```
{"Status": "VALIDATION_ASKED",}
```

## PayIn - Cash in payments
Here are the front end steps, for the user

1. The Buyer buys a €50 item and clicks on “Pay now”.
2. The Buyer is redirected to the payment page.
3. The Buyer has payed.

Technically speaking

You will need the CardRegistration and the Direct Payin APIs.

**1. The Buyer a €50 item and clicks on “Pay now”**

* The application creates a CardRegistration object/li>
* You’ll receive a JSON object with 3 interesting data at the stage:
1. the accesskey
2. the PreRegistrationData
3. CardRegistrationURL
4. Here is a returned sample
```
{
"Id": "1169423",
"Tag": null,
"CreationDate": 1383408863,
"UserId": "1167492",
"AccessKey": "1X0m87dmM2LiwFgxPLBJ",
"PreregistrationData": "S8HjKhXaPXeNlzbaHMqIv5ahx5EnS5jTkJowsAs6NUgDqe8Z5Lh ",
"RegistrationData": null,
"CardId": null,
"CardRegistrationURL": "https://homologation-webpayment.payline.com/getToken",
"ResultCode": null,
"ResultMessage": null,
"Currency": "EUR",
"Status": "CREATED"
}
```
* You collect the useful data from the returned object
* So the payment form on your HTTPS page has to directly POST the following data to the CardRegistrationURL:
1. the Accesskey (hidden for the user)
2. the PreRegistrationData (hidden for the user)
3. CardNumber
4. Expiry date
5. CVV
* [Here is our JS KIT including the card registration form](https://github.com/MangoPay/cardregistration-js-kit)

**2. The user Buyer is redirected to the payment page**

Once the Buyer fills out the form and clicks on the validation button, you post the data on the CardRegistrationURL, then receive a key which has to be added into the CardRegistration Object (PUT method). Finally, you instantly get a CardID back (the field was previously empty). This is a unique ID.

**3. The user Buyer has payed**

Actually, the user has now finished the work. Your server now creates a Direct PAYIN request using the CardID. This is totally transparent for the user and there is no interface here. Bellow, an example of a Direct PAYIN:
```
{
AuthorId: "1167492",
DebitedFunds: {Currency: "GBP", Amount: 5000},
Fees: {Currency: "GBP", Amount: 0},
CreditedWalletId: "1167810",
CardId: "1262419",
SecureMode:"DEFAULT",
SecureModeReturnURL:"https://www.mysite.com"
}
```

[alert type="info"]
* the CreditedWalletId is the buyer’s wallet
* the AuthorID is the ID of the User-buyer
* the CreditedUserId is the ID of the User-buyer too
[/alert]

## Validation - Transfer
You have to directly transfer the funds to the project e-wallet. This operation is transparent for the user. [entity_link entity="224"]Here is the Transfer API[/entity_link]. Now the funds belong to the Seller.

Following the €100 example, here is an example of the transfer:
```
{
AuthorId : "12345678",
CreditedUserId : "87654321",
DebitedFunds: {Currency : "EUR", Amount : 10000},
Fees : {Currency : "EUR", Amount : 0},
DebitedWalletID : "0987654",
CreditedWalletID : "4367890",
Tag : "DefaultTag"
}
```

[alert type="info"]
* The CreditedWalletID is the project e-wallet
* The DebitedWalletID is the Buyer’s wallet
* The CreditedUserID has to be the the buyer/contributor
* The AuthorID has to be the ID of the buyer/contributor too
[/alert]

## Refund
If a project hasn’t been funded you will reimburse the contributors or if a single buyer wants to get his/her money back, you have to create one or several Transfer-Refunds. The way, the money goes into the Buyer’s wallet and he/her can re-invest it into another project. Or you can even refunded into the credit card (Transfer-Refund + Payin-Refund).

[entity_link entity="189"]Here is the Transfer-Refund API[/entity_link]

[entity_link entity="191"]Here is the PayIn-Refund API[/entity_link]

![alt](/uploads/medias/refundCF.png)

[alert type="info"]You only can refund Buyer if the all the stored funds remain into the project wallet. If €1 has been cashed out or transferred, you will not be able to automatically reimburse contributors.[/alert]

## The cash out for the project owner
The project owner just collected the €1000. He is now able to withdraw its funds. Here are the steps:
1. Register the bank details
2. Ask for a withdrawal
3. Wait during 2 days max
4. Receive funds on bank account

Technically speaking here are the requests:
First you have to [entity_link entity="15"]register the bank details[/entity_link]
```
{
OwnerName: "Victor Hugo",
UserId: "1345678",
Type: "IBAN",
OwnerAddress: "1 rue des Misérables",
IBAN: "FR7618829754160173622224154",
BIC: "CMBRFR2BCME",
Tag: "custom tag"
}
```

Now you can [entity_link entity="228"]Ask for a withdrawal[/entity_link]
```
{
Tag:"custom tag",
AuthorId:"12567875",
DebitedFunds:{ Currency:"EUR", Amount:"4500"},
Fees:{ Currency:"EUR", Amount:"0"},
DebitedWalletId:"12449234",
BankAccountId:"12449209",
}
```

Wait during 2 days maximum. All the payout requests are treated several times every working days by a dedicated MANGOPAY team. Once it is done, the status changes:
* CREATED : the request is created but not treated yet
* SUCCEEDED : the request has been successfully processed
* FAILED : the request has failed.

Then, there is an interbank delay. It can take up to two days for the seller to get his/her funds.

[alert type="info"]Do not let the funds going out of the wallet if all the contributors who could be reimbursed. You only can refund Buyers if the all the stored funds remain into the project wallet. If €1 has been cashed out or transferred, you will not be able to automatically reimburse contributors.[/alert]

## Collect your fees
You can collect your fees when the project has been funded so on the Project owner PAYOUT.

Ask for a withdraw

As you know MANGOPAY calculates its fees on the cash-in payments. The user is never directly charged by MANGOPAY. You, as a platform, you are charged by MANGOPAY when you collect your fees. These fees are stored into a particular wallet created by mangopay specially for your platform, you do not have access to this wallet. At the end of the month MANGOPAY automatically sends the collected fees, minus mangopay fees into your bank account.

Best place to take fees in a crowdfunding model, is when you do the payout from the project’s walelt and the project owner bank account, once the project Is finished and correctly completed. The API only understands cents amounts.

Let’s take a example:
There are 1000€ into the Project owner’s wallet. The project is finished and correctly completed, the app orders to payout the amount. Your platform takes 10% fees so the app calculates the amount before creating the MANGOPAY request. Here it is 1000*10/100 = 100€. The project owner receives in his bank account 900€. The 100€ fees are collected into a fees wallet created by MANGOPAY specificly for your platform. You don’t have access to that wallet.

The project owner withdrawal
The project owner collected the entire amount needed for the project lets say 1000€. The project is finished and correctly completed, the app orders to payout the amount. Your platform takes 10% fees so the app calculates the amount before creating the MANGOPAY request. Here it is 1000*10/100 = 100€. The project owner receives in his bank account 900€. The 100€ fees are collected into a fees wallet created by MANGOPAY specificly for your platform. You don’t have access to that wallet.
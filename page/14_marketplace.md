# Integrating MANGOPAY for a Marketplace
**I am developing a Marketplace. How to implement MANGOPAY?**

## Workflow
MANGOPAY highly recommends to use the following workflow for any marketplaces business. If you have specific needs which are not mentioned here please [take a tour to our desk or contact the support team](https://mangopay.desk.com/).

![alt](http://demo.dev-app.net/uploads/medias/Capture-d’écran-2014-12-01-à-10.29.47.png)

According to this diagram
* Once a seller account is created on your application side, your server says to MANGOPAY to create a User and to automatically associate a wallet. The Seller and its seller’s wallet are created.
* Once a buyer account is created on your application side, your server says to MANGOPAY to create a User and to automatically associate a wallet. The Buyer and its wallet are created
* The User buyer pays into its own wallet. Funds are escrowed there
* Once the buyer receives his item (depends on your app rules) the seller is payed. This means your server says to MANGOPAY to transfer the funds from the buyer’s wallet to the seller ’s wallet.
* Your application takes its fees on this operation.
* Now the seller can cash-out the collected funds to her/his bank account.

Let's take an example
* A buyer wants to buy an item for €20
* He/she pays on the app
* €20 are hold into its wallet waiting for the item
* The item is received, the €20 are transferred to the seller’s wallet minus the Platform fees (let say 4€ in this case)
* The seller receives 16€ on the wallet.
* He/she can ask for a 16€ withdrawal

## Create buyers and sellers
MANGOPAY do not distinguish buyers and sellers. They all are users through the solution so your application has to make the difference between them.

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

[alert type="info"]You can add a tag to make comparisons with your data like : « Buyer – internalID: 12345678 »[/alert]

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

## Refund a PayIn
Find below the classic way to reimburse funds directly on the credit card. As the funds stand into the Buyer wallet before the validation of the application, a refund is a simple request. You also can let the funds into the buyer’s wallet and offer her/him to choose another item/product/service.

![alt](http://demo.dev-app.net/uploads/medias/Capture-d’écran-2014-12-01-à-11.14.36.png)

## Validation - Transfer
Once the app knows that the item has been received, or the service has been done, your server tells MANGOPAY to transfer the funds from the buyer’s wallet to the seller’s one.
[entity_link entity="224"]Here is the Transfer API[/entity_link]. Now the funds belong to the Seller.

Following the €50 example, here is an example of the transfer:
```
{
AuthorId : "12345678",
CreditedUserId : "87654321",
DebitedFunds: {Currency : "EUR", Amount : 5000},
Fees : {Currency : "EUR", Amount : 500},
DebitedWalletID : "0987654",
CreditedWalletID : "4367890",
Tag : "DefaultTag"
}
```

[alert type="info"]
* The CreditedWalletID is the Seller’s wallet
* The DebitedWalletID is the Buyer’s wallet
* The CreditedUserID has to be the the Seller
* The AuthorID has to be the ID of the Buyer
* The fees are yours
[/alert]

## Collect your fees
[As you know](http://demo.dev-app.net/guide/collecting-platform-fees) MANGOPAY calculates its fee on the cash-in payments and a fix fee on cash-out (only for none SEPA-EUR withdrawals). The user is never directly charged by MANGOPAY. You, as the platform, are charged by MANGOPAY at the end of the month.

You will take your fees on the transfer between the buyer’s wallet and the seller’s wallet. The API only understand cents amounts. Let’s take a example:

There are €50 into the Buyer’s wallet waiting for a €50 item to be received. Then the app orders to transfer the amount. Let’s say your platform takes 10% fee so your app calculates the amount before creating the request. Here it is 50*10/100 = €5.

So here is the Mangopay request:
```
{
AuthorId : "12345678",
CreditedUserId : "87654321",
DebitedFunds: {Currency : "EUR", Amount : 5000},
Fees : {Currency : "EUR", Amount : 500},
DebitedWalletID : "0987654",
CreditedWalletID : "4367890",
Tag : "DefaultTag"
}
```

The seller received 45€ and your platform just collected 5€ in the Fees-wallet created by MANGOPAY especially for your platform. You don’t have access to this Fees-wallet. At the end of the month, MANGOPAY transfers the €5 to your platform bank account minus the MANGOPAY fees.

## The Seller cash out
The seller just collected the 45€. He is now able to withdraw its funds. Here are the steps:
1. Register the bank details
2. Ask for a withdrawal
3. Wait during 2 days max
4. Receive funds on bank account

**Technically speaking here are the requests:**

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

[alert type="info"]You can even take a fee here just as you’re doing it on transfers between wallets.[/alert]

Wait during 2 days maximum. All the payout requests are treated several times every working days by a dedicated MANGOPAY team. Once it is done, the status changes:
* CREATED : the request is created but not treated yet
* SUCCEEDED : the request has been successfully processed
* FAILED : the request has failed.

Then, there is an interbank delay. It can take up to two days for the seller to get his/her funds.
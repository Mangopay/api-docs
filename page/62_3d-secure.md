# 3D Secure

3D-Secure is a security protocol designed to be an additional authentification layer for online credit and debit card transactions. It is mainly used in Europe and the US. It was first created by Visa and was quickly followed by MasterCard, JCB, American Express, Maestro and UnionPay. Each card issuer branded the name of the scheme: 

* Visa:  *Verified by VISA*
* MasterCard: *MasterCard Secure Code*
* American Express:  *SafeKey 3D Secure*

# How it works for the payer?

1. User check-out on merchant site
2. User enters his cards details on merchant site
3. User is re-directed to his bank url 
4. User enters password on the bank url: can be a pre-defined password or a one time password sent by text message or on a smart card reader. 

![alt](/uploads/medias/3DS.png)

# Benefits
**For the end user: No payment with stolen card**

3DS have been proven to reduce significantly the number of fraudulent payment on the web. A 3DS authentification requires the buyer to have both the card information and a second authentification token (password, card reader…) 

**For the merchant: No risk of chargebacks**

It highly reduces the number of disputed payment due to “unauthorized transacton”. As we explained on other documents, on e-commerce the transactions are Card Non Present (CNP). In other words, the card and the standard security measures are not physically present in the transaction. Therefore the risk for fraudulent transactions is much greater. Given this, the liability of the transactions rests on the merchant. In other words, the payer can open a dispute to contest the funds. 
When doing a transaction with 3DS, the liability of the transaction is shifted back to the buyer’s bank. 


# How it works for you

**Setting-up 3DS**

* By default Mangopay trigger the 3DS security protocole for any transaction above 50euros
* By request, you can ask to trigger the 3DS for a smaller transaction
* On any transaction you can force the 3DS by passing the value FORCE in the `SecureMode` parameter on your pay-in. 


**In the payment flow**

1. [Create a Card Direct PayIn ](https://docs.mangopay.com/endpoints/v2.01/payins#e278_create-a-card-direct-payin),[Create a Card WEB PayIn ](https://docs.mangopay.com/endpoints/v2.01/payins#e269_create-a-card-web-payin) or a [Create a PreAuthorization](https://docs.mangopay.com/endpoints/v2.01/preauthorizations#e184_create-a-preauthorization)
2. Get Mangopay API response
3. If the `SecureModeRedirectURL` is provided in the response, you will need to redirect the user to it
4. User fills the 3DS form
5. User is redirected to `SecureModeReturnURL`
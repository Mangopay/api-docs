# PSD2 and SCA

New authentication requirements have been introduced on 14 September 2019 as part of the second Payment Services Directive (PSD2). In order to smoothen the implementation, transition plans have been negotiated with the industry. The changes will therefore take place gradually until 2021. 

![alt](https://docs.mangopay.com/uploads/medias/Screenshot-2019-08-28-at-10.28.33.png)

## Strong Customer Authentication (SCA)  
![alt](https://docs.mangopay.com/uploads/medias/Screenshot-2019-08-28-at-10.35.36.png)

The second Payment Services Directive (PSD2) introduces new requirements for authenticating payments and concerns all actors involved in the payment, from the cardholder to the payment provider and the online platforms. The authentication procedure with the new requirements is known as Strong Customer Authentication (SCA). The SCA will have an important impact on our clients and their users.

End-users will now be asked to authenticate more securely by providing two out of three of the authentication factors below: 
* Something the customer knows (e.g. pin / password) 
* Something the customer has (e.g. an SMS One-time Password) 
* Something the customer is (e.g. fingerprint / facial recognition) 

The payment industry is currently in the process of adapting its systems to include these authentication factors, most notably thanks to  [3DS 2.0](https://docs.mangopay.com/guide/3ds-20). Note that the method of authentication is entirely managed by the issuing bank (cardholder bank). 

![alt](https://docs.mangopay.com/uploads/medias/Screenshot-2019-08-28-at-10.28.33.png)

##  The scope of the new measures 
![alt](https://docs.mangopay.com/uploads/medias/Screenshot-2019-08-28-at-10.35.36.png)

The new requirements target: 
* All customer initiated transactions within Europe: Payments with both issuing and acquiring banks in the EEA.  As a you are using MANGOPAY for acquisition, your acquiring bank will always be in the EEA. If the issuing bank is outside the EEA, it is considered as a "one leg" payment which is out of scope of the regulation
* All online transaction: transaction happening when payer is offline like direct debit or merchant initiated transactions are not subject to strong customer authentication. MANGOPAY is building a new feature for card payments happening when the user is offline. 

![alt](https://docs.mangopay.com/uploads/medias/Screenshot-2020-02-20-at-16.15.22.png)
![alt](https://docs.mangopay.com/uploads/medias/Screenshot-2019-08-28-at-10.35.36.png)
## Exemptions
![alt](https://docs.mangopay.com/uploads/medias/Screenshot-2019-08-28-at-10.35.36.png)

The Regulatory Technical Standards have identified low-risk payments which may be exempted from the Strong Customer Authentication rules. The exemptions are not granted automatically and must be requested by the acquirer to the issuer. 

*  Low amount transactions 
		* Applied if the transaction is under €30. However, this can only be applied on:  
											* 5 transactions in a row since the last successful authentication without a time limit
											* A maximum of €100 cumulated in a row since the last successful authentication without a time limit
		* If a transaction does not meet all the requirements above, an SCA will be requested on the transaction. 
		

* Trusted beneficiaries
			* A merchant declared as a trusted beneficiary by the payer to their issuing bank or payment service provider (e.g. via the banking interface; 3DS page) 
									* MANGOPAY will not be able to request this exemption since only the bank of the payer has the information. 


* Low risk transactions
		* A transaction considered low-risk after a Transaction Risk Analysis has been conducted by the payment provider. We provide more details on this exemption below.


		
* Anonymous transactions
		* A prepaid or corporate card payment where there is no visibility for the issuing bank on the cardholder’s identity. 


		
![alt](https://docs.mangopay.com/uploads/medias/Screenshot-2019-08-28-at-10.28.33.png)

## Basic principles of exemptions
![alt](https://docs.mangopay.com/uploads/medias/Screenshot-2019-08-28-at-10.35.36.png)

The exemptions are based on 5 basic principles. 

1. Not automatic: The exemption needs to be requested and justified with sufficient information. 
2. Not compulsory: Banks are not required to support exemptions. We expect banks to adapt to the exemptions over time.
3. One exemption maximum: MANGOPAY will need to ask for a specific exemption. We cannot request multiple exemptions for one payment. MANGOPAY will choose the appropriate exemption while you will only request to be exempted. 
4. Final decision on the issuer’s side: The issuer decides to apply or refuse the exemption.
5. The requester is liable. If you request to be exempted, you will be liable. In the case the issuing bank use an exemption, or force the SCA: they will be liable.



In order to adapt to the new regulation, the card industry has decided to release a new version of the 3DS:  [3DS 2.0](https://docs.mangopay.com/guide/3ds-20). 

![alt](https://docs.mangopay.com/uploads/medias/Screenshot-2019-08-28-at-10.28.33.png)


[alert type="info"]Please find below further explanation on the Low -risk transactions exemption, the most important for MANGOPAY[/alert]

### Focus on low-risk transactions

Low-risk transactions will be MANGOPAY’s main exemption to allow your users to have a seamless experience. The exemption is obtained thanks to a **Transaction Risk Analysis (TRA**). The analysis is conducted by the payment provider. The eligibility will mainly be based on the payment provider’s fraud rate (MANGOPAY). 


The following table shows which fraud rates from the PSP are associated with which exemption amounts:
* 0.13% : <€100
* 0.06% : €100-€250
* 0.01% : €250-€500

**MANGOPAY is currently eligible to exemptions for payments up to €250. **

The current version of the TRA mainly takes the provider’s fraud rate into account. The TRA will slowly take into account additional parameters such as: delivery address, ip address, basket details. You will soon be able to send those parameters via the PayIn and Pre-Auth endpoints. Moreover, the issuing banks will start scoring the merchant. 

This is why we recommend you to: 
* Keep a low fraud rate 
* Provide a maximum amount of payment information
		* MANGOPAY will setup new dedicated parameters to provide sufficient payment information to our API
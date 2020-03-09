# Integrating MANGOPAY for a Marketplace
**I am developing a Marketplace. How to implement MANGOPAY?**

This document specifies the workflow and basic functionalities used by marketplaces to process payments with MANGOPAY’s API. For specific needs, please [contact](https://support.mangopay.com/s/contactsupport) our team.

# Glossary

| |  |
| -------- | -------- |
| **MARKETPLACE** |	Online platform where products and services are exchanged by third parties. Transactions are processed by the platform. (You)	|
| **USER** | Natural person (natural user) or a legal person (legal user).	|
| **SELLER** | User selling a product or a service. |
| **BUYER** |	User buying a product or a service. |
| **E-WALLET** |	Digital wallet on which electronic money is stored. |
| **PAYIN** |	Deposit of funds by a user on an e-wallet. |
| **TRANSFER** |	Movement of funds from one e-wallet to another. |
| **PAYOUT** |	Withdrawal of funds from an e-wallet to a end-user’s bank account. |
| **FEE** |	Commission calculated and collected by the marketplace. |
| **FEE E-WALLET** |	E-wallet owned by the marketplace to collect fees. |
| **REFUND** |	Reimbursement to a user. |
| **KYC** *(Know your customer)* |	Verification process of your users’ identity, part of European anti-money laundering regulation. |
| **CLIENT ID** |	ID of the platform operator in MANGOPAY’s environment. |
| **USER ID** |	ID of the end-user in MANGOPAY’s environment. |
| **DASHBOARD** |	Personalised interface providing the platform with full access to their activity in MANGOPAY’s API. |



# Introduction

MANGOPAY is a payment solution which enables marketplaces to easily process third-party payments. The typical workflow is described below.

**Typical marketplace workflow**

![alt](https://docs.mangopay.com/uploads/medias/MarketplaceWorkflow-2.png)


# MANGOPAY Set-up

Your first step is to [register your platform](https://mangopay.com/sign-up/) and create a [sandbox](https://www.mangopay.com/start/sandbox/) account.

![alt](https://docs.mangopay.com/uploads/medias/SetupMgp-1.png)

Once these steps have been completed, you will have access to MANGOPAY’s API and dashboard.

### AUTHENTICATION

Authentication is available with [Basic Access Authentication](https://docs.mangopay.com/guide/authentification). In production, we recommend using OAuth 2.0. You can find more details [here](https://docs.mangopay.com/guide/authentification).

1.  Combine the ***ClientId*** and ***API KEY*** into a string separated by a colon (e.g. "ClientId:API KEY").
2.  Encode the resulting string using [Base64.](https://en.wikipedia.org/wiki/Base64)
3.  Complete the ***Authorization header*** by adding "Basic" to the encoded string.
    

Here is an example:


| `ClientId` | `API KEY` | String to encode in Base64 | Base64 encoded string | Authorization Header |
| -------- | -------- | -------- | -------- | -------- |
| Aladdin     | ghsiu6hjqQjj      | Aladdin:ghsiu6hjqQjj     | QWxhZGRpbjpnaHNpdTZoanFRamo=      | Basic QWxhZGRpbjpnaHNpdTZoanFRamo=     |


# Integration

## Register sellers

### 1. Create a seller

[alert type="info"]Sellers and buyers are indistinctly registered as [users](https://docs.mangopay.com/endpoints/v2.01/users#e253_the-user-object) within the MANGOPAY API. [/alert]

Users can be:
-   Natural: a natural person
-   Legal: a business, organisation, sole trader
  
Create sellers with the following API call. In this example, the seller is a natural user. Please refer to our documentation to create a [legal user.](https://docs.mangopay.com/endpoints/v2.01/users#e259_create-a-legal-user)


    Create "Natural" user
	
    POST | https://api.sandbox.mangopay.com/v2.01/{{CLIENT_ID}}/users/natural
    {  
    	“FirstName“: “Cyrano“
    	“LastName“: “de Bergerac“, 
    	“Address“: {
    		“AddressLine1“:“Street 7“,
    		“AddressLine2“: ““,
    		“City“: “Paris“,
    		“Region“:“Ile de France“,
    		 “PostalCode“:“75009“,
    		“Country“:“FR“ 
    	},
    	“Birthday“: -258443002,
    	“Nationality“: “FR“,
    	“CountryOfResidence“: “FR“,
    	“Email“: “cyrano@bergerac.com“,
    	“Capacity“: “NORMAL“,
    	“Tag“: “Postman create a user“
    }


Store the received [user information](https://docs.mangopay.com/endpoints/v2.01/users#e255_create-a-natural-user), particularly the ***user-id***, as it is required for all user actions.

### 2. Create a seller's e-wallet

Use the  ***user-id*** to [setup an e-wallet](https://docs.mangopay.com/endpoints/v2.01/wallets#e20_the-wallet-object) which enables the user to store e-money. The e-wallet is owned by the respective user.


    Create Wallet
	
    POST | https://api.sandbox.mangopay.com/v2.01/{{CLIENT_ID}}/wallets
    {  
    	“Owners“: [“{{USER-ID}}“], 
    	“Description“: “A very cool wallet“,
    	“Currency“: “EUR“,
    	“Tag“: “Postman create a wallet“
    }

### 3. Register a seller's bank account


Register the seller’s [bank account](https://docs.mangopay.com/endpoints/v2.01/bank-accounts#e24_the-bankaccount-object) to payout the funds from his e-wallet(s).

    Create BankAccount (IBAN)
	
    POST | https://api.sandbox.mangopay.com/v2.01/{{CLIENT_ID}}/users/{{USER-ID}}/ bankaccounts/iban
    {  
    	“OwnerName“: “Cyrano de Bergerac“,
    	“OwnerAddress“: {
    			“AddressLine1“:“Street 7“,
    			“AddressLine2“: ““,
    			“City“: “Paris“,  
    			“Region“:“Ile de Frog“,
    			“PostalCode“:“75010“,
    			“Country“:“FR“
    	},  
    	“IBAN“: “FR7630004000031234567890143“,
    	“BIC“: “CRLYFRPP“,  
    	“Tag“: “Postman create a bank account“
    }

[alert type="info"]You will need to input an existing and valid BIC/IBAN in the sandbox.[/alert]


### 4. Create and submit KYC documents


European regulation requires you to create and submit seller KYC documents.

Find more general information [here](https://www.mangopay.com/fr/kyc/). Find more technical information [here](https://docs.mangopay.com/endpoints/v2.01/kyc-documents#e204_the-kyc-document-object).

  
| Natural user :  | Legal user : |
|--|--|
| IDENTITY PROOF | GENERAL MANAGER ID CARD |
|  | ARTICLES OF ASSOCIATION |
|  | SHAREHOLDER DECARATION |
|  | REGISTRATION PROOF |

[alert type="info"] KYC documents uploaded to the sandbox will need to be validated on the dashboard. [/alert]

The process to send a KYC document is divided into 3 parts.

-   **Step 1 :** Creation of a KYC Document
-   **Step 2:** Creation of KYC Pages within the document
-   **Step 3:** Submission of the KYC Document

The documents will be validated by our compliance team.

**Step 1:** Create a KYC document with the following API call.

    Create a KYC Document
	
    POST | https://api.sandbox.mangopay.com/v2.01/{{CLIENT_ID}}/users/{{USER-ID}}/kyc/documents/
    {  
    	“Tag“: “custom meta“, 
    	“Type“: “IDENTITY_PROOF“ 
    }


Store MANGOPAY’s [response](https://docs.mangopay.com/endpoints/v2.01/kyc-documents#e205_create-a-kyc-document) on your side, particularly the ***KYCDocumentId***.
  
**Step 2:** [Create a KYC page](https://docs.mangopay.com/endpoints/v2.01/kyc-documents#e208_create-a-kyc-page) using the ***KYCDocumentId*** and the ***USER-ID***. Repeat this step as many times as there are pages.

    Create a KYC Page
	
    POST | https://api.sandbox.mangopay.com/v2.01/{{CLIENT_ID}}/users/{{USER-ID}}/kyc/documents/{{KYCDocumentId}}/pages/
    { 
     	“File“:“/9j/4AAQSwAARCAFAAYUDASIA ... (truncate example)“
    }


[alert type="info"] The file should be encoded in base64 and grouped into one document. [/alert]

**Step 3:** Submit the KYC document for validation with the following API call.

    Submit a KYC Document
	
    PUT | https://api.sandbox.mangopay.com/v2.01/{{CLIENT_ID}}/users/{{USER-ID}}/kyc/documents/{{KYCDocumentId}}
    {  
    	“Tag“: “custom meta“,
    	“Status“: “VALIDATION_ASKED“
    }

After submission, the object will be waiting to be “VALIDATED”.

If you wish to be notified in case of a change of status, you can setup [hook notifications](https://docs.mangopay.com/endpoints/v2.01/hooks#e246_the-hook-object).

# Register Buyers

### 1. Create a buyer

Create a buyer by repeating the seller creation process.

Once again, buyers and sellers can be a natural person (natural user) or a legal entity (legal user).

### 2. Create a buyer's e-wallet

Create a buyer’s e-wallet by repeating the seller’s e-wallet creation process.

# Payment execution (pay-in)

Sellers and buyers have now been registered within our API. The next step is to send funds to a user’s e-wallet.

### 1. Pay-In by registered card


We recommend using our [direct pay-in](https://docs.mangopay.com/endpoints/v2.01/payins#e285_the-card-direct-payin-object) endpoint for a seamless integration and one-click payments. This is a two-step process:

 - **Step 1 :** Register the card 
 - **Step 2 :** Process payments
  
**Step 1 :** Create a [card registration object](https://docs.mangopay.com/endpoints/v2.01/cards#e177_the-card-registration-object) to store reusable and non-sensitive card details (tokens) within MANGOPAY's environment. This object is linked to the user with the ***USER-ID***.

    Create card registration
	
    POST | https://api.sandbox.mangopay.com/v2.01/{{CLIENT_ID}}/CardRegistrationsiban
    {  
    	“UserId“: “{{USER-ID}}“, 
    	“Currency“: “EUR“,  
    	“CardType»: “CB_VISA_MASTERCARD“
    }

MANGOPAY’s response will include:

 1. **PreregistrationData**
 2. **AccessKey**
 3. **CardRegistrationURL** 

Use these 3 parameters in the next step to post the card info.

![alt](https://docs.mangopay.com/uploads/medias/PostCardInfo-1.png)

Once a token is created, complete the card registration (***CardRegID***) by sending the ***RegistrationData*** to MANGOPAY.

    Update card registration 
	
    PUT | https://api.sandbox.mangopay.com/v2.01/{{CLIENT_ID}}/cardregistrations/{{CardReg_Id}}
    {
    	“RegistrationData“ : “{{CardReg_RegistrationData}}“
    }

The registered card may be used multiple times (one-click payment).

**Step 2:** Process [payments with the registered card](https://docs.mangopay.com/endpoints/v2.01/payins#e289_the-direct-debit-direct-payin-object) via the [direct pay-in](https://docs.mangopay.com/endpoints/v2.01/payins#e285_the-card-direct-payin-object). The API call contains the ***cardID***, ***currency***, ***amount*** (in cents), and any additional information you may want to send.


    Create a Payin Card/Direct
	
    POST | https://api.sandbox.mangopay.com/v2.01/{{CLIENT_ID}}/payins/card/direct
    { 
    	“AuthorId“: “{{USER-ID}}“,
    	“DebitedFunds“: {
    			“Currency“: “EUR“,
    			“Amount“: 100
    			}, 
    	“Fees“: {  
    			“Currency“: “EUR“,
    			“Amount“: 0
    			}, 
    	“CreditedWalletId“: “{{WALLET-ID}}“,  
    	“SecureModeReturnURL“: “http://test.com/“,
    	“SecureMode“ :“DEFAULT“,  
    	“CardID“: “{{CARD-ID}}“,  
    	“Tag“: “Postman create a payin card direct“,
    	“StatementDescriptor“: “Payin“
    }


# Funds Management

As a marketplace, you may manage funds between buyers and sellers.

### 1. Refund

MANGOPAY gives the possibility to refund payments, either partially or totally.

Create a [refund](https://docs.mangopay.com/endpoints/v2.01/refunds#e316_the-refund-object) using the ***PAYIN-ID***.

    Create PayIn Refund
	
    POST |  https://api.sandbox.mangopay.com/v2.01/{{CLIENT_ID}}/payins/{{PAYIN-ID}}/refunds
    { 
    	“AuthorId“: “{{USER-ID}}“,
    	“DebitedFunds“: {
    		“Currency“: “EUR“, 
    		“Amount“: 100
    	}, 
    	“Fees“: {  
    		“Currency“: “EUR“,
    		“Amount“: 0
    	}
    }

### 2. Transfer funds between buyers' and sellers'

A transfer request allows you to move funds from one e-wallet to another. In the marketplace flow, funds will be transferred from the buyer’s e-wallet to the seller’s.

Create a transfer using the ***DebitedWalletID*** and ***CreditedWalletID***.

    Create Transfer
	
    POST |  https://api.sandbox.mangopay.com/v2.01/{{CLIENT_ID}}/transfers
    { 
    	“AuthorId“: “{{USER-ID}}“,
    	“DebitedFund“: {
    		“Currency“: “EUR“, 
    		“Amount“: 10000
    	}, 
    	“Fees“: { 
    		“Currency“: “EUR“,
    		“Amount“: 1000
    	},
    	“DebitedWalletId“: “{{WALLET-ID}}“,
    	“CreditedWalletId“: “{{WALLET-ID}}“, 
    	“Tag“: “Postman create a transfer“
    }


>The marketplace can collect Fees on any transaction (pay-in, transfer, pay-out, refund). Platforms fees are automatically placed on your “Fee e-wallet”.
>Fees are calculated and owned by the marketplace. Find out more [here](https://docs.mangopay.com/guide/collecting-platform-fees).


### 3. Pay-out to the seller's bank account 


The last step of the marketplace transaction flow is the [payout](https://docs.mangopay.com/endpoints/v2.01/payouts#e227_the-payout-object).

Create a payout from the seller’s ***DebitedWalletID*** to the seller’s bank account.


    Create Payout BankWire
	
    POST | https://api.sandbox.mangopay.com/v2.01/{{CLIENT_ID}}/payouts/bankwire
    { 
    	“AuthorId»: “{{USER-ID}}“, 
    	“DebitedFunds“: {
    		“Currency“: “EUR“, 
    		“Amount“: 9000
    	}, 
    	“Fees“: {
    		“Currency“: “EUR“,
    		“Amount“: 0
    	}, 
    	“DebitedWalletId“: “{{WALLET-ID}}“,
    	“BankAccountId“: “{{BANKACCOUNT-ID}}“,
    	“BankWireRef“: “Postman“ 
    }


# Testing MANGOPAY API with Postman
>Test the MANGOPAY API  calls in seconds. 

### What is Postman?

[Postman](https://www.getpostman.com/) is an app for easy RESTful API exploration. It allows you to test API calls without writing the code or installing the SDKs.

### Step 1: Get the Postman collection


1.  If you have not already, visit [https://www.getpostman.com/](https://www.getpostman.com/) and install the preferred version for your system.
2. Click the Run in Postman button below to open Postman and import MANGOPAY’s API Postman collection.

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/c8f5f08b69a16a340ce7)


### Step 2: Create your Postman environment

Our collection makes use of Postman's environment variables to easily manage your API credentials. Start by creating a sandbox environment.

1. Open the "Environment options" panel by clicking on the gear icon, then click **Manage Environments.** To create a new environment, click **Add**.
2. Name your environment something that indicates it is using sandbox credentials, for example "MANGOPAY Sandbox".
3. Add a variable/value pair with "***CLIENT_ID***" as the variable and your client ID as the value.
4. Add a variable/value pair with "***API_KEY***" as the variable and your api key as the value.
5. Add a variable/value pair with "***SERVEUR_URL***" as the variable and "https://api.sandbox.mangopay.com" as the value.
6. Add a variable/value pair with "***VERSION***" as the variable and "V2.01" as the value.
5. When you are finished adding variable/value pairs, click Add. Now, any test calls you make using this environment will automatically fill in the `CLIENT_ID` , `SERVEUR_URL`,  `VERSION`, `api_key` with your sandbox credentials.


### Step 3: Send a call to create your first user

Send a call to create your first user using your sandbox environment.

1. Click the dropdown menu next to the gear icon and choose your sandbox environment from the menu.
2. Open the  collection then click on create “natural” user under the **Register sellers/buyers folder**
3. Click “Send”. Postman will use your Basic Auth credentials to make the call.



The MANGOPAY API collection also includes folders for all MANGOPAY v2.01 API endpoints with pre-configured calls. Please find it [here](https://app.getpostman.com/run-collection/82ebbb72db2de02b6ed0)
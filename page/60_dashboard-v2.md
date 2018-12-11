# MANGOPAY Dashboard 

The MANGOPAY Dashboard is a visual interface which provides full access to all your activity and operations (get lists, do refunds, do payouts, etc.)! The info below presumes that you have basic knowledge of the Mangopay solution. The access to the MANGOPAY Dashboard is monitored by the  [SSO object](https://docs.mangopay.com/endpoints/v2.01/sso#e872_the-sso-object), you can create multiple access for multiple users with different permissions. This operation can be done throught the API or on the Account page of the dashboard.  

Please, be careful with your access credentials. In case you think someone has access who shouldn’t, please ask support@mangopay.com to regenerate your login info.

## How to access your MANGOPAY Dashboard
**STEP 1. Ask for your access**
* Go on [this link for a PRODUCTION ACCOUNT](https://api.mangopay.com/register) or on [this link for SANDBOX ACCOUNT (test environment)](https://api.sandbox.mangopay.com/register)
* Clic on "Create an access" button.
* Enter your application’s ClientId and the email (you should already have created an account)

You will then receive an email with a dedicated access

**STEP 2. Create your access**
* Click the link in the email within **30 min**!
* Create a password (with one uppercase letter, one lowercase letter, a number and a symbol)

**STEP 3. Sign in**
* To the [production dashboard](https://dashboard.mangopay.com)
* To the [V1 dashboard (old dashboard)](https://dashboard-v1.mangopay.com/)
* To the [sandbox production account](http://dashboard.sandbox.mangopay.com)
* If you’ve lost or forgotten your password. You can use the “forgotten password” button.

## How your MANGOPAY Dashboard works
[alert type="info"]Note that we changed some namings on the new version of the dashboard to give you a better experience.  [/alert]

Here is the list:
* Wallet credit becomes repudiation wallet
* Refunded payout →  Payout return
* Refunded paying →  Paying refund
* Refunded transfer →  Transfer refund
* Settlement →  Repudiation settlement
* Natural → Individual
* Legal →  Professional
 


**DASHBOARD Homepage**

![alt](/uploads/medias/homeversion2.png)

In the Dashboard homepage you will be able to see on the left side a the amount of fees your account balance nd on the right side the main blocking issue your users might be encountering: commpliance issues, payout issues and payment disputes.

On the top right corner, if you press the user icon, you will be able to access and edit  your Profile (Single Sign-on) and your Account details. 

At the top of all pages, you are able to search for objects IDs (users, transactions, cards, wallets).


**USER MENU**

![alt](/uploads/medias/Userslist.png)

In the User menu you can access to the list of all the users on your platform.
If you click on one user you will be able to access:

* The user’s profile, probably the most important page of the dashboard.  You are able to see in one glance: User details (of course) but also his cards, wallets, number of disputes, KYC, emoney, recent transactions, bank accounts. That’s not the end, you can also do a payin, a payout, a transfer, or upload a kyc documents.

![alt](/uploads/medias/Userdetails.png)

To have more information about a particular object click on the corresponding tabs, press "view all" or click on the action button (three dots) and then "view details". On the "Recent transactions" widget, click on the transaction.

![alt](/uploads/medias/Useraction.png)

On the action button (the three dotes), you can also do operations: Pay-in, Pay-out, transfers. A pop-in will appear and guide you throught the operation you want to create.  

![alt](/uploads/medias/POPINtransac.png)

* Their transactions and their status (whether succeeded, failed etc):

![alt](/uploads/medias/Usertransactions.png)

* The wallets associated to this user:

![alt](/uploads/medias/Userwallet.png)

* The list of cards registered for this user:

![alt](/uploads/medias/Usercards.png)

* The list of  pre-authorizations for this user:

![alt](/uploads/medias/Userpreauth.png)

* The list of registered bank accounts for this user:

![alt](/uploads/medias/Userbankaccounts.png)

* The list of mandates fot this user:

![alt](/uploads/medias/Usermandates.png)

* The KYC submitted documents and their status (successful, awaiting validation etc):

![alt](/uploads/medias/UserKYC.png)

**TRANSACTIONS MENU**

This is a new feature of this new dashboard. You are able to see all the transactions and to filter them by date, type and status. To have more details about the transaction click on the corresponding row. If you click on the action button (...), you can download the proof for this transaction.

![alt](/uploads/medias/Transactionslist.png)

After clicking on a transaction, you will have the transaction details including author, credited user, credited wallet, card used and all refunds for this transaction. Depending on the transaction type you can also re-do, refund the transaction.

![alt](/uploads/medias/Transactiondetails.png)

**COMPLIANCE MENU**

On this page, you are able to check all the KYC documents of your users and add new ones. 

![alt](/uploads/medias/Compliance.png)

**PAYMENT DISPUTES MENU**

On this page, you are able to see all the [Disputes](https://docs.mangopay.com/endpoints/v2.01/disputes#e176_the-dispute-object) created by your users. You can filter them by date, type, status and Uer or wallet. We strongly advice you to check as fast as possible the disputes with status "pending client" action in order to contest the dispute before the deadline. As for the transaction list, you can click on a dispute row to have more details about it. 

![alt](/uploads/medias/Disputeliste.png)

By clicking, you will have access to the dispute details page where you will be able to track dispute process, respond to the dispute (contest/close) and settle the dispute funds in the case the dispute is lost.  Read the comments in the "pending action from you" widget in order to inform yourself about the next step.

![alt](/uploads/medias/Disputedetails.png)

**REPORTING MENU**

On this page, you are able to create reports of transactions or wallets. You can add a name/tag to your report. 

![alt](/uploads/medias/Reporting.png)

**DEVELOPERS MENU (MOSTLY USED BY DEVELOPERS)**

On this menu you have access to the list of events and the the hooks (clicking on the corresponding tab). As for the transaction list, you can click on an event to have more details on it.

The "Hooks" will allow you to see which Events your developers have registered notifications for, what’s the status of these hooks and to which URL on your side you will be able to receive these notifications. It is not advisable that you change any of these settings without discussing with your developers first!

![alt](/uploads/medias/Devpage.png)
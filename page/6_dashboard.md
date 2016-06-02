# MANGOPAY Dashboard

The MANGOPAY Dashboard is a visual interface which provides full access to all your activity and operations (get lists, do refunds, do payouts, etc.)! The info below presumes that you have basic knowledge of the Mangopay solution.

Please, be careful with your access credentials. In case you think someone has access who shouldn’t, please ask support@mangopay.com to regenerate your login info.

## How to access your MANGOPAY Dashboard
**STEP 1. Ask for your access**
* Go on [this link for a PRODUCTION ACCOUNT](https://api.mangopay.com/authorize?response_type=code&client_id=mangoapps&redirect_uri=https://dashboard.mangopay.com/Authorize/SignIn) or on [this link for SANDBOX ACCOUNT (test environment)](https://api.sandbox.mangopay.com/authorize?response_type=code&client_id=mangoapps&redirect_uri=https://dashboard.sandbox.mangopay.com/Authorize/SignIn)
* Clic on "Create an access" button.
* Enter your application’s ClientId and the email (you should already have created an account)

You will then receive an email with a dedicated access

**STEP 2. Create your access**
* Click the link in the email within **30 min**!
* Create a password (with one uppercase letter, one lowercase letter, a number and a symbol)

**STEP 3. Sign in**
* For a production account: dashboard.mangopay.com
* For a Sandbox account: dashboard.sandbox.mangopay.com
* If you’ve lost or forgotten your password. You can use the “forgotten password” button.

## How your MANGOPAY Dashboard works
**DASHBOARD MENU**

![alt](/uploads/medias/DBMenu.png)

In the Dashboard menu you will be able to see the “Latest updates and news” regarding the new or updated features of our API. You have also access to the same news via our [site](/blog/).

At the top of all pages, you are able to search for objects IDs (users, transactions, cards, wallets).


**USER MENU**

![alt](/uploads/medias/DBUserMenu.png)

In the User menu you can access to the list of all the users on your platform.
If you click on green magnifying glass icon you will be able to access:

* The user’s profile and update it:

![alt](/uploads/medias/DBUserMenu2.png)

* Their transactions and their status (whether succeeded, failed etc):

![alt](/uploads/medias/DBUserMenuTransaction.png)

* The wallets associated to this user:

![alt](/uploads/medias/DBUserMenuWallet.png)

* The list of cards registered for this user:

![alt](/uploads/medias/DBUserMenuCards.png)

* The list of registered bank accounts for this user:

![alt](/uploads/medias/DBUserMenuBAN.png)

* The KYC submitted documents and their status (successful, awaiting validation etc):

![alt](/uploads/medias/DBUserMenuKYC.png)

Going back to the User’s list of transactions, you can click on the magnifying glass icon for each one to see the full details of the transaction. Let’s take a successful payin as example.

![alt](/uploads/medias/DBUserMenuTransaction2.png)

We arrive to the details of the PayIn page:

![alt](/uploads/medias/DBUserMenuTransactionPayIn.png)

If you want to refund this payin you can click on the “Refund” button.
You are then redirected to the “Operations” menu, with the fields prefilled, since you accessed it through the “Users menu”:

![alt](/uploads/medias/DBUserMenuTransactionPayInRefund.png)

You can also of course go to Operations directly and do the actions that you require, by filling all the parameters in yourself:

![alt](/uploads/medias/DBUserMenuTransactionPayInRefund2.png)

*Tip operation : You can access the operations through the user’s menu, that will allow you to access the operation menu but with prefilled fields.*

**NOTIFICATION MENU (MOSTLY USED BY DEVELOPERS)**

![alt](/uploads/medias/DBNotificationMenu.png)

The "Notification menu" will allow you to see which Events your developers have registered notifications for, what’s the status of these hooks and to which URL on your side you will be able to receive these notifications. It is not advisable that you change any of these settings without discussing with your developers first!

**API STATUS MENU**

This page keeps you aware of any upcoming or active incidents or technical maintenance on the API.
You can register to this site by clicking the button “Subscribe to updates” on our [status page](http://status.mangopay.com/) and receive a text message or an email.
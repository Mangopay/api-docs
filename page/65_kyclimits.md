# KYC and limits

KYC stands for Know Your Customer and entails the whole verification process of your users. This process is part of European anti-money laundering regulation, known as AML, which requires institutions such as MANGOPAY to make sure that money transacting through their system is clean. It will therefore be an integral part of your collaboration with us.


The whole verification process is automated thanks to our dedicated API endpoint. This feature is available for users worldwide and provides you with a global, compliant and trustful service.   


There are two levels of user verification, also called API levels: Light (default) and Regular. 
* Light (default) verification  requires basic information provided during the user[ creation process](https://docs.mangopay.com/endpoints/v2.01/users#e253_the-user-object). 
* Regular verification requires identity proof which allows users to handle unlimited funds freely. 

[alert type="info"]A user will never be blocked when exceeding their allowed KYC limits during a pay-in - it is the transfers and payouts that will be blocked.  [/alert]


**Know your limits**

The limit of funds which a user can handle with a Light (default) verification depends on your country of incorporation and the MANGOPAY services which you are using: Payment Services or Electronic Money Services.

|COUNTRY|                        PAYMENT SERVICES                      |                        ELECTRONIC MONEY ISSUER                      |
| -------- | -------- | -------- |
 |FRANCE| <ul><li> Pay-in/Transfers: no limit </li><li> Payout: 0.01€ | <ul><li> Cumulated Payout per calendar month: 250€</li><li> Account balance: 250€ |
|GERMANY| <ul><li> Pay-in/Transfers: no limit </li><li>  Payout: 0.01€| <ul><li> Cumulated Payout per calendar month: 100€ </li><li> Account balance: 100€  |
|REST OF EUROPE|<ul><li>  Pay-in/Transfers: no limit </li><li>  Payout: 0.01€| <ul><li> Cumulated Payout per calendar month: 250€</li><li> Account balance: 250€ |



To find out which MANGOPAY service you are using, please refer to your [contract](https://mangopay.desk.com/customer/portal/articles/2957440).
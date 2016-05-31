# How to run and test payments

In the Sandbox environment, you can use the following test data to simulate a transaction:

## Visa/MC
**For payments under 100€ you can use these cards:**

* N°: 4706750000000009
* Expiry: Any date in the future
* CSC: 123

* N°: 4706750000000033
* Expiry: Any date in the future
* CSC: 123

* N°: 4706750000000025
* Expiry: Any date in the future
* CSC: 123

* N°: 4706750000000017
* Expiry: Any date in the future
* CSC: 123

**For payments with 3D Secure you can use these cards:**

3D Secure starts from 100€. Therefore, on Sandbox environment, all payments over 100€ has to be processed with one of the following cards:

* N°: 3569990000000132
* Expiry: Any date in the future
* CSC: 123
* N°: 3569990000000157
* Expiry: Any date in the future
* CSC: 123

**You can only use these cards with the password ″secret3″ (is different from the BCMC and Diners one!). If you put a wrong password the card will be blocked**

**In order to test the liability shift, you can use these cards:**

* N°: 4970100000000154
* Expiry: Any date in the future
* CSC: 123

* N°: 4970101122334422
* Expiry: Any date in the future
* CSC: 123

* N°: 4970101122334406
* Expiry: Any date in the future
* CSC: 123

* N°: 4970101122334414
* Expiry: Any date in the future
* CSC: 123

**Error Codes Triggers**
With the Visa/Mastercard credit cards, you can trigger specific error codes given on the [error codes page](/guide/errors).

## Maestro
All Maestro payments require 3DS
* N°: 3012340000000000
* Expiry: Any date in the future
* CSC: not required

* N°: 3012349999999999
* Expiry: Any date in the future
* CSC: not required

**You can only use these cards with the password ″MAES123″ (this is different to the Visa/Mastercard and BCMC one!). If you put a wrong password the card will be blocked**

## Diners
* N°: 30123456789001
* Expiry: Any date in the future
* CSC: 123

## Masterpass
Choose "Masterpass" from the list and then:
* Login : joe.test@email.com
* Password : abc123
* Pet name : fido

## ELV
* Account number: 0010739408
* Bank code: 86055592

## Giropay
Step 1
* BIC : TESTDETT421
* IBAN : DE46940594210000012345

Step 2
* Id: sepatest1
* BIN: any 5 digits

Step 3
* Any 6 digits

## Sofort
* Bank code: 88888888
* Country of buyer’s bank:  Allemagne (‘DE’)
* Buyer’s bank code: 123456
* Buyer’s bank password: 123456

## P24
You do not need a card to test this payment method – just click on any of the bank logos and the transaction will be successful

## BCMC
* N°: 67031330054610319
* Expiry: Any date in the future

**You must use the password ″BCMC123″ (this is different to the Visa/Mastercard and Diners one!). If you put a wrong password the card will be blocked**

## iDeal
You do not need a specific test account to use iDeal in sandbox – just choose "ING" from the two options on the RedirectURL and the transasction will then be accepted (in production, you would then be redirected to the approriate bank to make the payment)
Note that the following specific amounts are reserved for specific errors:
* 2.00EUR: the transaction has been cancelled by the user (101002)
* 3.00EUR: User has let the payment session expire without paying (001034)
* 5.00EUR: Transaction Refused (101199)
* 4.00EUR and 7.00EUR will also result in errors

## PayLib
* Login : payline6.test@atos.net
* Password : P@ylin3

Then choose any one of the banks and validate the transaction.
# How to run and test payments

In the Sandbox environment, you can use the following test data to simulate a transaction.  Note that you can trigger specific error codes using specific amounts - see the [error codes page](/guide/errors) for more info.
[alert type="info"]For all cards, the expiry date can be any month/year in the future and the CSV (the three numbers on the back of the card) can be any three numbers[/alert]


## Visa/MC
**For payments under 50€ you can use these cards:**
* 4706750000000009
* 4706750000000033
* 4706750000000025
* 4706750000000017

**For payments with 3D Secure you can use these cards:**
3D Secure starts from 50€. Therefore in the Sandbox environment, all payments over 50€ must be processed with one of the following cards - **please use the correct password shown below to avoid blocking the card**:
* 3569990000000165
* 3569990000000140

[alert type="danger"]You can only use these cards with the password ″secret3″ (is different from the BCMC and Diners one!). If you put a wrong password the card will be blocked[/alert]

**In order to test the liability shift, you can use these cards:**
* 4970100000000154
* 4970101122334422
* 4970101122334406
* 4970101122334414

## Maestro
All Maestro payments require 3DS
* 3012340000000000
* 3012349999999999

[alert type="danger"]You can only use these cards with the password ″MAES123″ (this is different to the Visa/Mastercard and BCMC one!). If you put a wrong password the card will be blocked[/alert]

## Diners
* 30123456789001

## Masterpass
Choose "Masterpass" from the list and then:
* Login : joe.test@email.com
* Password : abc123
* Pet name : fido

## Giropay
*Step 1*
* BIC : TESTDETT421
* IBAN : DE46940594210000012345

*Step 2*
* Id: sepatest1
* BIN: any 5 digits

*Step 3*
* Any 6 digits

## Sofort
* Bank code: 88888888
* Country of buyer’s bank:  Allemagne (‘DE’)
* Buyer’s bank code: 123456
* Buyer’s bank password: 123456

## P24
You do not need a card to test this payment method – just click on any of the bank logos and the transaction will be successful

## BCMC
* 67031330054610319

[alert type="danger"]You must use the password ″BCMC123″ (this is different to the Visa/Mastercard and Diners one!). If you put a wrong password the card will be blocked[/alert]

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

##Mandates
For testing mandates, you should use a specific value for the FirstName for the user owning the mandate
* "Invalid" will result in a failed mandate due to incorrect bank account information – note that this only works for mandates with the Scheme "BACS"
* "Successful" will result in an active mandate, however you must do a payment with this mandate for the status to be updated
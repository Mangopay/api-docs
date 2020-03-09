**3. Send card details (Payment form)**

You have to send the fields AccessKey, PreregistrationData and the user card details (card number, expiry date and CSC) to the tokenization server through a form posted on the CardRegistrationURL. We recommend using the following registration kits to remain compliant and avoid any risks associated to sensitive card data :

- PHP integration sample: https://github.com/MangoPay/mangopay2-php-sdk/tree/master/demos/paymentDirect 
- JS integration sample: https://github.com/MangoPay/mangopay2-php-sdk/tree/master/demos/paymentDirect/js

*N.B : Users’ card information is directly sent to our PCI-DSS compliant PSP without reaching our servers. That is why the POST URL in this endpoint differs from the other endpoints. The retrieved data from this POST cannot be used or exploited without an authenticated MANGOPAY API call. *

[alert type="info"] Please note that the expiry date posted to the CardRegistrationURL must be in this format: MMYY  / Please note that parameters in this POST should be send in "x-www-form-urlencoded" instead of the classic JSON format. [/alert]

[alert type="info"] You can get the CardRegistrationURL from the "Create a card registration" json response. [/alert]

> **POST** : `https://homologation-webpayment.payline.com/webpayment/getToken`
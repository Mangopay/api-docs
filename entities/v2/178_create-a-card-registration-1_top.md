**Steps**
**1. Send the request (An input JSON example)**
**2. Get the reply (An output JSON example)**
**3. Send card details (Payment form)**
Now you have to send to the tokenization server the fields « AccesKey », « PreregistrationData » and the user card details (card number, expiry date and CSC) through a form posted at the « CardRegistrationURL ».
Here are 2 PHP samples to post card details:

PHP integration sample: https://github.com/MangoPay/mangopay2-php-sdk/tree/master/demos/paymentDirect
JS integration sample: https://github.com/MangoPay/mangopay2-php-sdk/tree/master/demos/paymentDirect/js

[alert type="info"]
Please note that the expiry date posted to the cardregistrationURL must be in this format: MMYY
[/alert]

**4. Get the RegistrationData key (After registration)**
 After posting card details, you get a « RegistrationData ». Here is an example :
 ``
« data=gcpSOxwNHZutpFWmFCAYQu1kk25qPfJFdPaHT9kM3gKumDF3GeqSw8f-k8nh-s5OC3GNnhGoFONuAyg1RZQW6rVXooQ_ysKsz09HxQFEJfb-6H4zbY2Nnp1TliwkEFi4 » (You also have to put « data= » into the field)
``

**5. Finally**, you have to edit the « CardRegistration » Object (PUT method) with this « RegistrationData » just received.

Now please, go to Update Card Registration.

TIP : You can download our graphic [KIT](http://docs.mangopay.com/files/2013/09/KIT.zip)
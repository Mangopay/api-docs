# Address Verification System 




Address Verification System is an anti-fraud tool used in the UK, US and Canada for online payment by Visa, Mastercard and Amex. 

The system compares the billing address entered by the user for the purchase and the address of the credit card registered at his bank.  Depending on multiple checks between these two addresses, a "score" is provided by the acquiring bank. We are now providing you this AVS result as an indicator. In other words, we won’t act over a bad scoring.  You are therefore responsible for implementing rules on the scoring. 

Result system:

|MANGOPAY value|Comments|
| -------- | -------- |
|FULL_MATCH|Billing address provided and address registered on bank side are strictly the same|
|ADDRESS_MATCH_ONLY|Only street name matches. Postal code does not match|
|POSTAL_CODE_MATCH_ONLY|Only postal code matches. Street name does not match|
|NO_MATCH|Billing address provided and address registered on bank side are totally different|
|NO_CHECK|No check has been done due to: a lack of data (no billing address has been provided) / a non-compatible card / an unavailability of AVS service on bank side. This status is also used for 3DS payments until the payment has been validated on the customer side (AVS check given when status = SUCCEEDED)



-----


***How to implement it with Mangopay?***

1. Send billing Information
 
 In order to offer this solution to you,  we have added the optional property `BillingAddress` on the API endpoints Create a Card Direct Payin and Create a PreAuthorization. This new property is composed of the same fields as all our `Address` structure in our API. If you want us to return the AVS scoring you must send us the `BillingAddress` completed with required field.

2. Get the AVS result:
 
If you have sent the billing information, you will get the `AVSResult` in the response to calls on the following endpoints:
* [Create a Card Direct Payin ](https://docs.mangopay.com/endpoints/v2.01/payins#e278_create-a-card-direct-payin)
* [Create a PreAuthorization](https://docs.mangopay.com/endpoints/v2.01/preauthorizations#e184_create-a-preauthorization)

The `AVSResult` information will appear inside the property `SecurityInfo`.  `SecurityInfo` is a new property that we will use more and more to transmit key anti-fraud information.



-----


***Tips:***

As we said before, AVS score only gives a score on a transaction, but doesn’t block the payment. In order to make the most of this feature, we advise you to adapt your flow adding conditions dependant on the AVS result. The best way to do so is to start by a PreAuthorization, check the `AVSResult` and depending on the result capture the funds or review manually the PreAuth before processing (or not) the payment.


***Go Further:***

We recently partnered up with Riskified. Riskified is an anti-fraud solution which matches transaction data to instantly give approvals on transactions. To completely eliminate any risk for your business, Riskified covers any chargeback due to fraud on transaction approved by them.   
	
***Mangopay and Antifraud:***

For 2018, we have planned different anti-fraud features to help you reduce significantly chargebacks. We will keep you posted on this subject and provide you tools and tips to improve payment security on your platform throughout the year.
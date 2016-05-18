“**Pre-authorization**” ensures the solvency of a registered card for 7 days. Beyond this period, it is still possible to charge the card (PayIns/Card/Direct) but funds are not guaranteed.
The overall process is as follows:
1. Register a card (CardRegistration)
2.  Create a PreAuthorization with the CardId. This allows you to charge an amount on a card
3.  Charge the card through the PreAuthorized PayIn object (Payins/preauthorized/direct)

How does PreAuthorization work?

* Once the « PreAuthorization » object is created the status is « CREATED » until 3D secure validation.
* If the authorization is successful the status is « SUCCEEDED » if it failed the status is « FAILED ».
* Once « Status » = « SUCCEEDED » and « PaymentStatus » = « WAITING » you can charge the card.
* The Pay-In amount has to be less than or equal to the amount authorized.


**Object Resources**

| Property | Type | Description |
| -------- | -------- | -------- |
| Tag     | string      | Custom data     |
| AuthorId     | string      | The user Id of the author of the pre-authorization     |
| DebitedFunds     | string      | It represents the amount debited on the bank account of the Author.DebitedFunds = Fees + CreditedFunds (amount received on wallet)     |
| Status     | string      | Status of the PreAuthorization: »CREATED », « SUCCEEDED », or « FAILED »     |
| PaymentStatus     | string      | The status of the payment after the PreAuthorization »WAITING », « CANCELED », « EXPIRED » or « VALIDATED »     |
| ResultCode     | string      | The PreAuthorization result code     |
| ResultMessage     | string      | The PreAuthorization result Message explaining the result code     |
| ExecutionType     | string      | How the PreAuthorization has been executed. Only on value for now: « CARD »     |
| SecureMode     | string      | The SecureMode correspond to « 3D secure » for CB Visa and MasterCard or « Amex Safe Key » for American Express. This field lets you activate it manualy.     |
| CardId     | string      | The ID of the registered card (Got through [textCardRegistration](https://docs.mangopay.com/api-references/card-registration/) object)     |
| SecureModeNeeded     | string      | Boolean. The value is « true » if the SecureMode was used     |
| SecureModeRedirectUrl     | string      | This is the URL where to redirect users to proceed to 3D secure validation     |
| SecureModeReturnURL     | string      | This is the URL where users are automatically redirected after 3D secure validation (if activated)     |
| ExpirationDate     | Timestamp      | The date when the payment is processed     |
| PayInId     | string      | The Id of the associated PayIn.     |

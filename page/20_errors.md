# Error codes
With the Visa/Mastercard credit cards, you can trigger specific error codes by using the transaction amounts given in the column "Test amount"

## Operation failed

|Result Code|Result Message| More information | Test amount |
| -------- | -------- | -------- | -------- |
| 001999 |	Generic Operation error	| An incident or connection issue has occured and closed all transactions. | |
| 001001 |	Unsufficient wallet balance |	The e-wallet does not contain enough funds to process the transaction	 | |
| 001002 |	Author is not the wallet owner |	The user ID used as Author has to be the wallet owner | |	
| 001011 |	Transaction amount is higher than maximum permitted amount	 | | |	
| 001012 |	Transaction amount is lower than minimum permitted amount		 | | |
| 001013 |	Invalid transaction amount | The user's bank has rejected the transaction. Users should contact his/her bank for more information. |		333.13 |
| 001014 |	CreditedFunds must be more than 0 (DebitedFunds can not equal Fees)	 | | |

## PayIn Web errors
|Result Code|Result Message | More information |
| -------- | -------- | -------- |
| 001030 |	User has not been redirected	| The user never gets the payment page and never opens the Payline session |
| 001031 |	User canceled the payment |	The User clicks on "Cancelled" on the payment page	 |
| 101002 |	The transaction has been cancelled by the user |	The User clicks on "Cancelled" on the payment page |	
| 001032 |	User is filling in the payment card details	| The user is still on the payment page (Payline session) |	
| 001033 |	User has not been redirected then the payment session has expired | The session has expired so the Payin Web is failed. The user has gone on the payment page |
| 001034 |	User has let the payment session expire without paying | The user went to the payment page but let the session expired. So the Payin Web has failed |
| 101001 |	The user does not complete transaction |   The user did not enter some of the compulsory information. All fields should be completed within the first minutes of payment. |

## Refund transaction errors
|Result Code|Result Message | More information |
| -------- | -------- | -------- |
| 001401 | Transaction has already been successfully refunded | |
| 005403 | The refund cannot exceed initial transaction amount | Refunding more than the initial transaction's value is not possible. Make a separate transfer to add a compensation. |
| 005404 | The refunded fees cannot exceed initial fee amount | Refunding more than the initial transaction fee is not possible. Make a separate transfer to add a compensation. |
| 005405 | Balance of client fee e-wallet insufficient | Fees cannot be included in a refund if the fee e-wallet has already been debited and that the outstanding amount has been payed out. |
| 005407 | Duplicated operation: you cannot refund the same amount more than once for a transaction during the same day | Refunds processed twice for the same amount on a specific transaction are blocked to prevent unintentional double-refunds. |
| 001403 | The transaction cannot be refunded (max 11 months) | |

## Card input errors
|Result Code|Result Message| More information | Test amount |
| -------- | -------- | -------- | -------- |
| 105101 | Invalid card number | The card number given doesn’t match the real number of the card| 333.14 |
| 105102 | Invalid cardholder name | The card holder name given doesn’t match the real owner of the card |  |
| 105103 | Invalid PIN code | The Personal Identification Number code is invalid. The user should check card information and retry.  | 333.55 |
| 105104 | Invalid PIN format | The Personal Identification Number format is invalid. The user should check card information and retry |  |

## Transaction Refused
|Result Code|Result Message | More information | Test amount |
| -------- | -------- | -------- | -------- |
| 101101 | Transaction refused by the bank (Do not honor) | The error "Do not honor" is a message from the bank. You could get it for several raisons: Maximum amount spent per month has been reached on this card // Maximum amount spent on internet per month has been reached on this card // No more funds on bank account | 333.05 (or use the CVV code 999) |
| 101102 | Transaction refused by the bank (Amount limit) | You will get this error if the user reached a bank amount limit. It could be: Maximum pre authorized amount reached // Maximum amount spent per month has been reached on this card // Maximum amount spent on internet per month has been reached on this card | 333.51 |
| 101103 | Transaction refused by the terminal | The terminal refusal may be linked to the user's card. The user should try to use an alternative card/payment method.  | 333.58 |
| 101104 | Transaction refused by the bank (card limit reached) |  | 333.60 |
| 101105 | The card has expired |  |  |
| 101106 | The card is inactive | The card is not active accourding to the bank and can therefore not be used |  |
| 101108 | Transaction refused: the Debited Wallet and the Credited Wallet must be different | Funds cannot be transferred to the same e-wallet. Try to move the funds to a different e-wallet. |  |
| 101109 | The payment period has expired |  Bankwires payin expire after one month if the funds has not been received by MANGOPAY within this time |  |
| 101110 | The payment has been refused |  Due to a bank wire issue, the bank transfer has been declined or cancelled. Please try again. |  |
| 101410 | The card is not active | The card has been disabled on Mangopay and is no longer useable |  |
| 101111 | Maximum number of attempts reached | Too much attempts for the same transaction | 333.38 |
| 101112 | Maximum amount exceeded | This is a card limitation on spent amount |  |
| 101113 | Maximum Uses Exceeded | Maximum attempts with this cards reached. You must try again after 24 hours |  |
| 101115 | Debit limit exceeded | This is a card limitation on spent amount | 333.61 |
| 101116 | Amount limit | The number of authorised daily transactions has been exceeded. Please contact our support to adjust the number of daily transactions. |  |
| 101118 | An initial transaction with the same card is still pending | | |
| 002996 | Blocked due to User Balance limitations (maximum owned amount reached) | | |
| 101199 |Transaction refused | The transaction has been refused by the bank. Contact your bank in order to have more information about it |  |
| 205001 | Paypal Data validation error | Please ensure that you are sending the right data. One of the required parameters may be either missing or invalid. |  |

## Secure mode / 3DSecure errors
|Result Code|Result Message | More information |
| -------- | -------- | -------- |
| 101399 | Secure mode: 3DSecure authentication is not available | 3DSecure is not available. Please contact our support to unblock the situation. |
| 101304 | Secure mode: The 3DSecure authentication session has expired |  |
| 101303 | Secure mode: The card is not compatible with 3DSecure |  |
| 101302 | Secure mode: The card is not enrolled with 3DSecure |  |
| 101301 | Secure mode: 3DSecure authentication has failed |  |


## Tokenization / Card registration errors
|Result Code|Result Message | More information |
| -------- | -------- | -------- |
| 001599 | Token processing error | The token has not been created as there was a problem - check that you sent all the correct parameters. |
| 105299 | Token input Error | This is a generic error meaning that we got an error when submitting the token to the bank. It is usually returned because there was a too long time between the card registration request and the first action done with this card. Indeed, you have 20min maximum to create the first Pre-auth or Payin |
| 105202 | Card number: invalid format | This error is returned in case the card number formate is wrong (on card registration) |
| 105203 | Expiry date: missing or invalid format | This error is returned in case the expiry date is wrong (on card registration) |
| 105204 | CVV: missing or invalid format | This error is returned in case the CVV is wrong (on card registration) |
| 105205 | Callback URL: Invalid format | This error is returned in case the ReturnURL is wrong on CardRegistration process |
| 105206 | Registration data : Invalid format | This error is returned in case the data sent to the tokenization server is not the right. You can get this error when you are trying to edit the CardRegistration Object with the RegistrationData(got from the tokenization server) |

The following errors may be received by our PSP when POSTing the card data to the `CardRegistrationURL`

|Result Code|Result Message | More information | Test amount |
| -------- | -------- | -------- | -------- |
| 02625 | Invalid card number |  |  |
| 02626 | Invalid date. Use MMYY format |  |  |
| 02627 | Invalid CCV number |  |  |
| 02628 | Transaction refused | Invalid URL return field |  |
| 02101 | Internal Error | There is an issue on the tokenization server (PSP side). Please check the resolution on http://status.mangopay.com/ |  |
| 02632 | Method GET is not allowed | Your Payment form has to use POST method on Tokenization Server |  |
| 09101 | Username/Password is incorrect | Please ensure that you are sending the right registration data. |  |
| 09102 | Account is locked or inactive |  |  |
| 01902 | This card is not active |  | 333.12 |
| 02624 | Card expired |  | 333.33 |
| 09104 | Client certificate is disabled |  |  |
| 09201 | You do not have permissions to make this API call |  |  |
| 02631 | Delay exceeded | Too much time taken from the creation of the CardRegistration object to the submission of the Card Details on the Tokenizer Server |  |

### Specific JS Kit card registration errors
|Result Code|Result Message | More information | Test amount |
| -------- | -------- | -------- | -------- |
| 009999 | Browser does not support making cross-origin Ajax calls |  | 333.57 |
| 001596 | An HTTP request was blocked by the User's antivirus | Getting the token from Payline failed due to the HTTP call  being  blocked by an anti-virus/plugin/extension - for example, this is known to happen with Kaspersky if the "Safe Money" option is activated |  |
| 001597 | An HTTP request failed| | |
| 001598 | A cross-origin HTTP request failed| | |
| 001599 | Token processing error | Getting the token from Payline failed as no token data was received - most likely, the HTTP call failed for some reason - a timeout or anti-virus/plugin/extension may have blocked it |  |
| 101699 | CardRegistration should return a valid JSON response | Finishing card registration with MANGOPAY API failed as a valid JSON response wasn't received for some reason |  |
| 105204 | CVV_FORMAT_ERROR | The CVV is missing or not the required the length |  |
| 105203 | PAST_EXPIRY_DATE_ERROR or EXPIRY_DATE_FORMAT_ERROR |The expiry date is not in the future  |  |
| 105202 | CARD_NUMBER_FORMAT_ERROR | The card number is not a valid format|  |

## KYC transaction errors
|Result Code|Result Message | More information |
| -------- | -------- | -------- |
| 002999 | Blocked due to a Debited User’s KYC limitations (maximum debited or credited amount reached) | The user is not KYC-validated. You can find more information [here](https://docs.mangopay.com/guide/kyclimits).  |
| 002998 | Blocked due to the Bank Account Owner’s KYC limitations (maximum debited or credited amount reached) | The bank account needs to be KYC verified [(more info)](https://docs.mangopay.com/guide/kyclimits) |

## Transaction fraud issue
|Result Code|Result Message | More information | Test amount |
| -------- | -------- | -------- | -------- |
| 008999 | Fraud policy error |  |  |
| 008001 | Counterfeit Card | Fake card detected by the bank. The user should contact his/her bank to unblock the situation.  |  |
| 008002 | Lost Card | A "lost card" error is a rule carried by the bank which deactivate a card due to too many payments (or attempts). In Sandbox, just choose another card, this one will be reactivated soon (the day after). In Production, the card is blocked for the day or concidered as fraudulent by the bank | 333.41 |
| 008003 | Stolen Card | Similar to 008002 | 333.43 |
| 008004 | Card bin not authorized | This card has been blocked by our fraud department. Please contact our support team or use a different card |  |
| 008005 | Security violation | This card has abnormal behavior and has been blocked by our fraud department. Please contact our support or use a different card.  | 333.63 |
| 008006 | Fraud suspected by the bank | This card has abnormal behavior and has been blocked by our fraud department. Please contact our support or use a different card. | 333.34 |
| 008007 | Opposition on bank account (Temporary) | The card has temporarily been blocked on our side. Please try again later |  |
| 008500 | Transaction blocked by Fraud Policy |   This payment does not comply with our anti-fraud rules. Please contact our support team to solve the issue. |  |
| 008504 | Amount of the transaction exceeded the amount permitted |  |  |
| 008505 | Number of accepted transactions exceeded the velocity limit set | Credit/debit cards are limited to 10 payments per day for security reasons. Please try again in 24 hours. |  |
| 008506 | Unauthorized IP address country |  |  |
| 008507 | Cumulative value of transactions exceeded |  |  |
| 008508| Unauthorized Card issuer country |  |  |
| 008509 | Number of bank cards allowed is exceeded |  |  |
| 008510 | Number of clients per card is exceeded |  |  |
| 008511 | The 3DSecure authentification has failed due to supplementary security checks |  Anti-fraud rules have triggered a supplementary 3DSecure authentication and this authentication has failed |  |
| 008512 | IP location different than card issuer country |  |  |
| 008513 | Number of device fingerprints allowed is exceeded |  |  |
| 008515 |  Authentication not available: do not benefit from liability shift | 3DSecure is not available on this transaction. Liability shift has been rejected by the issuing bank. The user should contact his/her bank to solve this problem and allow the liability shift. |  |
| 008514 | Unauthorized Card BIN |  |  |
| 008600 | Wallet blocked by Fraud policy |  |  |
| 008700 | User blocked by Fraud policy |   This user does not comply with our anti-fraud rules. Please contact our support team to solve the issue. |  |

## Technical errors
|Result Code|Result Message | More information | Test amount |
| -------- | -------- | -------- | -------- |
| 009103 | PSP configuration error |  | 333.03 |
| 009199 | PSP technical error | The error code is returned in the following cases: <ul><li>Card is not supported by Mangopay</li><li>Amount is higher than the maximum amount per transaction</li><li>Operation doesn’t fit to your Mangopay account settings </li><li>Use of a non-3DSecure test card for a payment which requires 3DSecure</li></ul> | 333.94 |
| 009499 | Bank technical error | The Bank has denied the payment for unknown reasons. The user should contact his/her bank for more information. | 333.91 |
| 009999 | Technical error |  |  |
| 009101 | PSP timeout please try later |  |  |
| 101202 | Bank not supported for Giropay | The user's bank does not support Giropay payments.  |  |

## Payout error codes
* If your payout is successfully treated (your payout becomes SUCCEEDED), it can later be reaccredited for a variety of reasons.
* In this case, the payout stays as "SUCCEEDED" but a new transaction is created, which will be a Refund of the original Payout (in the same way you can have a refunded Payin except the difference is that its not client driven).
* In this case, as for payin refunds, you’ll have 2 fields within `RefundReason` -> `RefundReasonMessage` and `RefundReasonType`. Possible `RefundReason` are: BANKACCOUNT_INCORRECT, BANKACCOUNT_HAS_BEEN_CLOSED, OWNER_DOT_NOT_MATCH_BANKACCOUNT, WITHDRAWAL_IMPOSSIBLE_ON_SAVINGS_ACCOUNTS. This will usually be accompanied by a custom message in the `RefundReasonMessage` field

|Result Code|Result Message | More information |
| -------- | -------- | -------- |
| 121999 | Generic withdrawal error | -------- |
| 121001 | The bank wire has been refused | The bankwire has been refused by MGP or cancelled by the user. You should contact us to unblock the situation and allow the bankwire towards MGP. |
| 121002 | The author is not the wallet owner | -------- |
| 121003 or 001001 | Insufficient wallet balance | -------- |
| 121004 | Specific case: please contact our Support Team | -------- |
| 121005 | Refused due to the Fraud Policy | -------- |
| 121006 | The associated bank account is not active | -------- |
| 002998 | Blocked due to the Bank Account Owner’s KYC limitations (maximum debited or credited amount reached) | The bank account needs to be KYC verified ([more info](https://docs.mangopay.com/guide/kyclimits)) |
| 002999 | Blocked due to a Debited User’s KYC limitations (maximum debited or credited amount reached) | One of the user’s who has contributed to the wallet being debited needs to be KYC verified ([more info](https://docs.mangopay.com/guide/kyclimits/guide/kyc)) |

## KYC document errors
|Refused Reason Type | IDENTITY_PROOF | REGISTRATION_PROOF  | ARTICLES_OF_ASSOCIATION | SHAREHOLDER_DECLARATION
| -------- | -------- | -------- | -------- | -------- |
| DOCUMENT_UNREADABLE | <ul><li>Document is fuzzy, unreadable</li><li>MRZ band is cut, must be perfectly readable (no flash)</li></ul> | A clear copy of your Up-to-date Extract from the Companies Register is required. The one provided is not clear enough | A clear copy of Up-to-date Articles of Association is required. The one provided is not clear enough | A clear copy of Up-to-date shareholder declaration is required. The one provided is not clear enough |
| DOCUMENT_NOT_ACCEPTED | <ul><li>Document is not acceptable</li><li>Document is not a national identity card, passport required out of the EEA</li><li>Document is not an ID proof accepted by our terms and conditions guideline</li></ul> | Document is not acceptable, it doesn't fit the KYC requirements guideline agreed with us | Document is not acceptable, it doesn't fit the KYC requirements guideline agreed with us | Document is not acceptable, it doesn't fit the KYC requirements guideline agreed with us |
| DOCUMENT_HAS_EXPIRED | <ul><li>ID proof is expired</li></ul>Only for FR, extended validity period from 10 to 15 years is not applicable if:<ul><li>individual was underage when document was issued</li><li>the document was issued before the 02/01/2004</li></ul> | <ul><li>Document is outdated (more than 3 months) </li><li> A recent copy of Up-to-date Extract from the Companies Register is required (maximum 3 months old)</li></ul> | <ul><li> Document is outdated </li><li> A copy of Up-to-date Articles of Association (which include the last modifications made) is required</li></ul> | N/A |
| DOCUMENT_INCOMPLETE | <ul><li>Document incomplete </li><li> Front or backside of the document is missing </li></ul> | <ul><li> A recent copy of Up-to-date Extract from the Companies Register is required </li><li> All the pages of the document need to be provided</li></ul> | The full copy of the Up-to-date Articles of Association is required (all the pages signed of the document need to be provided) | <ul><li>Date, name or signature is missing </li><li> Document was left blanked </li><li> Only legal entity legal person chart is completed and not the individual one </li><li> Important to know who INDIRECTLY own the company if a holding company has the first level ownership</li></ul> |
| DOCUMENT_DO_NOT_MATCH_USER_DATA | <ul><li>Declarative data and document data do not match </li><li> NATURAL USER: declarative data FirstName and LastName do not match with document data </li><li> LEGAL_PERSONALITY: declarative data LegalRepresentative FirstName and LegalRepresentative LastName do not match with document data </li><li> Declarative data should be edited and the document resubmitted: First name and Last name are compulsory, middle name is optional</li></ul> | N/A | N/A | N/A |
| DOCUMENT_DO_NOT_MATCH_ACCOUNT_DATA | Bank account title do not match wallet owner data | N/A | N/A | N/A |
| DOCUMENT_FALSIFIED| Document is falsified:<ul><li>Account will be blocked</li><li>Partner will be contacted, meanwhile fraud team will check all related transactions</li></ul> | N/A | N/A | N/A |
| UNDERAGE PERSON |Individual is underage and can not process transactions through MGP 18+ only | N/A | N/A | N/A |
| SPECIFIC_CASE | Specific case, please refer to RefusedReasonMessage for further informations | N/A | N/A | N/A |





## UBO DECLARATION errors
<ul><li>When an UBO declaration is INCOMPLETE, it is possible to modify / add information. </li> 
<li>When it is in REFUSAL : it will be necessary to make a new UBO declaration.</li></ul>
|Refused Reason Type | More information |
| -------- | -------- |
| MISSING_UBO | We miss some people in you declaration. </br></br>  ex:  in the statutes we have 2 shareholders having 50% and 50%, if only one is indicated, it is a missing UBO  | 
| WRONG_UBO_INFORMATION | Name, first name, or other parameters are incorrectly entered. | 
| UBO_IDENTITY_NEEDED | We need the UBO ID. | 
| SHAREHOLDER_DECLARATION_NEEDED | The statutes are silent, so we cannot verify if the information provided in the UBO is correct: We need a shareholder declaration document | 
| ORGANIZATION_CHART_NEEDED | In case of a complex holding architecture we need the organization chart | 
| DOCUMENT_NEEDED | We are waiting the statutes and / or proof of registration to verify that all is correct. | 
| DECLARATION_DO_NOT_MATCH_UBO_INFORMATION | The information provided does not match the information we have on the UBO. |


## Mandates errors
The table below lists the range of statuses that can be applied to a Direct Debit mandate, along with the corresponding description of when that status applies.

|Result Code|Result Message | More information |
| -------- | -------- | -------- |
| 001801 | The bank account has been closed |   |
| 001802 | The bank details supplied were incorrect |   |
| 001803 | Direct debit is not enabled for this bank account |   |
| 001804 | The user has disputed the authorisation of the mandate |   |
| 001805 | The user has cancelled the mandate |   |
| 001806 | The client has cancelled the mandate |   |
| 001807 | User has let the mandate session expire without confirming |   |
| 001024 | Author is not the Mandate owner |   |
| 001830 | There are insufficient funds in the bank account |   |
| 001831 | Contact the user |   |
| 001832 | The payment has been cancelled |   |
| 001833 | The Status of this Mandate does not allow for payments |   |
| 001834 | The user has disputed the payment |   |
| 009999 | Technical error |   |
| 001835 | The mandate has expired | No collection attempts were made against the mandate for over 13 months. As a result, it has expired, is inactive, and no further collections can be taken against it  |
| 001836 | The mandate has been submitted to the user’s bank | The mandate has been submitted to the customer's bank to set up against their bank account  |
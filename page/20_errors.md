# Error codes
With the Visa/Mastercard credit cards, you can trigger specific error codes by using the transaction amounts given in the column "Test amount"

## Operation failed

|ResultCode|ResultMessage| More information | Test amount |
| -------- | -------- | -------- | -------- |
| 001999 |	Generic Operation error	| Mangopay has no information for the bank yet	| |
| 001001 |	Unsufficient wallet balance |	The wallet balance doesn’t allow to process transaction	 | |
| 001002 |	Author is not the wallet owner |	The user ID used as Author has to be the wallet owner | |	
| 001011 |	Transaction amount is higher than maximum permitted amount	 | | |	
| 001012 |	Transaction amount is lower than minimum permitted amount		 | | |
| 001013 |	Invalid transaction amount |  |		333.13 |
| 001014 |	CreditedFunds must be more than 0 (DebitedFunds can not equal Fees)	 | | |

## PayIn Web errors
|ResultCode|ResultMessage | More information |
| -------- | -------- | -------- |
| 001030 |	User has not been redirected	| The user never gets the payment page and never opens the Payline session |
| 001031 |	User canceled the payment |	The User clicks on "Cancelled" on the payment page	 |
| 101002 |	The transaction has been cancelled by the user |	The User clicks on "Cancelled" on the payment page |	
| 001032 |	User is filling in the payment card details	| The user is still on the payment page (Payline session) |	
| 001033 |	User has not been redirected then the payment session has expired | The session has expired so the Payin Web is failed. The user has gone on the payment page |
| 001034 |	User has let the payment session expire without paying | The user went to the payment page but let the session expired. So the Payin Web has failed |
| 101001 |	The user does not complete transaction | |

## Refund transaction errors
|ResultCode|ResultMessage | More information |
| -------- | -------- | -------- |
| 001401 | Transaction has already been successfully refunded | |
| 005403 | The refund cannot exceed initial transaction amount | |
| 005404 | The refunded fees cannot exceed initial fee amount | |
| 005405 | Balance of client fee wallet insufficient | |
| 005407 | Duplicated operation: you cannot refund the same amount more than once for a transaction during the same day | |

## Card input errors
|ResultCode|ResultMessage| More information | Test amount |
| -------- | -------- | -------- | -------- |
| 105101 | Invalid card number |  | 333.14 |
| 105102 | Invalid cardholder name | The card holder name given doesn’t match the real owner of the card |  |
| 105103 | Invalid PIN code |  | 333.55 |
| 105104 | Invalid PIN format |  |  |

## Transaction Refused
|ResultCode|ResultMessage | More information | Test amount |
| -------- | -------- | -------- | -------- |
| 101101 | Transaction refused by the bank (Do not honor) | The error "Do not honor" is a message from the bank. You could get it for several raisons: Maximum amount spent per month has been reached on this card // Maximum amount spent on internet per month has been reached on this card // No more funds on bank account | 333.05 |
| 101102 | Transaction refused by the bank (Amount limit) | You will get this error if the user reached a bank amount limit. It could be: Maximum pre authorized amount reached // Maximum amount spent per month has been reached on this card // Maximum amount spent on internet per month has been reached on this card | 333.51 |
| 101103 | Transaction refused by the terminal |  | 333.58 |
| 101104 | Transaction refused by the bank (card limit reached) |  | 333.60 |
| 101105 | The card has expired |  |  |
| 101106 | The card is inactive | The card is not active accourding to the bank and can therefore not be used |  |
| 101410 | The card is not active | The card has not been disabled on Mangopay and is no longer useable |  |
| 101111 | Maximum number of attempts reached | Too much attempts for the same transaction | 333.38 |
| 101112 | Maximum amount exceeded | This is a card limitation on spent amount |  |
| 101113 | Maximum Uses Exceeded | Maximum attempts with this cards reached. You must try again after 24 hours |  |
| 101115 | Debit limit exceeded | This is a card limitation on spent amount | 333.61 |
| 101116 | Amount limit | The contribution transaction has failed |  |
| 101199 |Transaction refused | The transaction has been refused by the bank. Contact your bank in order to have more information about it |  |

## Secure mode / 3DSecure errors
|ResultCode|ResultMessage | More information |
| -------- | -------- | -------- |
| 101399 | Secure mode: 3DSecure authentication is not available |  |
| 101304 | Secure mode: The 3DSecure authentication session has expired |  |
| 101303 | Secure mode: The card is not compatible with 3DSecure |  |
| 101302 | Secure mode: The card is not enrolled with 3DSecure |  |
| 101301 | Secure mode: 3DSecure authentication has failed |  |


## Tokenization / Card registration errors
|ResultCode|ResultMessage | More information |
| -------- | -------- | -------- |
| 001599 | Token processing error | The token has not been created as there was a problem - check that you sent all the correct parameters. |
| 105299 | Token input Error | This is a generic error meaning that we got an error when submitting the token to the bank. It is usually returned because there was a too long time between the card registration request and the first action done with this card. Indeed, you have 20min maximum to create the first Pre-auth or Payin |
| 105202 | Card number: invalid format | This error is returned in case the card number formate is wrong (on card registration) |
| 105203 | Expiry date: missing or invalid format | This error is returned in case the expiry date is wrong (on card registration) |
| 105204 | CVV: missing or invalid format | This error is returned in case the CVV is wrong (on card registration) |
| 105205 | Callback URL: Invalid format | This error is returned in case the ReturnURL is wrong on CardRegistration process |
| 105206 | Registration data : Invalid format | This error is returned in case the data sent to the tokenization server is not the right. You can get this error when you are trying to edit the CardRegistration Object with the RegistrationData(got from the tokenization server) |

The following errors may be received by our PSP when POSTing the card data to the `CardRegistrationURL`

|ResultCode|ResultMessage | More information | Test amount |
| -------- | -------- | -------- | -------- |
| 02625 | Invalid card number |  |  |
| 02626 | Invalid date. Use mmdd format |  |  |
| 02627 | Invalid CCV number |  |  |
| 02628 | Transaction refused | Invalid URL return field |  |
| 02101 | Internal Error | There is an issue on the tokenization server (PSP side). Please check the resolution on http://status.mangopay.com/ |  |
| 02632 | Method GET is not allowed | Your Payment form has to use POST method on Tokenization Server |  |
| 09101 | Username/Password is incorrect |  |  |
| 09102 | Account is locked or inactive |  |  |
| 01902 | This card is not active |  | 333.12 |
| 02624 | Card expired |  | 333.33 |
| 09104 | Client certificate is disabled |  |  |
| 09201 | You do not have permissions to make this API call |  |  |
| 02631 | Delay exceeded | Too much time taken from the creation of the CardRegistration object to the submission of the Card Details on the Tokenizer Server |  |

### Specific JS Kit card registration errors
|ResultCode|ResultMessage | More information | Test amount |
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
|ResultCode|ResultMessage | More information |
| -------- | -------- | -------- |
| 002999 | Blocked due to a Debited User’s KYC limitations (maximum debited or credited amount reached) |  |
| 002998 | Blocked due to the Bank Account Owner’s KYC limitations (maximum debited or credited amount reached) |  |

## Transaction fraud issue
|ResultCode|ResultMessage | More information | Test amount |
| -------- | -------- | -------- | -------- |
| 008999 | Fraud policy error |  |  |
| 008001 | Counterfeit Card |  |  |
| 008002 | Lost Card | A "lost card" error is a rule carried by the bank which deactivate a card due to too many payments (or attempts). In Sandbox, just choose another card, this one will be reactivated soon (the day after). In Prodcution, the card is blocked for the day or concidered as fraudulent by the bank | 333.41 |
| 008003 | Stolen Card | Similar to 008002 | 333.43 |
| 008004 | Card bin not authorized |  |  |
| 008005 | Security violation |  | 333.63 |
| 008006 | Fraud suspected by the bank |  | 333.34 |
| 008007 | Opposition on bank account (Temporary) |  |  |
| 008500 | Transaction blocked by Fraud Policy |  |  |
| 008600 | Wallet blocked by Fraud policy |  |  |
| 008700 | User blocked by Fraud policy |  |  |

## Technical errors
|ResultCode|ResultMessage | More information | Test amount |
| -------- | -------- | -------- | -------- |
| 009103 | PSP configuration error |  | 333.03 |
| 009199 | PSP technical error | The error code is returned in the following cases: <ul><li>Card is not supported by Mangopay</li><li>Amount is higher than the maximum amount per transaction</li><li>Operation doesn’t fit to your Mangopay account settings </li><li>Use of a non-3DS test card for a payment which requires 3DS</li></ul> | 333.94 |
| 009499 | Bank technical error |  | 333.91 |
| 009999 | Technical error |  |  |
| 009101 | PSP timeout please try later |  |  |

## Payout error codes
* If your payout is successfully treated (your payout becomes SUCCEEDED), it can later be reaccredited for a variety of reasons.
* In this case, the payout stays as "SUCCEEDED" but a new transaction is created, which will be a Refund of the original Payout (in the same way you can have a refunded Payin except the difference is that its not client driven).
* In this case, as for payin refunds, you’ll have 2 fields within `RefundReason` -> `RefundReasonMessage` and `RefundReasonType`. Possible `RefundReason` are: BANKACCOUNT_INCORRECT, BANKACCOUNT_HAS_BEEN_CLOSED, OWNER_DOT_NOT_MATCH_BANKACCOUNT, WITHDRAWAL_IMPOSSIBLE_ON_SAVINGS_ACCOUNTS. This will usually be accompanied by a custom message in the `RefundReasonMessage` field

|ResultCode|ResultMessage | More information |
| -------- | -------- | -------- |
| 121999 | Generic withdrawal error | -------- |
| 121001 | The bank wire has been refused | -------- |
| 121002 | The author is not the wallet owner | -------- |
| 121003 or 001001 | Insufficient wallet balance | -------- |
| 121004 | Specific case: please contact our Support Team | -------- |
| 121005 | Refused due to the Fraud Policy | -------- |
| 002998 | Blocked due to the Bank Account Owner’s KYC limitations (maximum debited or credited amount reached) | The bank account needs to be KYC verified ([more info](/guide/kyc)) |
| 002999 | Blocked due to a Debited User’s KYC limitations (maximum debited or credited amount reached) | One of the user’s who has contributed to the wallet being debited needs to be KYC verified ([more info](/guide/kyc)) |

## KYC document errors
|RefusedReasonCode|RefusedReasonMessage | More information |
| -------- | -------- | -------- |
| DOCUMENT_UNREADABLE | A custom description will potentially appears into the RefusedReasonMessage field | This means Mangopay can’t read the document. The error code will appears on RefusedReasonType, the custom description on RefusedReasonMessage |
| DOCUMENT_NOT_ACCEPTED | A custom description will potentially appears into the RefusedReasonMessage field | This means the document is unvalidate. The error code will appears on RefusedReasonType, the custom description on RefusedReasonMessage |
| DOCUMENT_HAS_EXPIRED | A custom description will potentially appears into the RefusedReasonMessage field | This means the document has expired. The error code will appears on RefusedReasonType, the custom description on RefusedReasonMessage |
| DOCUMENT_INCOMPLETE | A custom description will potentially appears into the RefusedReasonMessage field | This means Mangopay the document is incomplete. The error code will appears on RefusedReasonType, the custom description on RefusedReasonMessage |
| DOCUMENT_MISSING | A custom description will potentially appears into the RefusedReasonMessage field | This means Mangopay there is no doument sent. The error code will appears on RefusedReasonType, the custom description on RefusedReasonMessage |
| DOCUMENT_DO_NOT_MATCH_USER_DATA | A custom description will potentially appears into the RefusedReasonMessage field | The error code will appears on RefusedReasonType, the custom description on RefusedReasonMessage |
| DOCUMENT_DO_NOT_MATCH_ACCOUNT_DATA | A custom description will potentially appears into the RefusedReasonMessage field | The error code will appears on RefusedReasonType, the custom description on RefusedReasonMessage |
| SPECIFIC_CASE | A custom description will potentially appears into the RefusedReasonMessage field | The error code will appears on RefusedReasonType, the custom description on RefusedReasonMessage |
| OTHER | A custom description will potentially appears into the RefusedReasonMessage field | The error code will appears on RefusedReasonType, the custom description on RefusedReasonMessage |
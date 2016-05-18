A direct debit mandate is an instruction between a user and a bank account which allows you to process payments directly from his bank to a wallet for a dedicated user.
* After using this method, you can then use it to do a direct debit payin (in a similar way to registering a card and then doing a direct card payin for that card.
* Mandates and direct debit payins are only available for certain business types, and is not activated by default – please contact your sales manager for more info
* Mandates cover only payments in Europe, and this is split between two schemes (see Scheme in the mandate object) – BACS (for the UK) and SEPA (the rest of the EU). MANGOPAY handles the complexities and strict compliance regulations in each case, but you should be aware of a couple of particularities:
-  Only GBP payments can be made with mandates in the BACS Scheme
- The confirmation page and emails for mandates in the BACS Scheme are only available in English
* Only bank account types GB and IBAN can be used to create a Mandate
* When a mandate in the BACS Scheme is confirmed by the user, we will send them an email on your behalf (the design of this email, and the confirmation webpage they see, can be lightly customised – see here)
* Once confirmed, mandates have the Status "SUBMITTED which means it has been submitted to the user’s bank and will become "ACTIVE" after a few days. However, you can immediately make payments against the mandate (ie you do not need to wait for the Status to become "ACTIVE") and we will manage the submission process for you – read more about the timings on the payments page
* For testing mandates, you should use a specific value for the FirstName for the user owning the mandate
* "Invalid" will result in a failed mandate due to incorrect bank account information – note that this only works for mandates with the `Scheme` "BACS"
* "Successful" will result in an active mandate, however you must do a payment with this mandate for the status to be updated
* Note that for all the mandate list methods, the usual pagination and filter parameters are available, such as `BeforeDate`, `AfterDate` and `Status` and you can order by `CreationDate`
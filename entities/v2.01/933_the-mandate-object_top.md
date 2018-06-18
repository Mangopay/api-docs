A `Direct Debit Mandate` is an instruction between a user and a bank account which allows you to process payments directly from his bank to a wallet for a dedicated user.
* After using this method, you can then use it to do a [entity_link entity="288"]direct debit payin[/entity_link] (in a similar way to registering a card and then doing a direct card payin for that card.
* Mandates and [entity_link entity="288"]direct debit payin[/entity_link] are only available for certain business types, and is not activated by default – please contact your sales manager for more info
* Mandates cover only payments in Europe, and this is split between two schemes (see Scheme in the mandate object) – BACS (for the UK) and SEPA (the rest of the EU). MANGOPAY handles the complexities and strict compliance regulations in each case, but you should be aware of a couple of particularities:
1. Only GBP payments can be made with mandates in the BACS Scheme
2. The confirmation page and emails for mandates in the BACS Scheme are only available in English
3. Only bank account types GB and IBAN can be used to create a Mandate
* When a mandate in the BACS Scheme is confirmed by the user, we will send them an email on your behalf (the design of this email, and the confirmation webpage they see, can be lightly customised with your logo and colours – see [entity_link entity="200"]the client object[/entity_link] for more info on that)
* Once confirmed, mandates have the Status "SUBMITTED which means it has been submitted to the user’s bank and will become "ACTIVE" after a few days. For SEPA, you can immediately make a Direct Debit Payin against the mandate. This first payment will  change the status from SUBMITTED to ACTIVE– read more about the timings on the [entity_link entity="289"]payments page[/entity_link]
* For testing mandates, you should use a specific value for the FirstName for the user owning the mandate
1. "Invalid" will result in a failed mandate due to incorrect bank account information – note that this only works for mandates with the `Scheme` "BACS"
2. "Successful" will result in an active mandate, however you must do a payment with this mandate for the status to be updated
* Note that for all the mandate list methods, the usual [pagination](/guide/lists-pagination-management) and filter parameters are available, such as `BeforeDate`, `AfterDate` and `Status` and you can order by `CreationDate`
* **For UK clients**: note that mandates can't be created on accounts where multiple signatures are required (business accounts). 

[alert type="info"]Note that the language for the mandate confirmation pages and mandate PDFs is only English and French for now[/alert]
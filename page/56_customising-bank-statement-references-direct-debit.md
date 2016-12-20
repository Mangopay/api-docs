#Customising bank statement references (direct debit)
[alert type="info"]Note that this functionality is only available for SEPA (European) payments, and not BACS (UK)[/alert]
* You have the ability to add a custom statement descriptor (or reference) for each PayIn – this can be specified via the `StatementDescriptor` field in the `PayIn` object
* The `StatementDescriptor` field can be up to 100 characters long, and can only include alphanumeric characters or spaces. This field is however entirely optional and can be left blank
* The information shown on the bank statement is made up of two elements – the name of your account (specified when creating your account) and the optional statement descriptor payin reference. A full example is as follows:
> GC re MANGOPAY `ClientName` `StatementDescriptor`
* You should be aware however that each bank handles this information differently – some may show less or none of the reference and we have no control over this – we continue to work with our partners to improve this
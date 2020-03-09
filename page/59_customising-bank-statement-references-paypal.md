#Customising bank statement references (Paypal)
[alert type="danger"]Note that this functionality is in private beta and not available for all clients[/alert]
* You have the ability to add a custom statement descriptor (or reference) for each Paypal PayIn – this can be specified via the `StatementDescriptor` field in the `Paypal Web PayIn` object.
* The `StatementDescriptor` field can be up to 10 characters long, and can only include alphanumeric characters or spaces. This field is however entirely optional and can be left blank.
* The information shown on the bank statement is made up of two elements – the name of your account (specified when creating your account) and the optional statement descriptor payin reference. A full example is as follows:
> MGP\* `ClientName` `StatementDescriptor`
* The information shown on the bank statement can be up to 22 characters long. If your `ClientName` is too long we truncate this field.
* You should be aware however that each bank handles this information differently – some may show less or none of the reference and we have no control over this – we continue to work with our partners to improve this
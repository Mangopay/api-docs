#Customising bank statement references (payouts)
* You have the ability to add a custom statement reference for each Payout – this can be specified via the `BankWireRef` field in the `Payout` object. 
* The `BankWireRef` field can be up to 12 characters long, and can only include alphanumeric characters or spaces. This field is however entirely optional and can be left blank
* The information shown on the bank statement is made up of two elements – the name of your account (specified when creating your account) and the optional bank wire reference. A full example is as follows:
> MGP\* `ClientName` `BankWireRef`
* You should be aware however that each bank handles this information differently – some may show less or none of the reference and we have no control over this – we continue to work with our partners to improve this
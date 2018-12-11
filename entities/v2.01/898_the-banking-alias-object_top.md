Banking aliases allow you to create a way to pay funds directly into a wallet, without having to declare the payin beforehand (unlike a traditional [entity_link entity="280"]payin bankwire[/entity_link]). For example, if you create an IBAN banking alias for a wallet, you'll be given a unique IBAN and BIC for this wallet. Any funds that we receive for this IBAN and BIC will be automatically credited to the wallet. You should be aware that you are unable to add `Fees` to a payin created via a banking alias.

[alert type="info"]Note that only IBAN type banking aliases are available at present, and only the currency EUR is supported. You are also only able to create one banking alias per wallet due to regulation requirements. Once created, you can not change the `CreditedUserId`[/alert]


These are the base parameters for a Banking Alias - for each type (see below) there are various other parameters specific to that type.

Please note that this functionality doesn't work with the old SDK versions, and with system prior to PHP 5.4.
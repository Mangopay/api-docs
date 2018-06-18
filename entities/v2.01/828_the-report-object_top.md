The `Report`object gives the possibility to download huge lists of transactions or wallets to CSV format for accounting or analysis purposes. This can be done either from the API or Dashboard.

You can choose certain filters including:

**Transactions**

* A date range (`BeforeDate` and `AfterDate`) - note that the range can’t be more than 6 months, and must be < 13 months ago
* Min/Max `DebitedFunds`
* Min/Max `Fees`
* A `WalletId`
* A `UserId`
* A transaction `Type` (PAYIN, PAYOUT or TRANSFER)
* A transaction `Status` (CREATED, SUCCEEDED or FAILED)
* A transaction `Nature` (REGULAR, REFUND, REPUDIATION or SETTLEMENT)
* A `ResultCode`

**Wallets**
* A date range (`BeforeDate` and `AfterDate`) - note that the range can’t be more than **24 months**, but with **no limitations** on historical data.
* Min/Max `BalanceAmount`
* A wallet `Currency`
* A wallet `CreationDate`
* A wallet `Owner`


In each case, you can specify multiple values if you wish.

You also get to choose what datas you want to see (`Columns`) for each transaction - eg you might just be interested in seeing `CreationDate`, `AuthorId`, `DebitedFunds` and `CardType` for example.

A report can be requested and then we’ll update it’s `Status` as soon as it’s ready to download - the wait time is normally only a couple of seconds though. We’ll also ping a particular URL (`CallbackURL`) if you specified one - just like for hook notifications.

[alert type="info"]Note that reports expire after 24 hours (ie they’ll be no longer available) but you can “rerun” the same report from the Dashboard very easily.[/alert]
[alert type="info"] To ensure that data provided on each report are up-to-date, `BeforeDate` cannot be greater than report creation date minus 5 minutes. If it is, `BeforeDate` will be automatically set according to this constraint. [/alert]
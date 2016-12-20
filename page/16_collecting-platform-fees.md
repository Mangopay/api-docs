# Collecting platform fees
**Summary**: MANGOPAY charges its "service fees" (for example 1.8% + 0.18€) per transaction in €, however we never charge your users, but only you. This means that in the API, you won't see any mention of these service fees. You will however see a field called `Fees` which is totally different - with this, you can decide to collect **your own fees** (perhaps your commission) during the PayIn, Transfer or even PayOut (or infact on any transaction, even Refunds).

**Example use case:**
Let’s say for this example that your platform takes 10% commission and that you decide to add this fee when the user does a PayOut Bankwire (from their wallet to a bank account). Then:
1. The user A does a PayIn of 10€ (in the API, this would be requested as `DebitedFunds`=1000 and `Fees`=0)
2. User A therefore receives 10€ in his wallet
3. User A does a Transfer to User B’s wallet
3. User B decides to do a PayOut to her bank account  (in the API, this would be requested as `DebitedFunds`=1000 and `Fees`=100)
4. User B receives in her bank account 9€ (10€ – 10% of the fees that you took)

Your platform fees (the 1€ in this example) are automatically placed into a seperate wallet called the "Fees wallet" (note that you'll have one for each currency) and held there until you are next invoiced (when we'll send you the balance, minus our service fees). You can view the available funds in this wallet, however you are not able to create transactions directly involving it (ie you can not do a PayIn directly to this wallet nor PayOut the funds yourself). You can read more about accessing your client wallets [entity_link entity="271"]here[/entity_link].
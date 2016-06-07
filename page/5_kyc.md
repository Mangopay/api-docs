# KYC and compliance

[KYC means "Know Your Customer"](https://en.wikipedia.org/wiki/Know_your_customer) and are a set of legal obligations related to our license as an electronic money issuer and are neccessary in order to fight fraud, money laundering and financing of terrorism. There are 3 levels of validation (light, regular and strong) and the whole process of uploading documents and viewing a user's KYC level is all **managed through the API**. A higher KYC level allows a user to handle higher volumes of cash flows:

* **Light validation**: Transactions worth less than €2,500 for **cash-in** and/or €1,000 for **cash-out** cumulated **per legal year and per user** (transfers are also counted in this equation)
* **Regular validation**: Transactions worth more than €2,500 for **cash-in** and/or €1,000 for **cash-out** cumulated **per legal year and per user**
* **Strong validation**: Clients suspected of money laundering and/or terrorism and/or politically exposed persons

[alert type="info"]A user will never be blocked due to going over their allowed KYC volumes when doing a payin - it is a transfer or payout that will be blocked[/alert]

To change the KYC level, you must provide certain information about the user, as well as various documents (detailed below):

|Document type|Usage|
| -------- | -------- |
|"IDENTITY_PROOF"|ID Card or Passport <sup>(1)</sup> or driving licence for UK, USA and Canada (a passport is required outside of SEPA area)<br>In the case of a legal user, this document should refer to the individual duly empowered to act on behalf of the legal entity|
|"ARTICLES_OF_ASSOCIATION"|Certified articles of association (Statute) - formal memorandum stated by the entrepreneurs, in which the following information is mentioned: business name, activity, registered address, shareholding…|
|"REGISTRATION_PROOF"|Extract from the Company Register issued within the last three months<sup>(4)</sup><br>In the case of an organization or soletrader, this can be a proof of registration from the official authority|
|"SHAREHOLDER_DECLARATION"|Send information referring to the [shareholder declaration](https://www.mangopay.com/terms/shareholder-declaration/Shareholder_Declaration-EN.pdf)|
|"ADDRESS_PROOF"|A proof of address<sup>3</sup>|


## Light Authentification
[alert type="info"]Allows for up to 2500€ for cash-in and up to 1000€ for cash-out (per user, per year)[/alert]

This is the basic information you are **required** to collect from your users in order to process payments (Cash-in / Cash-out). We cannot allow any transactions from a user who has not provided the following information:


|Person type|Required infos|Required KYC documents|
| -------- | -------- | -------- |
|Natural|Email - `Email`<br>First name - `FirstName`<br>Last name - `LastName`<br>Country of Residence  - `CountryOfResidence`<br>Birthday - `Birthday`<br>Nationality - `Nationality`|*None*|
|Legal|Business Name - `Name`<br>Generic business email - `Email`<br>First name of the legal representative - `LegalRepresentativeFirstName`<br>Last name of the legal representative - `LegalRepresentativeLastName`<br>Birthday of the legal representative - `LegalRepresentativeBirthday`<br>Nationality of the legal representative - `LegalRepresentativeNationality`<br>Country of residence of the legal representative - `LegalRepresentativeCountryOfResidence`|*None*|


## Regular Authentification
[alert type="info"]Allows for unlimited cash-in or cash-out (per user, per year)[/alert]

As well as the information for "light" level, this is the information **you are required** to collect from your users to go over the Cash-in (€2,500)  and/or Cash-out (€1,000) limits:

|Person type|LegalPersonType|Required infos|Required KYC documents|
| -------- | -------- | -------- | -------- |
|Natural|n/a|Address - `Address`<br>Occupation<sup>(2)</sup> - `Occupation`<br>Income range<sup>(2)</sup> - `IncomeRange`|ID Card or Passport <sup>(1)</sup> or driving licence for UK, USA and Canada (a passport is required outside of SEPA area) - "IDENTITY_PROOF"|
|Legal|Business|Headquarters address - `HeadquartersAddress`<br>Legal representative email - `LegalRepresentativeEmail`<br>Legal representative address - `LegalRepresentativeAddress`|"IDENTITY_PROOF"<br>"ARTICLES_OF_ASSOCIATION"<br>"REGISTRATION_PROOF"<br>"SHAREHOLDER_DECLARATION"|	
|Legal|Organization|*As above*|"IDENTITY_PROOF"<br>"ARTICLES_OF_ASSOCIATION"<br>"REGISTRATION_PROOF"|
|Legal|Soletrader|*As above*|"IDENTITY_PROOF"<br>"REGISTRATION_PROOF"|

[alert type="info"]Note that you can change the `LegalPersonType` once it has been set (although if the user doesn't have the required KYC docs for the new value as per the table above, their KYC level will be downgraded as you would expect)[/alert]

## Strong Authentification
This KYC level is used when a user is suspected of money laundering, terrorism or for politically exposed persons. Note that this level is manual and not managed via the API.

As well as the information for "light" level, this is the information we required in specific cases.

* For a natural user, an "ADDRESS_PROOF" is required
* For a legal user, confirmation of bank details must be provided (this must be sent to us manually and can not be done via the API)


-----


> *(1) ID card: Front AND Back (Valid) OR Passport (Valid)*
> 
> *(2) For credit and debit transactions worth more than €15,000*
> 
> *(3) Confirmation of residence: Less than a year old. Residencial Registration Form*
> * *Water/electricity/gas/telephone bill*
> * *Tax certificate*
> * *Householder insurance*
> * *Confirmation of real estate ownership*
> 
> *(4) Less than 3 months old*
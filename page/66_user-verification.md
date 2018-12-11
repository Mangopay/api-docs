# KYC and Compliance

There are two levels of user verification, also called API levels: Light (default) and Regular. 
* Light (default) verification  requires basic information provided during the user [creation process.](https://docs.mangopay.com/endpoints/v2.01/users#e253_the-user-object) 
* Regular verification requires identity proof which allows users to handle unlimited funds freely. 

## Light verification

Every user provides basic information to create a profile in our system. This will enable him to handle funds freely under  certain [limits](https://docs.mangopay.com/guide/kyclimits).

Here is the information which we require: 

|Person type|Required infos|Required KYC documents|
| -------- | -------- | -------- |
|Natural user: Individual|Email - `Email`<br>First name - `FirstName`<br>Last name - `LastName`<br>Country of Residence  - `CountryOfResidence`<br>Birthday - `Birthday`<br>Nationality - `Nationality`|*None*|
|Legal user: Legal entity|Business Name - `Name`<br>Generic business email - `Email`<br>First name of the legal representative - `LegalRepresentativeFirstName`<br>Last name of the legal representative - `LegalRepresentativeLastName`<br>Birthday of the legal representative - `LegalRepresentativeBirthday`<br>Nationality of the legal representative - `LegalRepresentativeNationality`<br>Country of residence of the legal representative - `LegalRepresentativeCountryOfResidence`|*None*|


## Regular verification
[alert type="info"]Allows for unlimited cash-in or cash-out (per user, per year)[/alert]

In addition to the information provided for “light” verification, the following is the information** you are required** to collect from your users to allow them to go over the default [limit](https://docs.mangopay.com/guide/kyc-1). Users will need to provide at least one document proving their identity.

|Person type|LegalPersonType|Required infos|Required KYC documents|
| -------- | -------- | -------- | -------- |
|Natural|n/a|	n/a |ID Card or Passport <sup>(1)</sup> or driving licence for UK, USA and Canada (a passport is required outside of SEPA area) - "IDENTITY_PROOF"|
|Legal|Business|Headquarters address - `HeadquartersAddress`<br>Legal representative email - `LegalRepresentativeEmail`<br>Legal representative address - `LegalRepresentativeAddress`|"IDENTITY_PROOF"<br>"ARTICLES_OF_ASSOCIATION"<br>"REGISTRATION_PROOF"<br>"SHAREHOLDER_DECLARATION"|	
|Legal|Organization|*As above*|"IDENTITY_PROOF"<br>"ARTICLES_OF_ASSOCIATION"<br>"REGISTRATION_PROOF"|
|Legal|Soletrader|*As above*|"IDENTITY_PROOF"<br>"REGISTRATION_PROOF"|

*Note that you can change the `LegalPersonType` once it has been set (although if the user doesn't have the required KYC documents for the new value listed in the table above, their KYC level will be downgradedt)*

[alert type="info"]Note: In some exceptional cases, our Legal team will ask for extra documents if they suspect the user of illegal activities or political exposure.[/alert]


## KYC documents

Here are the required documents for regular verification.
Please find below the details for each required document. 

|Document type|Usage|
| -------- | -------- |
|"IDENTITY_PROOF"| ID Card, Passport or driving license for SEPA area. Passport or driving licence for the UK, USA and Canada. For other nationalities a passport is required.<br>In the case of a legal user, this document should refer to the individual duly empowered to act on behalf of the legal entity.  ID card: Front AND Back (Valid) OR Passport (Valid)|
|"ARTICLES_OF_ASSOCIATION"|Certified articles of association (Statute) - formal memorandum stated by the entrepreneurs, in which the following information is mentioned: business name, activity, registered address, shareholding…|
|"REGISTRATION_PROOF"|Extract from the Company Register issued within the last three months<br>In the case of an organization or soletrader, this can be a proof of registration from the official authority|
|"SHAREHOLDER_DECLARATION"|Send information referring to the [shareholder declaration](https://www.mangopay.com/terms/shareholder-declaration/Shareholder_Declaration-EN.pdf)|
|"ADDRESS_PROOF"|Proof of address. Confirmation of residence: Less than a year old. Can be: Residential Registration Form, Water/electricity/gas/telephone bill, Tax certificate, Householder insurance, Confirmation of real estate ownership|

These documents can be refused for various reasons - see details at the end of the [Errors page](/guide/errors).
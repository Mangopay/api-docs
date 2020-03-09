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

[alert type="info"]Please note that we recently changed the required information to do the regular validation of a `Legal User` type business. We now ask you to declare the `CompanyNumber` and to post an `UBOs declaration` instead of the manual shareholder declaration.    [/alert]

Allows for unlimited cash-in or cash-out (per user, per year)

In addition to the information provided for “light” verification, the following is the information** you are required** to collect from your users to allow them to go over the default [limit](https://docs.mangopay.com/guide/kyc-1). Users will need to provide at least one document proving their identity.

|Person type|LegalPersonType|Required infos|Required KYC documents|
| -------- | -------- | -------- | -------- |
|Natural|n/a|	n/a |ID Card or Passport <sup>(1)</sup> or driving licence for UK, USA and Canada (a passport is required outside of EU area) - "IDENTITY_PROOF"|
|Legal|Business| `HeadquartersAddress`<br> `LegalRepresentativeEmail`<br> `LegalRepresentativeAddress`<br> [`CompanyNumber`](https://docs.mangopay.com/guide/company-number) <br> [`UBO declaration`](https://docs.mangopay.com/endpoints/v2.01/ubo-declarations#e1024_the-ubo-declaration-object) |"IDENTITY_PROOF"<br>"ARTICLES_OF_ASSOCIATION"<br>"REGISTRATION_PROOF"|	
|Legal|Organization|`HeadquartersAddress`<br> `LegalRepresentativeEmail`<br> `LegalRepresentativeAddress`|"IDENTITY_PROOF"<br>"ARTICLES_OF_ASSOCIATION"<br>"REGISTRATION_PROOF"|
|Legal|Soletrader|`HeadquartersAddress`<br> `LegalRepresentativeEmail`<br> `LegalRepresentativeAddress`|"IDENTITY_PROOF"<br>"REGISTRATION_PROOF"|

*Note that you can change the `LegalPersonType` once it has been set (although if the user doesn't have the required KYC documents for the new value listed in the table above, their KYC level will be downgraded)*

[alert type="info"]Note: In some exceptional cases, our Legal team will ask for extra documents if they suspect the user of illegal activities or political exposure. Also when the UBO declared with this functionality can not be matched with an official paper (Article of association registration proof), we will be required to request extra documents (such as the shareholder delcaration) to validate the KYC of this user. This is part of our contractual relationship ( article 4.2).[/alert]


## KYC documents

KYC documents must be submitted in one of the following languages: [French](https://support.mangopay.com/s/article/French-users-what-documents-can-be-submitted?language=en_US), [English](https://support.mangopay.com/s/article/users-from-the-uk-what-documents-can-be-submitted?language=en_US), [German](https://support.mangopay.com/s/article/German-user-which-documents-should-be-submitted), [Dutch](https://support.mangopay.com/s/article/dutch-user-what-documents-can-be-submitted?language=en_US), [Spanish](https://support.mangopay.com/s/article/Spanish-user-which-verification-documents-should-be-submitted), [Italian](https://support.mangopay.com/s/article/Italian-user-which-verification-documents-should-be-submitted), and [Portuguese](https://support.mangopay.com/s/article/portugese-users-what-documents-can-be-submitted?language=en_US).
If a document is not available in one of the above languages, an official translation in French or English will be required. The Legal team may ask for the official translation of a document if deemed necessary.

Please find below the details for each required document. 

|Document type|Usage|
| -------- | -------- |
|"IDENTITY_PROOF"| ID Card, Passport, Residence Permit, or Driving License for EU area. Passport or Driving Licence for the UK, USA and Canada. For other nationalities, a passport is required.<br>In the case of a legal user, this document should refer to the individual duly empowered to act on behalf of the legal entity.  ID card: Front AND Back (Valid) OR Passport (Valid)|
|"ARTICLES_OF_ASSOCIATION"|Certified articles of association (Statute) - formal memorandum stated by the entrepreneurs, in which the following information is mentioned: business name, activity, registered address, shareholding…|
|"REGISTRATION_PROOF"|Extract from the Company Register issued within the last three months<br>In the case of an organization or soletrader, this can be a proof of registration from the official authority|
|"ADDRESS_PROOF"|Proof of address. Confirmation of residence: Less than a year old. Can be: Residential Registration Form, Water/electricity/gas/telephone bill, Tax certificate, Householder insurance, Confirmation of real estate ownership|

These documents can be refused for various reasons - see details at the end of the [Errors page](/guide/errors).
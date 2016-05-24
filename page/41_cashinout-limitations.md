[KYC means « Know Your Customer »](https://en.wikipedia.org/wiki/Know_your_customer). These legal obligations are related to our license as an electronic money issuer and are neccessary in order to fight fraud, money laundering and financing of terrorism. There are 3 levels of authentication (light/regular/strong) **managed through the API** by the MANGOPAY compliance team once you sent them. This validation will let your users access a higher level (light to regular or regular to strong):

* **Light Authentication**: Transactions worth less than €2,500 for **cash-in** and/or €1,000 for **cash-out** cumulated **per legal year and per user** (transfers are also counted in this equation).
* **Regular Authentication**: Transactions worth more than €2,500 for **cash-in** and/or €1,000 for **cash-out** cumulated **per legal year and per user**.
* **Strong Authentication**: Clients suspected of money laundering and/or terrorism and/or politically exposed persons

# Light Authentification
[alert type="info"]
Up to 2500€ for cash-in per user

Up to 1000€ for cash-out per user
[/alert]

This is the basic information you are **required** to collect from your users in order to process payments (Cash-in / Cash-out). We cannot allow any transactions from a user who has not provided the following information:


**For a customer (NATURAL_PERSON):**

* Email
* FirstName
* LastName
* Country of Residence
* Birthday
* Nationality


**For a business or organization (LEGAL_PERSON):**

* Legal Person Type (‘BUSINESS’ or ’ORGANIZATION’)
* Business Name
* Generic business email
* FirstName of the legal representative
* LastName of the legal representative
* Birthday of the legal representative
* Nationality of the legal representative
* Country of residence of the legal representative


# Regular Authentification
[alert type="info"]
For unlimited cash-in per user

For unlimited cash-out per user
[/alert]

This is the information **you are required** to collect from your users to go over the Cash-in (€2,500)  and/or Cash-out (€1,000) limits:


**For a customer (NATURAL_PERSON):**

In addition to the Light Authentication fields:

* Address (declarative field)
* ID Card or Passport (1) (Proof Of Identity) or driving licence for UK, USA and Canada
* Passport required out of the SEPA area
* Occupation (2) (declarative field)
* Income Range (2) (declarative field)


**For a business company (LEGAL_PERSON):**

In addition to the Light Authentication fields:

* Headquarter address (declarative field)
* Legal Representative email
* Legal Representative Address
* Certified articles of association (Statute) : formal memorandum stated by the entrepreneurs, in which the following information is mentioned:business name, activity, registered address, shareholding…
* Proof of registration: Extract from the Company Register issued within the last three months (4)
* Send the [Shareholder declaration](https://docs.mangopay.com/files/2013/08/Shareholder-declaration.pdf)
* The ID or the passport of the individual duly empowered to act on behalf of the legal entity or driving licence for UK, USA and Canada
* Passport required out of the SEPA area


**For an organization (LEGAL_PERSON):**

In addition to the Light Authentication fields:

* Headquarter address (declarative field)
* Legal Representative email
* Legal Representative Address
* The ID or the passport of the individual duly empowered to act on behalf of the legal entity or driving licence for UK, USA and Canada
* Passport required out of the SEPA area
* Certified articles of association (Statute)
* Proof of registration from the official authority

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


# Strong Authentification
[alert type="info"]
Client suspected of money laundering and/or terrorism and/or politically exposed persons
[/alert]

This is the information **required** for users suspected of fraud, money laundering, terrorism, politically exposed people:


**For a customer (NATURAL_PERSON):**

To be added to Light & Regular Authentication fields:

* Confirmation of residence (3) (Proof Of Address)


**For a business or organization (LEGAL_PERSON):**

To be added to Light & Regular Authentication fields:

* Confirmation of bank details

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


# Modus Operandi

1.  The [Object Documents](http://demo.dev-app.net/endpoints/v2#e204_the-kyc-document-object) is a request to validate a required document. There is 1 request for 1 « type » of document
2.  Upload a file through the [Object Page](http://demo.dev-app.net/endpoints/v2#e208_create-a-kyc-page). A document should get several pages
3.  Edit the object Document and set the « Status » field to « VALIDATION_ASKED » (instead of « CREATED »)
4.  The demand is received by our team. The object is waiting for a « VALIDATED » status
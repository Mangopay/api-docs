The `KYC Document Object` is a container to store document pages in it. There is one KYC Document Object for one `Type` of document

The process to send a KYC document is divided into 3 parts.

• **Step 1 **: [Creation of a KYC Document](https://docs.mangopay.com/endpoints/v2.01/kyc-documents#e205_create-a-kyc-document)

• **Step 2**:  [Creation of KYC Pages within the document](https://docs.mangopay.com/endpoints/v2.01/kyc-documents#e208_create-a-kyc-page). A document can have several pages. 

• **Step 3**:  [Submission of the KYC Document](https://docs.mangopay.com/endpoints/v2.01/kyc-documents#e206_submit-a-kyc-document). You will have to edit the object Document and set the Status field to "VALIDATION_ASKED" (instead of "CREATED")


The documents will be validated by our compliance team.

[alert type="danger"]Note that you are not allowed to store KYC documents on your side unless you have permission from the approriate authorities in your country[/alert]
You need to create document in order to upload pages on this document.

1.  The `KYC Document Object` is a request to validate a required document. There is 1 request for 1 « type » of document
2.  Upload a file through the [Object Page](http://demo.dev-app.net/endpoints/v2#e208_create-a-kyc-page). A document should get several pages
3.  Edit the object Document and set the « Status » field to « VALIDATION_ASKED » (instead of « CREATED »)
4.  The demand is received by our team. The object is waiting for a « VALIDATED » status
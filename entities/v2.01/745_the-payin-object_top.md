The table below describes the different **PayIn methods available** with the MANGOPAY API, and which capabilities are available for each. Note that for certain card payments, there may be an extra step for [3D-Secure](https://mangopay.desk.com/customer/en/portal/articles/2572098-all-you-need-to-know-about-3d-secure-integration-workflow-etc-?b_id=10427) to be completed - you can read more about the triggers for this step [here](https://mangopay.desk.com/customer/en/portal/articles/2506712-what-is-the-trigger-for-3ds-is-it-possible-to-modify-it-?b_id=10427).

[alert type="info"]The appropriate test cards/data can be found [here](/guide/testing-payments).[/alert]

|  | PayIn Web | PayIn Direct | 3DSecure | Refund | Currency | Payment Type |
| -------- | -------- | -------- | -------- | -------- | -------- | -------- |
| CB/Visa/Mastercard  ![alt](/uploads/medias/cb-visa-mastercard.png)     | Yes |	Yes	| Yes | Yes | All |	Card |
| Maestro ![alt](/uploads/medias/103_0_574_Maestro21.png) | Yes | Yes | Always 3DS | Yes | EUR | Card |
| Diners ![alt](/uploads/medias/diners.png) | Yes | Yes | No | Yes | EUR | Card |
| Przelewy24 ![alt](/uploads/medias/p24-small.png) | Yes | No | No | Yes | PLN | Card |
| iDeal ![alt](/uploads/medias/IDEAL_Logo.png) | Yes | No | No | Yes | EUR | Card |
| Bancontact/Mister Cash ![alt](/uploads/medias/bancontact.png) | Yes | Yes | Always 3DS | Yes | EUR | Card |
| PayLib ![alt](/uploads/medias/paylib.jpg) | Yes | No | No | Yes | EUR | Card |
| Sofort ![alt](/uploads/medias/klarna.png) | Yes | No | No | Yes | EUR | Direct Debit |
| Giropay ![alt](/uploads/medias/giropay.jpg) | Yes | No | No | Yes | EUR | Direct Debit |
| Direct Debit ![alt](/uploads/medias/bank.png) | No | Yes | No | Yes | EUR/GBP | Direct Debit |
| Bankwire ![alt](/uploads/medias/bank.png) | No | Yes | No | No | All | Bankwire |
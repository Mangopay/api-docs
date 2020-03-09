You need to register a card in order to process a [entity_link entity="278"]Direct PayIn[/entity_link]. **Card registration enables you to tokenize a Card**. These are the steps to follow:

1. Create a `CardRegistration` Object *(1. 2. & 3. in the diagram)*
2. Get the `PreRegistrationData` , `CardRegistrationURL` and  `AccessKey`  *(4. in the diagram)*
3. The user posts `PreRegistrationData`, `AccessKey` and `card details` through a form to the `CardRegistrationURL` *(5. in the diagram)*
4. Get a `RegistrationData` back *(6. in the diagram)*
5. Edit the `CardRegistration` Object  with the `RegistrationData` just received *(7.8. in the diagram)*
6. Get the `CardId` ready to use into the **[entity_link entity="278"]Direct PayIn[/entity_link]** Object *(9. in the diagram)*

[alert type="info"]  You need to do your tests in sandbox mode only with the [testing cards](/guide/testing-payments) [/alert]

[alert type="info"]  If you don’t want to save the card you must change the field ACTIVE in the card object to false as shown [entity_link entity="182"]here[/entity_link] [/alert]

[alert type="danger"]**IMPORTANT**: card details must never pass via your server – therefore you must use the card registration process given below and not implement a different system where the card details may touch your server – (this approach or anything similar) is strictly not allowed[/alert]

**Registration Flow**

Here is the registration flow (the last step correponds to the [entity_link entity="278"]Direct PayIn[/entity_link]):
![alt](/uploads/medias/SchemeCardRegistration.png)

[alert type="info"]
* It is imperative to inform your users if you are registering their cards
* The validity of a registered card (CardId) before a payment or a pre-authorisation is 30min maximum. Once one of these operations is made, the card `Validity` field change to "VALID". Then, it is available up to the expiry date
[/alert]
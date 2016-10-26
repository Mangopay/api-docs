# Customize web templates

PayIns via Web interface allow you to provide a property called `TemplateURLOptions` to customize your payment pages for credit cards, Sofort and ELV. Giropay does not allow to iFramed its payment page. So you cannot use this Template method with Giropay.

## Rules
You will need to create your own skeleton (page markup) by positioning a zone to be completed by the PSP form via the API when creating a payment page. If your template isn’t displayed, it could be for these reasons:

* The dynamic skeleton will need to be **hosted on your website**
* Your **SSL certificate** has to be "real" (**not auto-signed**) and can not be a "Let's Encrypt" type certificate either
* Your **SSL certificate** has to contain at least the fields CN, O, OU and C (**level 2**). we recommend GeoTrust.com
* **All the certificates** of the SSL certification chain have to be shown/sent by your server (root & intermediate certificate) which blocks the ssl handshake
* Your certificate **common name** has to match your **host name** exactly
* Be careful not to use **SNI** (http://en.wikipedia.org/wiki/Server_Name_Indication) on your URL
* Your template **URL has to be absolute** and in **HTTPS** (port 443) (into the property `TemplateURL`)
* All resources/calls have to be submitted as **absolute URLs**
* The URL must **accept POST request**
* The URL must **not to be protected** by a password (htaccess, etc.)
* Your server must be compatible with Java v1.6
* These rules apply to Sandbox and Production environments
* Your domain and SSL certificate **must get a "A" level** [here](https://www.ssllabs.com/ssltest/)

[alert type="info"]You must include the "Powered by MANGOPAY" banner on your payment page - you can download it [here](https://www.mangopay.com/terms/powered-by-mangopay.png)[/alert]

## Payline template implementation
This skeleton can be called for all payments, but it can also be generated dynamically, according to the data which is relevant for each transaction. In this case, the URL could look like this:

> https://url_squelette_dynamique?orderRef=XXXXX&orderAmount=YYYYY&orderCurrency=ZZZ&step=2

The URL will be submitted by initiliasing the parameter **`TemplateURL`**».

### Contextual Parameters
The following parameters are submitted to the merchant while reaching out to the dynamic templates:

> step: The process that is currently being undertaken may have one of the following values:
* 1: entering payment information
* 2: error

### Payline Form
The dynamic skeleton enables a merchant to create their own payment pages. The only condition is that the skeleton contains an HTML code which indicates where Payline should dynamically include its payment form via the API.

A very basic skeleton may look like this:

```
<html>

   <body>

      <div id="PaylineForm"></div>

   </body>

</html>
```

### Stylesheets
The HTML code added by Payline via the API is in compliance with HTML v4.01.
You can personalise the appearance of the Payline form that will be added to the payment pages by using a Stylesheet. In order to personalise this form, simply  add your CSS. Here is an example:
```
<style type= “text/css“>

< !--

#PaylineForm {
    font-family:Tahoma, sans-serif;
    font-size: 76%;
    margin:0 auto;
    width:750px;
}

#PaylineForm h2 {
    margin: 0;
    padding:0;
    font-size: 1em;
    line-height:1.5em;
    color:orange;
}

#PaylineForm h3 {
    margin: 0;
    margin-bottom:.5em;
    font-size: 1em;
    font-weight: bold;
    color:#333;
}

#PaylineForm input[type=radio],
#PaylineForm label,
#PaylineForm label img,
.checkable * {
    vertical-align:middle;
}

#PaylineForm form {
    margin:0;
}

/* Panel contenant les champs */

#PaylineForm .pane {
    padding:.5em;
    margin-bottom:.5em;
    background-color: #efefef;
    border: 1px solid orange;
}

#PaylineForm div.radio {
    margin-bottom:.5em;
}

/* Bouton de validation*/

#PaylineForm #submitButton {
    background-color:orange;
    color:white;
    font-weight: bold;
}

/* Bouton d'annulation */

#PaylineForm #cancelButton {
    background-color:orange;
    color:white;
}

/* Message de feed-back de paiement */

.paymentmessage {
    text-align:center;
    background: #fefefe;
    line-height: 3em;
}

/* Zone contenant le bouton */

#actionButtons {
    text-align: center;
}

/* Messages d'erreur */

#PaylineForm ul.errors,
#PaylineForm ul.errors li {
    margin:0;
    padding:0;
    list-style: none;
}

#PaylineForm ul.errors {
    padding:.5em
    margin-bottom:1em;
    color:red;
    background-color: #ffe;
    border:1px solid #ccc;
}

/* Champs désactivés */

.disabled {
    background-color: #fafafa;
}

-->

</style>
```

### Details of the various forms
When using these instructions (CSS), the following HTML elements apply:

#### Page for choosing the means of payment

| Element | Description |
| -------- | -------- |
| #PaylineForm | Layout of the form (font, size etc.)  |
| #PaylineForm h2 | Title of the form (i.e. "Means of Payment") |
| #PaylineForm .pane | Form |
| #PaylineForm h3 | Title of the form section (i.e. pay with existing card) |
| #PaylineForm #submitButton | Confirmation button (i.e. "Confirm") |

#### Choosing the means of payment while using an e-wallet

#### Form for gathering payment data

| Element | Description |
| -------- | -------- |
| #PaylineForm | Layout of the form (font, size etc.)  |
| #PaylineForm h2 | Title of the form (i.e. "Means of Payment") |
| #PaylineForm .pane | Form |
| #PaylineForm h3 | Title of the form section (i.e. pay with existing card) |
| #PaylineForm #cancelButton | Cancellation button (i.e. "Return") |
| #PaylineForm #submitButton | Confirmation button (i.e. "Confirm") |
| #PaylineForm table.form th | Form: Header cell (i.e. "Credit card type") |
| #PaylineForm table.form th label | Form: Labelling of the form (i.e. "Credit card number") |
| #PaylineForm table.form td | Form: Cell of the form |
| #PaylineForm table.form tr#cardNumber td input | Form: Cell (i.e. "Credit card number") |
| #PaylineForm table.form tr#cardNumber td a | Form: Link (i.e. "Further information") |
| #PaylineForm ul.errors li | Error message |
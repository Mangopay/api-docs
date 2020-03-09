# Customize web templates

PayIns via Web interface allow you to provide a property called `TemplateURLOptions` to customize your payment pages for credit cards and Sofort. Giropay does not allow to iFramed its payment page. So you cannot use this Template method with Giropay.

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
* Your domain and SSL certificate should get **an "A" level** [here](https://www.ssllabs.com/ssltest/)

[alert type="info"]You must include the "Powered by MANGOPAY" banner on your payment page - you can download it [here](https://www.mangopay.com/terms/powered-by-mangopay.png)[/alert]



## Payline template implementation
This skeleton can be called for all payments, but it can also be generated dynamically, according to the data which is relevant for each transaction. In this case, the URL could look like this:

> https://mysite.com?orderRef=XXXXX&orderAmount=YYYYY&orderCurrency=ZZZ&step=2&token=azertyrezaertyrez&transactionid=12345657

The URL will be submitted by initialiasing the parameter **`TemplateURL`**.

### Payline Form
The dynamic skeleton enables a merchant to create their own payment pages. The only condition is that the skeleton contains an HTML code which indicates where Payline should dynamically include its payment form via the API.

A very basic skeleton may look like this:

```
<html>
   <body>
      <div id="PaylineWidget" data-token=""></div>
   </body>
</html>
```

`data-token` attribute should contain the payment token. 

You can use the code sample bellow to fill this attribute automaticaly using javascript.

```
<script type="text/javascript">
// Pour charger le widget
var urlToken = url_query('token');
if (urlToken) {
    var element = document.getElementById('PaylineWidget');
    element.setAttribute('data-token', urlToken);
}

// Parse URL Queries
function url_query( query ) {
	query = query.replace(/[\[]/,"\\\[").replace(/[\]]/,"\\\]");
	var expr = "[\\?&]"+query+"=([^&#]*)";
	var regex = new RegExp( expr );
	var results = regex.exec( window.location.href );
	if ( results !== null ) {
    	return results[1];
	} else {
    	return false;
	}
}
</script>

<script type="text/javascript">
// Pour charger le widget
var urlToken = url_query('token');
if (urlToken) {
    var element = document.getElementById('PaylineWidget');
    element.setAttribute('data-token', urlToken);
}

// Parse URL Queries
function url_query( query ) {
	query = query.replace(/[\[]/,"\\\[").replace(/[\]]/,"\\\]");
	var expr = "[\\?&]"+query+"=([^&#]*)";
	var regex = new RegExp( expr );
	var results = regex.exec( window.location.href );
	if ( results !== null ) {
    	return results[1];
	} else {
    	return false;
	}
}
</script>
``` 

[alert type="info"]
`transactionid` are also available from the redirected URL. You can directly use this information in others endpoints.
[/alert]

### Add references 
Last step : you should link the above html payment form to the Payline widget :

Sandbox environment :
```
<script src="https://homologation-payment.payline.com/scripts/widget-min.js"> </script>
<link href="https://homologation-payment.payline.com/styles/widget-min.css" rel="stylesheet" />
```
 
Production environment :
```
<script src="https://payment.payline.com/scripts/widget-min.js"> </script>
<link href="https://payment.payline.com/styles/widget-min.css" rel="stylesheet"/>
```

 
[alert type="info"]
We suggest you to add theses scripts tags at the end of your page, in the footer for example. In order to not slow down the rest of your page during the javascript loading time.
[/alert]


## Optionnals steps
### Cancel a transaction button
To add the "Cancel" button and allow users to cancel the payment, add two functions to your javascript

ExecuteCancelAction function :
```
function executeCancelAction() {
                var cancelUrl = Payline.Models.Contexts.ContextManager.getCurrentContext().getCancelUrl();

                //Execution du endToken
                Payline.Api.endToken(null, function () {
                    //Redirection
                    window.location.href = cancelUrl;
                }, null, false);
            }
```

Onload function : 
```
function OnLoad() {

                Payline.jQuery('.pl-pmContainer .pl-pay-btn-container').after('<a class="cancelButton" style="display:block;cursor:pointer" title="Annuler le paiement">Annuler</a>');
                Payline.jQuery('.cancelButton').click(executeCancelAction);
            }
```

In the html page you should also add a new parameters `data-event-didshowstate="OnLoad"` in the widget div.

Exemple : 
```
<div id="PaylineWidget" data-token="1eECHHVWYqzRU1E9b3751578319991770" data-template="column" data-event-didshowstate="OnLoad" data-embeddedredirectionallowed="false"></div>
```


## Stylesheets
The HTML code added by Payline via the API is compliant with HTML v5.
You can personalise the appearance of the Payline form that will be added to the payment pages by using a Stylesheet. 
You can completly personalise the form style by surcharging the default stylesheet. Possibilities are unlimited. 

Here is some examples : 

| Description | Parameters |
| -------- | -------- |
| Brand header color | #PaylineWidget .pl-header-title-wrapper { background-color: #ABCDEF; } |
| Brand text color | #PaylineWidget .pl-header-title-content h4 { color: #ABCDEF; } |
| Amount to pay text color | #PaylineWidget .pl-header-title-content p { color: #ABCDEF; } |
| Payment button color | #PaylineWidget .pl-pay-btn { background-color: #ABCDEF; } #PaylineWidget .pl-pay-btn:hover { background-color: #ABCDEF; } |
| Form background color | #PaylineWidget .pl-body { background-color: #ABCDEF; } |
| Payment area color | #PaylineWidget .pl-pmContainer {background-color: #ABCDEF; border-color: #ABCDEF; } |
| Close the lightbox color button | #PaylineWidget .pl-icon-close { color: #ABCDEF; } |
| Window width/ height are optimised in the following configuration : max width : 900px, min width : 500px | .PaylineWidget.pl-container-default .pl-pmContainer .pl-label-input  { display: none;} .PaylineWidget.pl-container-default .pl-pmContainer .pl-input-group-container { margin-left: 0; } |
| Payline proposes to reduce the margins in order to adjust the window above 900px wide, for this you just have to decrease the width of the label (xx%), and to decrease the margin on the left of the fields (xx% by default 30% ). | .PaylineWidget.pl-container-default .pl-pmContainer .pl-label-input { width: xx%; } .PaylineWidget.pl-container-default .pl-pmContainer .pl-input-group-container .PaylineWidget.pl-container default .pl-form-container label.pl-remember-container { margin-lef: yy%; } |


### Details of the various forms
When using these instructions (CSS), the following HTML elements apply:

#### Page for choosing the means of payment

| Element | Description |
| -------- | -------- |
| #PaylineWidget | Layout of the form (font, size etc.)  |
| #PaylineWidget h2 | Title of the form (i.e. "Means of Payment") |
| #PaylineWidget .pane | Form |
| #PaylineWidget h3 | Title of the form section (i.e. pay with existing card) |
| #PaylineWidget #submitButton | Confirmation button (i.e. "Confirm") |

#### Choosing the means of payment while using an e-wallet

#### Form for gathering payment data

| Element | Description |
| -------- | -------- |
| #PaylineWidget | Layout of the form (font, size etc.)  |
| #PaylineWidget h2 | Title of the form (i.e. "Means of Payment") |
| #PaylineWidget .pane | Form |
| #PaylineWidget h3 | Title of the form section (i.e. pay with existing card) |
| #PaylineWidget #cancelButton | Cancellation button (i.e. "Return") |
| #PaylineWidget #submitButton | Confirmation button (i.e. "Confirm") |
| #PaylineWidget table.form th | Form: Header cell (i.e. "Credit card type") |
| #PaylineWidget table.form th label | Form: Labelling of the form (i.e. "Credit card number") |
| #PaylineWidget table.form td | Form: Cell of the form |
| #PaylineWidget table.form tr#cardNumber td input | Form: Cell (i.e. "Credit card number") |
| #PaylineWidget table.form tr#cardNumber td a | Form: Link (i.e. "Further information") |
| #PaylineWidget ul.errors li | Error message |
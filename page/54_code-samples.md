# Code samples
On this site, you'll see the option to get a code sample for each method (in the right hand column under "Code").

### PHP
For the PHP samples, they use the latest SDK and you'll need to include the following code before each sample (in the examples, this is referred to as `mangopay.php`):
```
require_once("../mangopay2-php-sdk/vendor/autoload.php");
$MangopayApi = new \MangoPay\MangoPayApi();
$MangopayApi->Config->ClientId = "Your-ClientId"; //#TODO Update with your own info
$MangopayApi->Config->ClientPassword = "Your-Passphrase"; //#TODO Update with your own info
$MangopayApi->Config->TemporaryFolder = "/a/path/to/a/writeable/folder/"; //#TODO The SDK will store it's oauth token here in a file
//$MangopayApi->Config->BaseUrl = "https://api.mangopay.com"; //uncomment this line to use the production environment

//Uncomment any of the following to use a custom value (these are all entirely optional)
//$MangopayApi->Config->CurlResponseTimeout = 20; //The cURL response timeout in seconds (its 30 by default)
//$MangopayApi->Config->CurlConnectionTimeout = 60; //The cURL connection timeout in seconds (its 80 by default)
//$MangopayApi->Config->CertificatesFilePath = ''; //Absolute path to file holding one or more certificates to verify the peer with (if empty, there won't be any verification of the peer's certificate)

```
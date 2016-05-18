**iOS INTEGRATION**
Check out the demo app:

**INSERT IMAGE XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX AND LINK**

Scanpay also provide a [textGithub demo](https://github.com/scanpay/scanpay-demo-ios)

**Requirements for card scanning**
* iOS version 5.0 or higher
* iPad / iPhone 4 or higher

**To add ScanPay to your iOS app, follow these steps:**

* Drag and drop the folder ScanPay to your project
* Add the following frameworks to your project:
** AssetsLibrary.framework
** AudioToolbox.framework
** AVFoundation.framework
** CoreMedia.framework
** CoreVideo.framework
** libsqlite3.0.dylib
** libstdc++.dylib
** QuartzCore.framework
** Security.framework
* Go to Target -> Other Linker Flags and add the following flag: -ObjC
* Go to Project Settings Build Settings search for C++ Standard Library and change to libstdc++
* Create a class conform to ScanPayDelegate protocol
* To start the scan simply present the scanViewController from a UIViewController :
```
#import "ScanPayViewController.h"
ScanPayViewController *scan = [[ScanPayViewController alloc]initWithDelegate:self appToken:@"PUT_YOUR_TOKEN_HERE"
];
[self presentViewController:scan animated:YES completion:nil];
[scan release];
```
* You will be notified of  user interaction through the delegate method:
```
- (void)scanPayViewController:(ScanPayViewController *)scanPayViewController didScanCard:(SPCreditCard *)card
{
}
- (void)scanCancelledByUser:(ScanPayViewController *)scanPayViewController
{
}
- (void)scanPayViewController:(ScanPayViewController *)scanPayViewController failedToScanWithError:(NSError *)error
{
}
```
* If you want to use your own confirmation view simply implement:
```
- (BOOL)scanPayViewControllerShouldShowConfirmationView:(ScanPayViewController *)scanPayViewController
{
return NO:
}
```
* If you want to hide the manual button:
```
- (BOOL)scanPayViewControllerShouldShowManualEntryButton:(ScanPayViewController *)scanPayViewController
{
return NO:
}
```
* If you have an old version of Scanpay, add **libc++.dylib** library in Build Phase , in Project Settings Build Settings search for C++ Standard Library and add **libstdc++** and delete **opencv2.framework** and the **ScanpayRessource.bundle** is no longer required.

**ANDROID INTEGRATION**
Check out the demo app:

**INSERT IMAGE XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX AND LINK**

Scanpay also provide a[text Github demo](https://github.com/scanpay/scanpay-demo-android)

**Requirements for card scanning**
* Android version 2.2 or higher
* Processor Armv7

**To add ScanPay to your Android app, follow these steps:**
* Copy the content of ScanPay libs folder into your project libs folder
* Right click on your project name and click properties
* Go to Java build path section and open Libraries tab
* Click add jar and select LibScanpay.jar in your libs folder
* Go to Order and Export tab and check the libScanpay.jar box
* Add these permissions to your AndroidManifest.xml:
```
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.VIBRATE" />
<uses-feature android:name="android.hardware.camera" android:required="false" />
<uses-feature android:name="android.hardware.camera.autofocus" android:required="false" />
<uses-feature android:name="android.hardware.camera.flash" android:required="false" />
```
* Declare the activity used by ScanPay in your AndroidManifest.xml:
```
<!-- ScanPay Activities -->
<
activity
android:name="scanpay.it.ScanPayActivity"
android:configChanges="orientation|keyboardHidden"
android:screenOrientation="portrait"
android:theme="@android:style/Theme.Black.NoTitleBar" >
</activity>
<activity
android:name="scanpay.it.ValidationActivity"
android:screenOrientation="portrait"
android:theme="@android:style/Theme.Black.NoTitleBar"
android:windowSoftInputMode="stateHidden" >
</activity>
```
* Before you build in a release mode, make sure to adjust your proguard configuration by adding the following to proguard.cnf:
```
-keep class scanpay.it.**
-keepclassmembers class scanpay.it.** {
*;
}
```
* Start scanning using:
```
Intent scanActivity = new Intent(this, ScanPayActivity. class);
scanActivity.putExtra(ScanPay.EXTRA_TOKEN, "PUT_YOUR_TOKEN_HERE");
//Put true if you want use your own manual entry UI
scanActivity.putExtra(ScanPay.EXTRA_SHOULD_SHOW_CONFIRMATION_VIEW, false);
// You can hide button like that
scanActivity.putExtra(ScanPay.EXTRA_SHOULD_SHOW_MANUAL_ENTRY_BUTTON, false);
startActivityForResult(scanActivity, YOUR_RESULT_DEFINE);
```
* To get the scan result, you must implement onActivityResult as follows:
```
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data)
{
super.onActivityResult(requestCode, resultCode, data);
if (requestCode == RESULT_SCANPAY_ACTIVITY && resultCode == ScanPay.RESULT_SCAN_SUCCESS)
{
CreditCard creditCard = (CreditCard) data.getParcelableExtra(ScanPay.EXTRA_CREDIT_CARD);
Toast.makeText(this, creditCard.number + " " + creditCard.month + "/" + creditCard.year + " " + creditCard.cvv, Toast.LENGTH_LONG).show();
}
else if (requestCode == RESULT_SCANPAY_ACTIVITY && resultCode == ScanPay.RESULT_SCAN_CANCEL)
{
Toast.makeText(this, "Scan cancel", Toast.LENGTH_LONG).show();
}
}
```
* If you have a version of Scanpay prior to 2.0, the assets folder is no longer required
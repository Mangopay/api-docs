Once setup, hook notifications allow us to make a request to a specific URL on your server to make you aware of various Events (such as a failed PayOut). You can set up one URL for each `EventType`. Here are the rules:
* After 100 failed notifications for an `EventType` (we couldn’t reach your URL), the hook will be automatically set to `Validity`="INVALID" and `Status`= "DISABLED".
* Every 10 failed notifications you will receive an email warning you of the issue.
* Each time you have a successful notification, we reset this counter (so if you have 99 failures, then 1 successful and then 1 failure, this won’t result in the 100 failed email alert)
* Changing the URL for a hook will not reset your failure count though
* The URL that we hook **must respond with a 200 status code within 2 seconds** – otherwise we will consider the hook a failure
* You are **strongly advised** to do a GET on the resource to check its Status (to ensure the Event is still relevant, but also to ensure the hook is authentic)
* You can also view and manage your Hook notifications from the new MANGOPAY Dashboard.

Notification format: http://www.your-site.com?EventType=`EventId`&RessourceId=`ResourceId`&Date=`Timestamp`

Example :
If you want to create a notification for the event type "KYC_SUCCEEDED" on your URL: "http://www.mynotificationurl.com" you will recieve this ping: http://www.mynotificationurl.com?EventType=KYC_SUCCEEDED&RessourceId=1309853&Date=1397037093

A useful cloud tool for testing notifications in sandbox is requestb.in.
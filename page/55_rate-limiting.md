# API Rate limiting
[alert type="info"]Note that rate limiting will be in effect from 1st August, therefore the information on this page is only relevant after this date[/alert]

The API uses rate limiting to ensure the stability and reliablity for all clients, in both the production and sandbox environments. All endpoints are affected and you have a maximum amount of calls allowed in a given period:

|Time period|API calls allowed|
| -------- | -------- |
|15mins|2300|
|30mins|4500
|1hr|8800|

If you go over any of these rate limits (by doing too many API calls), you will receive the response code 429 with the response body:
```
{
  "Message": "Rate limit exceeded. Please contact support for more assistance",
  "Type": "rate_limit",
  "Id": *,
  "Date": *,
  "errors": null
}
```

[alert type="info"]If you are frequently being affected by this error, please contact our support team to ensure your integration is approriate or to increase your limits[/alert]

For any API call, you’ll see some useful information in the response headers specifying:
* how many calls you’re allowed (`X-RateLimit-Limit`)
* how many you have left (`X-RateLimit-Remaining`)
* the time until these will be reset (`X-RateLimit-Reset`)
In each case, several values will be given, separated by a  comma - these correspond to each rate limit bucket (there are currently three - see the table above).

With normal usage of the API, you should not be affected by these rate limits. However if you plan to launch many API requests together (to do some batch payouts/transfers for example), it is very important to take into account these header infos, and adapt your scripts accordingly - for example, if you do not have many calls left for a bucket, you should either stop and start again after the `X-RateLimit-Reset` time, or start adding increasing pauses in-between your calls, to ensure you don’t go over a limit.

The API rate limiting operates using a "[leaky bucket](http://en.wikipedia.org/wiki/Leaky_bucket)" algorithm as a controller. This allows for infrequent bursts of calls, and allows your app to continue to make an unlimited amount of calls over time. The bucket allowance is sliding per time window, as opposed to being reset a specific intervals in the hour. For example, with a bucket of 15 minutes, if you do 10 calls, you need to wait just 15 minutes to liberate those 10 calls from your allowance (as opposed to waiting till 15 minutes past the hour).
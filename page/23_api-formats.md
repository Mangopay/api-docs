# FORMATS USED IN THE MANGOPAY API
**Dates**
All date and time values are displayed as integer numbers and represent the number of seconds since the Unix Epoch (January 1 1970 00:00:00 GMT), like [PHP time()](http://php.net/manual/en/function.time.php) function. The date/time property type in the specification is specified as “Time”, the actual JSON type is “Number”.

**Case Sensitive Parameters**
The field and parameter names in requests are case sensitive.

**Amounts**
All monetary amounts are given as integer numbers in cents (by default eurocents).

**Currencies**
You can pay and wire funds in these currencies:
* « EUR »,
* « USD »,
* « GBP »,
* « PLN »,
* « CHF »,
* « NOK »,
* « SEK »,
* « DKK »,

The [ISO_4217](https://en.wikipedia.org/wiki/ISO_4217) format is expected
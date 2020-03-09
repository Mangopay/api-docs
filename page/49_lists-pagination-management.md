# Pagination list management

All the list returned by the API are paginable.

**Parameters (in URL query)**

* `Page`: index of the page (start to 1)  Default value: 1
* `Per_Page`: number of items returned.  Default value: 10  Max: 100

Here is an example:
```
users/154876/bank-details?page=2&per_page=10
```

If you miss out any parameter in the query the default value is used.

**Header Informations:**

We provide a link to navigate easily (**first**, **previous**, **next**, **last page**) in the pagination. Here are examples:
```
http://api.mangopay.com/v2/`ClientId`/users/`UserId`/bank-details?page=1&per_page=10">; rel="first
```
```
http://api.mangopay.com/v2/`ClientId`/users/`UserId`/bankaccounts?page=1&per_page=10">; rel="prev
```
```
http://api.mangopay.com/v2/`ClientId`/users/`UserId`/bankaccounts?page=3&per_page=10">; rel="next
```
```
http://api.mangopay.com/v2/`ClientId`/users/`UserId`/bankaccounts?page=21&per_page=10">; rel="last
```

**X-Number-Of-Items**
In the header X-Number-Of-Item you can read the number of items in the entire list.

**X-Number-Of-Pages**
In the header X-Number-Of-Pages you can read the number of pages in the entire list.


# Filtering list management

You can filter **transactions lists** with multiple values for each GET parameter.

Here is an example:
```
users/154876/transactions?Status=Succeeded,Failed&Type=Payin,Payout
```
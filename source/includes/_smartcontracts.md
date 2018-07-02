# Smart Contracts

Data and services provided by ChainRider are often invaluable for different distributed applications based on smart contracts. Below you can find more info on how ChainRider service could be used to feed smart contracts with data about addresses, transactions, payment forwards, etc from different blockchains.

## Oraclize support

Chainrider supports API requests thru [Oriclize](http://www.oraclize.it/) service. This allows you to fetch any data provided by ChainRider APIs in your smart contract or create payment forwards from within the smart contract.

**Important notice**

In order to support TLSNotary Proof one needs to use `https://api-dot-vizlorepaymentprocessor.appspot.com/v1/` instead of `https://api.chainrider.io/v1/` domain in requests.

<h3 id="pfOraclize">Oraclize POST example </h3>

<a id="pfOraclizeToken"></a>
For POST requests, one needs to make sure to add `\n` prior to data payload which informs Oraclize to send data in `application/json` format instead of `application/x-www-form-urlencoded` format which is default one. GET requests could be send without any changes.

An example for creating a paymentforward with TLSNotary proof and fetch payment address could be found on the right side.
<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|payment_address|

> Code samples

```shell
oraclize_query(
"URL",
"json(https://api-dot-vizlorepaymentprocessor.appspot.com/v1/bitcoin/testnet/paymentforward).payment_address",
 '\n{
     "destination_address": "2MxAS7QfBDQspHxmY4g4i92tLNTPH4r2DTZ",
    "callback_url": "http://blockchainvlf.requestcatcher.com/test",
    "token": "o2IEP1p50pe1jfDtz8osOc7RpWZkwbfp"
  }'
);

# Result

mkN6PfXfF6b8dfBrRM9kyVu6zxqzTLXYZ5
```

```php
<?php
oraclize_query(
"URL",
"json(https://api-dot-vizlorepaymentprocessor.appspot.com/v1/bitcoin/testnet/paymentforward).payment_address",
 '\n{
     "destination_address": "2MxAS7QfBDQspHxmY4g4i92tLNTPH4r2DTZ",
    "callback_url": "http://blockchainvlf.requestcatcher.com/test",
    "token": "o2IEP1p50pe1jfDtz8osOc7RpWZkwbfp"
  }'
);
?>

# Result

mkN6PfXfF6b8dfBrRM9kyVu6zxqzTLXYZ5
```

```javascript
oraclize_query(
"URL",
"json(https://api-dot-vizlorepaymentprocessor.appspot.com/v1/bitcoin/testnet/paymentforward).payment_address",
 '\n{
     "destination_address": "2MxAS7QfBDQspHxmY4g4i92tLNTPH4r2DTZ",
    "callback_url": "http://blockchainvlf.requestcatcher.com/test",
    "token": "o2IEP1p50pe1jfDtz8osOc7RpWZkwbfp"
  }'
);

# Result

mkN6PfXfF6b8dfBrRM9kyVu6zxqzTLXYZ5
```

```python
oraclize_query(
"URL",
"json(https://api-dot-vizlorepaymentprocessor.appspot.com/v1/bitcoin/testnet/paymentforward).payment_address",
 '\n{
     "destination_address": "2MxAS7QfBDQspHxmY4g4i92tLNTPH4r2DTZ",
    "callback_url": "http://blockchainvlf.requestcatcher.com/test",
    "token": "o2IEP1p50pe1jfDtz8osOc7RpWZkwbfp"
  }'
);

# Result

mkN6PfXfF6b8dfBrRM9kyVu6zxqzTLXYZ5
```

```ruby
oraclize_query(
"URL",
"json(https://api-dot-vizlorepaymentprocessor.appspot.com/v1/bitcoin/testnet/paymentforward).payment_address",
 '\n{
     "destination_address": "2MxAS7QfBDQspHxmY4g4i92tLNTPH4r2DTZ",
    "callback_url": "http://blockchainvlf.requestcatcher.com/test",
    "token": "o2IEP1p50pe1jfDtz8osOc7RpWZkwbfp"
  }'
);

# Result

mkN6PfXfF6b8dfBrRM9kyVu6zxqzTLXYZ5
```

```java
oraclize_query(
"URL",
"json(https://api-dot-vizlorepaymentprocessor.appspot.com/v1/bitcoin/testnet/paymentforward).payment_address",
 '\n{
     "destination_address": "2MxAS7QfBDQspHxmY4g4i92tLNTPH4r2DTZ",
    "callback_url": "http://blockchainvlf.requestcatcher.com/test",
    "token": "o2IEP1p50pe1jfDtz8osOc7RpWZkwbfp"
  }'
);

# Result

mkN6PfXfF6b8dfBrRM9kyVu6zxqzTLXYZ5
```

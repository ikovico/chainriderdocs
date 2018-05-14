# Payment Forward APIs

The set of APIs allows you to crate and manage payment forward rules.
Payment forward allows you to forward DASH received on one address to one or two new addresses.
In order to create a payment forward partially populated PaymentForward object is used.

Once created, payment forward rule will continue to forward payments in a predefined way set during payment forward creation until you explicitly delete it by calling the API for payment forward delete.

## Create Payment Forward

<h3 id="postCreatePaymentForward">POST /paymentforward </h3>

<a id="opIdpostCreatePaymentForward"></a>

*Create Payment Forward*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|destination_address|body|String|True|Destination address represents the address to which received DASH will be forwarded.|
|commission_address|body|String|False|Commission address is an optional address to which funds will be forwarded in a predefined way. If commission address is specified, one must specify either commission_fee_percent or commission_fee_duffs parameter (cannot use both for the same payment forward)|
|commission_fee_percent|body|Float|False|Commission fee as normalized percentage. Minimum is 0.001. Maximum is 0.999. In case commission_address is set, commission_fee_percent specifies amount which will be forwarded to commission_address as percentage of the total received payment. The rest of the funds will be forwarded to destination_address. Mining fee is subtracted from previously calculated commission amount.|
|commission_fee_duffs|body|Integer|False|Commission fee in duffs. In case commission_address is set, commission_fee_duffs specifies fixed amount of the total received payment which will be forwarded to commission_address. The rest of the funds will be forwarded to destination_address.|
|mining_fee_duffs|body|String|False|Mining fee for forwarding transaction. Default fee is 10 000 duffs. Min 10 000 duffs. Max 150 000 duffs.|
|callback_url|body|String|False|URL to which the notification will be posted upon each successful payment forward.|
|token|body|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[PaymentForwardObject](#schemepaymentforwardobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

> Code samples

```shell
curl -X POST https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -D '<body_here>'
```

```php
<?php
    $body="<body_here>";
    $opts = array('http' =>
      array(
        'method'  => 'POST',
        'header'  => Content-Type: application/json\r\nAccept: application/json\r\n",
        'content' => $body
      )
    );
    $context  = stream_context_create($opts);
    $URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward";
    $result = file_get_contents($url, false, $context, -1, 40000);
);


$context = stream_context_create($aHTTP);
    $response = file_get_contents($URL, false, $context);
?>

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
};

var requestBody=<body_here>

$.ajax({
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward',
  method: 'POST',
  headers: headers,
  data: requestBody,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward',
         payload:<body_here>, headers: headers

p JSON.parse(result)
```

```python
import requests

headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward',
                  data=<body_here>, params={}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestProperty("Accept", "application/json");
con.setRequestProperty("Content-Type", "application/json");
con.setDoOutput(true);
con.setRequestMethod("POST");
OutputStream os = con.getOutputStream();
OutputStreamWriter osw = new OutputStreamWriter(os, "UTF-8");
osw.write("<body_here>");
osw.flush();
osw.close();
os.close();  //don't forget to close the OutputStream
httpCon.connect();


//read the inputstream and print it
String result;
BufferedInputStream bis = new BufferedInputStream(con.getInputStream());
ByteArrayOutputStream buf = new ByteArrayOutputStream();
int result2 = bis.read();
while(result2 != -1) {
    buf.write((byte) result2);
    result2 = bis.read();
}
result = buf.toString();
System.out.println(result);
```

> Body parameter


```json
{
    "destination_address": "XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
    "callback_url": "http://blockchainvlf.requestcatcher.com/test",
    "token": <TOKEN>,
    "commission_fee_percent": 0.1,
    "commission_address": "XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb"
}
```

> Example response

```json
{
    "paymentforward_id":"2pRxUXWLXQlwABUUPmuo9xi1Ghaqa0Lj",
    "payment_address":"XhhqcCVhSmkETV6Q55RFskgASyUd9Seuwv",
    "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
    "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
    "commission_fee_percent":0.1,
    "mining_fee_duffs":10000
}
```

## Get Payment Forward by Id

<h3 id="getPaymentForwardById">GET /paymentforward/< paymentforward_id > </h3>

<a id="opIdGetPaymentForwardById"></a>

*Get Payment Forward by ID for corresponding token*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|paymentforward_id|path|String|True|Unique Payment Forward ID|
|token|query|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[PaymentForwardObject](#schemepaymentforwardobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward/<PAYMENTFORWARD_ID>?token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
{
    "paymentforward_id":"XozC3GyOfhEGwD6zK8rIvi0HU6ZwqAuU",
    "payment_address":"XcyXgQzCnKsWpK2YSjoRYwM1vWB6GvWQ2u",
    "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
    "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
    "commission_fee_percent":0.1,
    "commission_fee_duffs":null,
    "created_date":"2018-04-13T11:01:46.000Z",
    "callback_url":"https://webhook.site/175c954d-6595-4bf8-a518-990f5e876fa7",
    "mining_fee_duffs":10000,
    "processed_txs":
    [
        {
            "input_transaction_hash":"6e3648463d26ee5af215fa3b61e976bf06cc7b1c6d2c034253967be65fc1c889",
            "received_amount_duffs":5000000,
            "transaction_hash":"7c89d485e06f295de6fb1d676311340be35148dfc1a54de13b57e785227da78f",
            "processed_date":"2018-04-13T11:04:19.000Z"
        }
    ]
}
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward/<PAYMENTFORWARD_ID>?token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "paymentforward_id":"XozC3GyOfhEGwD6zK8rIvi0HU6ZwqAuU",
    "payment_address":"XcyXgQzCnKsWpK2YSjoRYwM1vWB6GvWQ2u",
    "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
    "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
    "commission_fee_percent":0.1,
    "commission_fee_duffs":null,
    "created_date":"2018-04-13T11:01:46.000Z",
    "callback_url":"https://webhook.site/175c954d-6595-4bf8-a518-990f5e876fa7",
    "mining_fee_duffs":10000,
    "processed_txs":
    [
        {
            "input_transaction_hash":"6e3648463d26ee5af215fa3b61e976bf06cc7b1c6d2c034253967be65fc1c889",
            "received_amount_duffs":5000000,
            "transaction_hash":"7c89d485e06f295de6fb1d676311340be35148dfc1a54de13b57e785227da78f",
            "processed_date":"2018-04-13T11:04:19.000Z"
        }
    ]
}
?>
```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

$.ajax({
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward/<PAYMENTFORWARD_ID>?token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "paymentforward_id":"XozC3GyOfhEGwD6zK8rIvi0HU6ZwqAuU",
    "payment_address":"XcyXgQzCnKsWpK2YSjoRYwM1vWB6GvWQ2u",
    "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
    "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
    "commission_fee_percent":0.1,
    "commission_fee_duffs":null,
    "created_date":"2018-04-13T11:01:46.000Z",
    "callback_url":"https://webhook.site/175c954d-6595-4bf8-a518-990f5e876fa7",
    "mining_fee_duffs":10000,
    "processed_txs":
    [
        {
            "input_transaction_hash":"6e3648463d26ee5af215fa3b61e976bf06cc7b1c6d2c034253967be65fc1c889",
            "received_amount_duffs":5000000,
            "transaction_hash":"7c89d485e06f295de6fb1d676311340be35148dfc1a54de13b57e785227da78f",
            "processed_date":"2018-04-13T11:04:19.000Z"
        }
    ]
}
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
}

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward/<PAYMENTFORWARD_ID>',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "paymentforward_id":"XozC3GyOfhEGwD6zK8rIvi0HU6ZwqAuU",
    "payment_address":"XcyXgQzCnKsWpK2YSjoRYwM1vWB6GvWQ2u",
    "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
    "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
    "commission_fee_percent":0.1,
    "commission_fee_duffs":null,
    "created_date":"2018-04-13T11:01:46.000Z",
    "callback_url":"https://webhook.site/175c954d-6595-4bf8-a518-990f5e876fa7",
    "mining_fee_duffs":10000,
    "processed_txs":
    [
        {
            "input_transaction_hash":"6e3648463d26ee5af215fa3b61e976bf06cc7b1c6d2c034253967be65fc1c889",
            "received_amount_duffs":5000000,
            "transaction_hash":"7c89d485e06f295de6fb1d676311340be35148dfc1a54de13b57e785227da78f",
            "processed_date":"2018-04-13T11:04:19.000Z"
        }
    ]
}
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward/<PAYMENTFORWARD_ID>',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "paymentforward_id":"XozC3GyOfhEGwD6zK8rIvi0HU6ZwqAuU",
    "payment_address":"XcyXgQzCnKsWpK2YSjoRYwM1vWB6GvWQ2u",
    "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
    "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
    "commission_fee_percent":0.1,
    "commission_fee_duffs":null,
    "created_date":"2018-04-13T11:01:46.000Z",
    "callback_url":"https://webhook.site/175c954d-6595-4bf8-a518-990f5e876fa7",
    "mining_fee_duffs":10000,
    "processed_txs":
    [
        {
            "input_transaction_hash":"6e3648463d26ee5af215fa3b61e976bf06cc7b1c6d2c034253967be65fc1c889",
            "received_amount_duffs":5000000,
            "transaction_hash":"7c89d485e06f295de6fb1d676311340be35148dfc1a54de13b57e785227da78f",
            "processed_date":"2018-04-13T11:04:19.000Z"
        }
    ]
}
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward/<PAYMENTFORWARD_ID>?token=<TOKEN>");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestProperty("Accept", "application/json");
con.setRequestProperty("Content-Type", "application/json");
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

// Response example
{
    "paymentforward_id":"XozC3GyOfhEGwD6zK8rIvi0HU6ZwqAuU",
    "payment_address":"XcyXgQzCnKsWpK2YSjoRYwM1vWB6GvWQ2u",
    "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
    "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
    "commission_fee_percent":0.1,
    "commission_fee_duffs":null,
    "created_date":"2018-04-13T11:01:46.000Z",
    "callback_url":"https://webhook.site/175c954d-6595-4bf8-a518-990f5e876fa7",
    "mining_fee_duffs":10000,
    "processed_txs":
    [
        {
            "input_transaction_hash":"6e3648463d26ee5af215fa3b61e976bf06cc7b1c6d2c034253967be65fc1c889",
            "received_amount_duffs":5000000,
            "transaction_hash":"7c89d485e06f295de6fb1d676311340be35148dfc1a54de13b57e785227da78f",
            "processed_date":"2018-04-13T11:04:19.000Z"
        }
    ]
}
```

## Get Payment Forwards

<h3 id="getPaymentForwardsPaginated">GET /paymentforward </h3>

<a id="opIdGetPaymentForwardsPaginated"></a>

*Get all Payment Forwards for corresponding token*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|from|query|Integer|False|Start index (zero index based, default 0)|
|to|query|Integer|False|End index (zero index based, default 100)|
|token|query|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Array [PaymentForwardObject](#schemepaymentforwardobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward?token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
[
    {
        "paymentforward_id":"bbM4nQ3fnAfI5VhJ9K8wWQQOx0Namr4l",
        "payment_address":"XnRZrhsm5vWEitEqXAVGG1JTCeGBeJfj2d",
        "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
        "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
        "commission_fee_percent":null,
        "commission_fee_duffs":20000,
        "created_date":"2018-04-12T12:10:56.000Z",
        "callback_url":"http://blockchainvlf.requestcatcher.com/test",
        "mining_fee_duffs":10000
    },
    {
        "paymentforward_id":"fHKGPLDqWUlce0cQIPzROzexDZ9WwTlj",
        "payment_address":"XfFckk6ky9WeuNuCqVNxgXuPUobjfeHGGu",
        "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
        "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
        "commission_fee_percent":0.1,
        "commission_fee_duffs":null,
        "created_date":"2018-04-12T12:10:56.000Z",
        "callback_url":"http://blockchainvlf.requestcatcher.com/test",
        "mining_fee_duffs":10000
    }
]
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward?token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
[
    {
        "paymentforward_id":"bbM4nQ3fnAfI5VhJ9K8wWQQOx0Namr4l",
        "payment_address":"XnRZrhsm5vWEitEqXAVGG1JTCeGBeJfj2d",
        "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
        "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
        "commission_fee_percent":null,
        "commission_fee_duffs":20000,
        "created_date":"2018-04-12T12:10:56.000Z",
        "callback_url":"http://blockchainvlf.requestcatcher.com/test",
        "mining_fee_duffs":10000
    },
    {
        "paymentforward_id":"fHKGPLDqWUlce0cQIPzROzexDZ9WwTlj",
        "payment_address":"XfFckk6ky9WeuNuCqVNxgXuPUobjfeHGGu",
        "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
        "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
        "commission_fee_percent":0.1,
        "commission_fee_duffs":null,
        "created_date":"2018-04-12T12:10:56.000Z",
        "callback_url":"http://blockchainvlf.requestcatcher.com/test",
        "mining_fee_duffs":10000
    }
]
?>
```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

$.ajax({
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward?token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
[
    {
        "paymentforward_id":"bbM4nQ3fnAfI5VhJ9K8wWQQOx0Namr4l",
        "payment_address":"XnRZrhsm5vWEitEqXAVGG1JTCeGBeJfj2d",
        "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
        "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
        "commission_fee_percent":null,
        "commission_fee_duffs":20000,
        "created_date":"2018-04-12T12:10:56.000Z",
        "callback_url":"http://blockchainvlf.requestcatcher.com/test",
        "mining_fee_duffs":10000
    },
    {
        "paymentforward_id":"fHKGPLDqWUlce0cQIPzROzexDZ9WwTlj",
        "payment_address":"XfFckk6ky9WeuNuCqVNxgXuPUobjfeHGGu",
        "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
        "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
        "commission_fee_percent":0.1,
        "commission_fee_duffs":null,
        "created_date":"2018-04-12T12:10:56.000Z",
        "callback_url":"http://blockchainvlf.requestcatcher.com/test",
        "mining_fee_duffs":10000
    }
]
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
}

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
[
    {
        "paymentforward_id":"bbM4nQ3fnAfI5VhJ9K8wWQQOx0Namr4l",
        "payment_address":"XnRZrhsm5vWEitEqXAVGG1JTCeGBeJfj2d",
        "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
        "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
        "commission_fee_percent":null,
        "commission_fee_duffs":20000,
        "created_date":"2018-04-12T12:10:56.000Z",
        "callback_url":"http://blockchainvlf.requestcatcher.com/test",
        "mining_fee_duffs":10000
    },
    {
        "paymentforward_id":"fHKGPLDqWUlce0cQIPzROzexDZ9WwTlj",
        "payment_address":"XfFckk6ky9WeuNuCqVNxgXuPUobjfeHGGu",
        "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
        "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
        "commission_fee_percent":0.1,
        "commission_fee_duffs":null,
        "created_date":"2018-04-12T12:10:56.000Z",
        "callback_url":"http://blockchainvlf.requestcatcher.com/test",
        "mining_fee_duffs":10000
    }
]
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
[
    {
        "paymentforward_id":"bbM4nQ3fnAfI5VhJ9K8wWQQOx0Namr4l",
        "payment_address":"XnRZrhsm5vWEitEqXAVGG1JTCeGBeJfj2d",
        "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
        "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
        "commission_fee_percent":null,
        "commission_fee_duffs":20000,
        "created_date":"2018-04-12T12:10:56.000Z",
        "callback_url":"http://blockchainvlf.requestcatcher.com/test",
        "mining_fee_duffs":10000
    },
    {
        "paymentforward_id":"fHKGPLDqWUlce0cQIPzROzexDZ9WwTlj",
        "payment_address":"XfFckk6ky9WeuNuCqVNxgXuPUobjfeHGGu",
        "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
        "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
        "commission_fee_percent":0.1,
        "commission_fee_duffs":null,
        "created_date":"2018-04-12T12:10:56.000Z",
        "callback_url":"http://blockchainvlf.requestcatcher.com/test",
        "mining_fee_duffs":10000
    }
]
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward?token=<TOKEN>");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestProperty("Accept", "application/json");
con.setRequestProperty("Content-Type", "application/json");
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

// Response example
[
    {
        "paymentforward_id":"bbM4nQ3fnAfI5VhJ9K8wWQQOx0Namr4l",
        "payment_address":"XnRZrhsm5vWEitEqXAVGG1JTCeGBeJfj2d",
        "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
        "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
        "commission_fee_percent":null,
        "commission_fee_duffs":20000,
        "created_date":"2018-04-12T12:10:56.000Z",
        "callback_url":"http://blockchainvlf.requestcatcher.com/test",
        "mining_fee_duffs":10000
    },
    {
        "paymentforward_id":"fHKGPLDqWUlce0cQIPzROzexDZ9WwTlj",
        "payment_address":"XfFckk6ky9WeuNuCqVNxgXuPUobjfeHGGu",
        "destination_address":"XvtUXjA3UBnGvsbV7MDs4Duu411CfofDEK",
        "commission_address":"XtFU7dFv8b7JeW7eG9yYXc28uSYUQqiNCb",
        "commission_fee_percent":0.1,
        "commission_fee_duffs":null,
        "created_date":"2018-04-12T12:10:56.000Z",
        "callback_url":"http://blockchainvlf.requestcatcher.com/test",
        "mining_fee_duffs":10000
    }
]
```

## Delete Payment Forward

<h3 id="deletePaymentForward">DELETE /paymentforward/< paymentforward_id > </h3>

<a id="opIdDeletePaymentForward"></a>

*Delete Payment Forward by id for corresponding token*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|paymentforward_id|path|String|True|Unique Payment forward ID|
|token|query|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|{}|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

> Code samples

```shell
curl -X DELETE https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward/<PAYMENTFORWARD_ID>?token=<TOKEN>\
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
{}
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward/<PAYMENTFORWARD_ID>?token=<TOKEN>";
$aHTTP['http']['method']  = 'DELETE';
$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";
$context = stream_context_create($aHTTP);
$response = file_get_contents($URL, false, $context);
?>

// Response example
{}
```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

$.ajax({
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward/<PAYMENTFORWARD_ID>?token=<TOKEN>',
  method: 'DELETE',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{}
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Authorization' => 'Bearer <token>'
}

result = RestClient.delete 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward/<PAYMENTFORWARD_ID>',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{}
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
}

r = requests.delete('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward/<PAYMENTFORWARD_ID>',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{}
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/paymentforward/<PAYMENTFORWARD_ID>?token=<TOKEN>");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestProperty("Accept", "application/json");
con.setRequestProperty("Content-Type", "application/json");
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

// Response example
{}
```

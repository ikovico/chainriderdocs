# Events and Web Hooks

Blockchains are extremely vivid distributed ledgers with large number of events such as new transactions, new blocks, confirmation of transactions, changing of address balance, etc. ChainRider offers rich set of different events you can listen to. The notification system is based on web hook methodology and each time the event is triggered on the blockchain, you will receive notification on a specified URL. This way you can stay up to speed with latest updates on the blockchain that concern you.

## Event types

Following event types are supported by ChainRider:

|Event type|Description|
|---|---|
|BLOCK|Triggered each time new block is added on the blockchain. The notification provides Block object as a payload.|
|TRANSACTION|Triggered each time new transaction is emitted on the blockchain. It could be prior to reaching the block (unconfirmed) or when the transaction is included in the block (1 confirmation). The notification provides Transaction object as a payload. The event will provide notifications for both regular transactions and InstantSend transactions.|
|IX_TRANSACTION|Triggered each time new InstantSend transaction is emitted on the blockchain. The notification provides Transaction object as a payload. Only InstantSend transactions trigger the event.|
|ADDRESS|Triggered each time new transaction is emitted on the blockchain which includes specified address. Basically the event is triggered each time a balance of the address is changed (coins have been received to or sent from the address). Additionally you can specify "confirmation" parameter which allows you to receive notifications each time the transaction is confirmed in the blockchain until the specified number of confirmations. The notification provides Transaction object as a payload. This allows you to act on address balance change when you are confident that the transaction has been confirmed in the blockchain. In case the transaction is InstantSend the corresponding `txlock` parameter is set to True and provided within the Transaction object.|

## Web Hooks

In order to set up a web hook you need to create an event by leveraging the Create Event API below. Once the event is triggered you will receive notification on a specified URL with method `POST` in `JSON` format. In order to successfully confirm that you have received a notification, you need to respond with status code `200` to this `POST` request.

On failed notification delivery, each delivery is attempted 6 times with exponential back-off: 1s, 2s, 4s, 8s, 16s, 32s. In case the cycle fails to deliver notification (due to any reason such as network connectivity issue, bad gateway, response status code different from 200, etc.), cycle will be retried for 112 times prior to deleting the event/web hook.


## Create Event

<h3 id="postCreateEvent">POST /events </h3>

<a id="opIdpostCreateEvent"></a>

*Create Event / Web Hook*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|event_type|body|String|True|Type of the event. Please refer to Event Types for more details.|
|callback_url|body|String|True|The URL to which the notification will be posted once the event is triggered. The notification payload is delivered in JSON format by using method POST. The response status code must be set to 200 in order to acknowledge the notification delivery.|
|address|body|String|False|This parameter is required if you are creating `ADDRESS` event type. It represents an address for which you want to be notified on balance change.|
|confirmations|body|Integer|False|Test|
|token|body|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[PaymentForwardObject](#schemepaymentforwardobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<a id="divider"></a>

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

## Get Event by Id

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

<a id="divider"></a>

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

## Get Events

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

<a id="divider"></a>

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

## Delete Event

<h3 id="deletePaymentForward3">DELETE /paymentforward/< paymentforward_id > </h3>

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

<a id="divider"></a>

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

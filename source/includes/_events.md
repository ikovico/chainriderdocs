# Events and Web Hooks

Blockchains are extremely vivid distributed ledgers with large number of events such as new transactions, new blocks, confirmation of transactions, changing of address balance, etc. ChainRider offers rich set of different events you can listen to. The notification system is based on web hook methodology and each time the event is triggered on the blockchain, you will receive notification on a specified URL. This way you can stay up to speed with latest updates on the blockchain that concern you.

## Event types

<a id="eventtypesheader"></a>

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
|event_type|body|String|True|Type of the event - ENUM {'ADDRESS', 'BLOCK', 'TRANSACTION', 'IX_TRANSACTION'}. Please refer to [Event Types](#eventtypesheader) for more details.|
|callback_url|body|String|True|The URL to which the notification will be posted once the event is triggered. The notification payload is delivered in JSON format by using method POST. The response status code must be set to 200 in order to acknowledge the notification delivery.|
|address|body|String|False|This parameter is required if you are creating `ADDRESS` event type. It represents an address for which you want to be notified on balance change.|
|confirmations|body|Integer|False|Optional parameter with default value set to 0 wile max value is 9. Confirmations parameter should only be set if you are creating `ADDRESS` event type. In case it's set, you will receive notifications for detected transactions involving specified address each time until detected transaction receives specified number of confirmations.|
|token|body|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[EventIdObject](#schemeeventidobject)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|{"error": "error description"}|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<a id="divider"></a>

> Code samples

```shell
curl -X POST https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events \
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
    $URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events";
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
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events',
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

result = RestClient.post 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events',
         payload:<body_here>, headers: headers

p JSON.parse(result)
```

```python
import requests

headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events',
                  data=<body_here>, params={}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events");
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
    "event_type": "ADDRESS",
    "callback_url": "http://blockchainvlf.requestcatcher.com/test",
    "token": <TOKEN>,
    "address": "yiVCptUPyxLLxt7dndcLrUjYwt3W16hwQ9",
    "confirmations": 3
}
```

> Example response

```json
{
    "event_id":"GCeUpByO6V08eUgYB1mg9GSXPgN77LUV"
}
```

## Get Event by Id

<h3 id="getEventById">GET /events/< event_id > </h3>

<a id="opIdGetEventById"></a>

*Get Event by ID for corresponding token*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|event_id|path|String|True|Unique Event ID|
|token|query|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[EventObject](#schemeeventobject)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|{"error": "error description"}|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<a id="divider"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events/<EVENT_ID>?token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
{
    "event_id": "YyZMc3zVNrCsgMi9BWv4ckfXj4R4aW76",
    "event_type": "ADDRESS",
    "callback_url": "http://addrvlf.requestcatcher.com/test",
    "address": "yiVCptUPyxLLxt7dndcLrUjYwt3W16hwQ9",
    "confirmations": 4,
    "retry": 0,
    "created_date": "2018-08-10T07:28:00.000Z",
    "enabled": 1
}
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events/<EVENT_ID>?token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "event_id": "YyZMc3zVNrCsgMi9BWv4ckfXj4R4aW76",
    "event_type": "ADDRESS",
    "callback_url": "http://addrvlf.requestcatcher.com/test",
    "address": "yiVCptUPyxLLxt7dndcLrUjYwt3W16hwQ9",
    "confirmations": 4,
    "retry": 0,
    "created_date": "2018-08-10T07:28:00.000Z",
    "enabled": 1
}
?>
```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

$.ajax({
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events/<EVENT_ID>?token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "event_id": "YyZMc3zVNrCsgMi9BWv4ckfXj4R4aW76",
    "event_type": "ADDRESS",
    "callback_url": "http://addrvlf.requestcatcher.com/test",
    "address": "yiVCptUPyxLLxt7dndcLrUjYwt3W16hwQ9",
    "confirmations": 4,
    "retry": 0,
    "created_date": "2018-08-10T07:28:00.000Z",
    "enabled": 1
}
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
}

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events/<EVENT_ID>',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "event_id": "YyZMc3zVNrCsgMi9BWv4ckfXj4R4aW76",
    "event_type": "ADDRESS",
    "callback_url": "http://addrvlf.requestcatcher.com/test",
    "address": "yiVCptUPyxLLxt7dndcLrUjYwt3W16hwQ9",
    "confirmations": 4,
    "retry": 0,
    "created_date": "2018-08-10T07:28:00.000Z",
    "enabled": 1
}
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events/<EVENT_ID>',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "event_id": "YyZMc3zVNrCsgMi9BWv4ckfXj4R4aW76",
    "event_type": "ADDRESS",
    "callback_url": "http://addrvlf.requestcatcher.com/test",
    "address": "yiVCptUPyxLLxt7dndcLrUjYwt3W16hwQ9",
    "confirmations": 4,
    "retry": 0,
    "created_date": "2018-08-10T07:28:00.000Z",
    "enabled": 1
}
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events/<EVENT_ID>?token=<TOKEN>");
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
    "event_id": "YyZMc3zVNrCsgMi9BWv4ckfXj4R4aW76",
    "event_type": "ADDRESS",
    "callback_url": "http://addrvlf.requestcatcher.com/test",
    "address": "yiVCptUPyxLLxt7dndcLrUjYwt3W16hwQ9",
    "confirmations": 4,
    "retry": 0,
    "created_date": "2018-08-10T07:28:00.000Z",
    "enabled": 1
}
```

## Get Events

<h3 id="getEventsPaginated">GET /events </h3>

<a id="opIdGetEventsPaginated"></a>

*Get all Events for corresponding token*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|from|query|Integer|False|Start index (zero index based, default 0)|
|to|query|Integer|False|End index (zero index based, default 100)|
|token|query|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Array [EventObject](#schemeeventobject)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|{"error": "error description"}|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<a id="divider"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events?token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
[
    {
        "event_id": "YyZMc3zVNrCsgMi9BWv4ckfXj4R4aW76",
        "event_type": "ADDRESS",
        "callback_url": "http://addrvlf.requestcatcher.com/test",
        "address": "yiVCptUPyxLLxt7dndcLrUjYwt3W16hwQ9",
        "confirmations": 4,
        "retry": 0,
        "created_date": "2018-08-10T07:28:00.000Z",
        "enabled": 1
    },
    {
        "event_id": "ZjWQQkQzv91XqUiskvXv5wlK8bETvpdx",
        "event_type": "BLOCK",
        "callback_url": "http://blockvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:28:35.000Z",
        "enabled": 1
    },
    {
        "event_id": "SEDMCFP7IvevVcnMUDLjpzE07zghzZyV",
        "event_type": "TRANSACTION",
        "callback_url": "http://txvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:28:49.000Z",
        "enabled": 1
    },
    {
        "event_id": "TFTnKD1R0AGk4bkBFJAPkxN4ro1AdrKD",
        "event_type": "IX_TRANSACTION",
        "callback_url": "http://itxvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:29:01.000Z",
        "enabled": 1
    }
]
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events?token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
[
    {
        "event_id": "YyZMc3zVNrCsgMi9BWv4ckfXj4R4aW76",
        "event_type": "ADDRESS",
        "callback_url": "http://addrvlf.requestcatcher.com/test",
        "address": "yiVCptUPyxLLxt7dndcLrUjYwt3W16hwQ9",
        "confirmations": 4,
        "retry": 0,
        "created_date": "2018-08-10T07:28:00.000Z",
        "enabled": 1
    },
    {
        "event_id": "ZjWQQkQzv91XqUiskvXv5wlK8bETvpdx",
        "event_type": "BLOCK",
        "callback_url": "http://blockvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:28:35.000Z",
        "enabled": 1
    },
    {
        "event_id": "SEDMCFP7IvevVcnMUDLjpzE07zghzZyV",
        "event_type": "TRANSACTION",
        "callback_url": "http://txvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:28:49.000Z",
        "enabled": 1
    },
    {
        "event_id": "TFTnKD1R0AGk4bkBFJAPkxN4ro1AdrKD",
        "event_type": "IX_TRANSACTION",
        "callback_url": "http://itxvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:29:01.000Z",
        "enabled": 1
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
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events?token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
[
    {
        "event_id": "YyZMc3zVNrCsgMi9BWv4ckfXj4R4aW76",
        "event_type": "ADDRESS",
        "callback_url": "http://addrvlf.requestcatcher.com/test",
        "address": "yiVCptUPyxLLxt7dndcLrUjYwt3W16hwQ9",
        "confirmations": 4,
        "retry": 0,
        "created_date": "2018-08-10T07:28:00.000Z",
        "enabled": 1
    },
    {
        "event_id": "ZjWQQkQzv91XqUiskvXv5wlK8bETvpdx",
        "event_type": "BLOCK",
        "callback_url": "http://blockvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:28:35.000Z",
        "enabled": 1
    },
    {
        "event_id": "SEDMCFP7IvevVcnMUDLjpzE07zghzZyV",
        "event_type": "TRANSACTION",
        "callback_url": "http://txvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:28:49.000Z",
        "enabled": 1
    },
    {
        "event_id": "TFTnKD1R0AGk4bkBFJAPkxN4ro1AdrKD",
        "event_type": "IX_TRANSACTION",
        "callback_url": "http://itxvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:29:01.000Z",
        "enabled": 1
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

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
[
    {
        "event_id": "YyZMc3zVNrCsgMi9BWv4ckfXj4R4aW76",
        "event_type": "ADDRESS",
        "callback_url": "http://addrvlf.requestcatcher.com/test",
        "address": "yiVCptUPyxLLxt7dndcLrUjYwt3W16hwQ9",
        "confirmations": 4,
        "retry": 0,
        "created_date": "2018-08-10T07:28:00.000Z",
        "enabled": 1
    },
    {
        "event_id": "ZjWQQkQzv91XqUiskvXv5wlK8bETvpdx",
        "event_type": "BLOCK",
        "callback_url": "http://blockvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:28:35.000Z",
        "enabled": 1
    },
    {
        "event_id": "SEDMCFP7IvevVcnMUDLjpzE07zghzZyV",
        "event_type": "TRANSACTION",
        "callback_url": "http://txvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:28:49.000Z",
        "enabled": 1
    },
    {
        "event_id": "TFTnKD1R0AGk4bkBFJAPkxN4ro1AdrKD",
        "event_type": "IX_TRANSACTION",
        "callback_url": "http://itxvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:29:01.000Z",
        "enabled": 1
    }
]
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
[
    {
        "event_id": "YyZMc3zVNrCsgMi9BWv4ckfXj4R4aW76",
        "event_type": "ADDRESS",
        "callback_url": "http://addrvlf.requestcatcher.com/test",
        "address": "yiVCptUPyxLLxt7dndcLrUjYwt3W16hwQ9",
        "confirmations": 4,
        "retry": 0,
        "created_date": "2018-08-10T07:28:00.000Z",
        "enabled": 1
    },
    {
        "event_id": "ZjWQQkQzv91XqUiskvXv5wlK8bETvpdx",
        "event_type": "BLOCK",
        "callback_url": "http://blockvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:28:35.000Z",
        "enabled": 1
    },
    {
        "event_id": "SEDMCFP7IvevVcnMUDLjpzE07zghzZyV",
        "event_type": "TRANSACTION",
        "callback_url": "http://txvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:28:49.000Z",
        "enabled": 1
    },
    {
        "event_id": "TFTnKD1R0AGk4bkBFJAPkxN4ro1AdrKD",
        "event_type": "IX_TRANSACTION",
        "callback_url": "http://itxvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:29:01.000Z",
        "enabled": 1
    }
]
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events?token=<TOKEN>");
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
        "event_id": "YyZMc3zVNrCsgMi9BWv4ckfXj4R4aW76",
        "event_type": "ADDRESS",
        "callback_url": "http://addrvlf.requestcatcher.com/test",
        "address": "yiVCptUPyxLLxt7dndcLrUjYwt3W16hwQ9",
        "confirmations": 4,
        "retry": 0,
        "created_date": "2018-08-10T07:28:00.000Z",
        "enabled": 1
    },
    {
        "event_id": "ZjWQQkQzv91XqUiskvXv5wlK8bETvpdx",
        "event_type": "BLOCK",
        "callback_url": "http://blockvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:28:35.000Z",
        "enabled": 1
    },
    {
        "event_id": "SEDMCFP7IvevVcnMUDLjpzE07zghzZyV",
        "event_type": "TRANSACTION",
        "callback_url": "http://txvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:28:49.000Z",
        "enabled": 1
    },
    {
        "event_id": "TFTnKD1R0AGk4bkBFJAPkxN4ro1AdrKD",
        "event_type": "IX_TRANSACTION",
        "callback_url": "http://itxvlf.requestcatcher.com/test",
        "address": "",
        "confirmations": 0,
        "retry": 0,
        "created_date": "2018-08-10T07:29:01.000Z",
        "enabled": 1
    }
]
```

## Delete Event

<h3 id="deleteEvent">DELETE /events/< event_id > </h3>

<a id="opIdDeleteEvent"></a>

*Delete event_type by id for corresponding token*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|event_id|path|String|True|Unique Event ID|
|token|query|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|{}|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|{"error": "error description"}|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<a id="divider"></a>

> Code samples

```shell
curl -X DELETE https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events/<EVENT_ID>?token=<TOKEN>\
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
{}
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events/<EVENT_ID>?token=<TOKEN>";
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
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events/<EVENT_ID>?token=<TOKEN>',
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

result = RestClient.delete 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events/<EVENT_ID>',
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

r = requests.delete('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events/<EVENT_ID>',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{}
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/events/<EVENT_ID>?token=<TOKEN>");
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

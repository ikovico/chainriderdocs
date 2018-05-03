# Blockchain APIs

The set of APIs below provides insight into the network status and general information about the corresponding blockchain selected by specifying endpoint for digital currency and blockchain type.

## General information

<h3 id="getBlockchainInfo">GET /status</h3>

<a id="opIdGetBlockchainInfo"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getInfo&token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
{
    "info":
    {
        "version":120203,
        "insightversion":"0.6.0",
        "protocolversion":70208,
        "blocks":855511,
        "timeoffset":0,
        "connections":8,
        "proxy":"",
        "difficulty":41610185.00844856,
        "testnet":false,
        "relayfee":0.00001,
        "errors":"",
        "network":"livenet"
    }
}
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getInfo&token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "info":
    {
        "version":120203,
        "insightversion":"0.6.0",
        "protocolversion":70208,
        "blocks":855511,
        "timeoffset":0,
        "connections":8,
        "proxy":"",
        "difficulty":41610185.00844856,
        "testnet":false,
        "relayfee":0.00001,
        "errors":"",
        "network":"livenet"
    }
}
?>
```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

$.ajax({
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getInfo&token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "info":
    {
        "version":120203,
        "insightversion":"0.6.0",
        "protocolversion":70208,
        "blocks":855511,
        "timeoffset":0,
        "connections":8,
        "proxy":"",
        "difficulty":41610185.00844856,
        "testnet":false,
        "relayfee":0.00001,
        "errors":"",
        "network":"livenet"
    }
}
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
}

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status',
         params: {'q': 'getInfo', 'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "info":
    {
        "version":120203,
        "insightversion":"0.6.0",
        "protocolversion":70208,
        "blocks":855511,
        "timeoffset":0,
        "connections":8,
        "proxy":"",
        "difficulty":41610185.00844856,
        "testnet":false,
        "relayfee":0.00001,
        "errors":"",
        "network":"livenet"
    }
}
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status',
                  params={'q': 'getInfo', 'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "info":
    {
        "version":120203,
        "insightversion":"0.6.0",
        "protocolversion":70208,
        "blocks":855511,
        "timeoffset":0,
        "connections":8,
        "proxy":"",
        "difficulty":41610185.00844856,
        "testnet":false,
        "relayfee":0.00001,
        "errors":"",
        "network":"livenet"
    }
}
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getInfo&token=<TOKEN>");
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
    "info":
    {
        "version":120203,
        "insightversion":"0.6.0",
        "protocolversion":70208,
        "blocks":855511,
        "timeoffset":0,
        "connections":8,
        "proxy":"",
        "difficulty":41610185.00844856,
        "testnet":false,
        "relayfee":0.00001,
        "errors":"",
        "network":"livenet"
    }
}
```

*Get general information about the blockchain.*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|q|query|String|True|Please use `geInfo` as value|
|token|query|String|True|Token obtained from the ChainRider service|


|Response|
|-----|

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[BlockchainInfoObject](#schemeblockchaininfoobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

## Current difficulty

<h3 id="getBlockchainDifficulty">GET /status</h3>

<a id="opIdGetBlockchainDifficulty"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getDifficulty&token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
{
    "difficulty": 41610185.00844856
}
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getDifficulty&token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "difficulty": 41610185.00844856
}
?>
```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

$.ajax({
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getDifficulty&token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "difficulty": 41610185.00844856
}
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
}

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status',
         params: {'q': 'getDifficulty', 'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "difficulty": 41610185.00844856
}
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status',
                  params={'q': 'getDifficulty', 'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "difficulty": 41610185.00844856
}
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getDifficulty&token=<TOKEN>");
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
    "difficulty": 41610185.00844856
}
```

*Get current difficulty for the blockchain.*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|q|query|String|True|Please use `getDifficulty` as value|
|token|query|String|True|Token obtained from the ChainRider service|

|Response|
|-----|

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[BlockchainDifficultyObject](#schemeblockchaindifficultyobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

## Best Block hash

<h3 id="getBlockchainBestBlock">GET /status</h3>

<a id="opIdGetBlockchainBestBlock"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getBestBlockHash&token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
{
    "bestblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getBestBlockHash&token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "bestblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
?>
```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

$.ajax({
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getBestBlockHash&token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "bestblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
}

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status',
         params: {'q': 'getBestBlockHash', 'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "bestblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status',
                  params={'q': 'getBestBlockHash', 'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "bestblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getBestBlockHash&token=<TOKEN>");
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
    "bestblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
```

*Get best block hash for the blockchain.*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|q|query|String|True|Please use `getBestBlockHash` as value|
|token|query|String|True|Token obtained from the ChainRider service|

|Response|
|-----|

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[BlockchainBestBlockObject](#schemeblockchainbestblockobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

## Last Block hash

<h3 id="getBlockchainLastBlock">GET /status</h3>

<a id="opIdGetBlockchainLastBlock"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getLastBlockHash&token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
{
    "syncTipHash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5",
    "lastblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getLastBlockHash&token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "syncTipHash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5",
    "lastblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
?>
```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

$.ajax({
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getLastBlockHash&token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "syncTipHash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5",
    "lastblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
}

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status',
         params: {'q': 'getLastBlockHash', 'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "syncTipHash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5",
    "lastblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status',
                  params={'q': 'getLastBlockHash', 'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "syncTipHash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5",
    "lastblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/status?q=getLastBlockHash&token=<TOKEN>");
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
    "syncTipHash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5",
    "lastblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
```

*Get last block hash for the blockchain.*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|q|query|String|True|Please use `getLastBlockHash` as value|
|token|query|String|True|Token obtained from the ChainRider service|

|Response|
|-----|

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[BlockchainLastBlockObject](#schemeblockchainlastblockobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

## Blockchain Data Sync status

<h3 id="getBlockchainDataSync">GET /sync</h3>

<a id="opIdGetBlockchainDataSync"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/sync?token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
{
    "status":"finished",
    "blockChainHeight":855511,
    "syncPercentage":100,
    "height":855511,
    "error":null,
    "type":"bitcore node"
}
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/sync?token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "status":"finished",
    "blockChainHeight":855511,
    "syncPercentage":100,
    "height":855511,
    "error":null,
    "type":"bitcore node"
}
?>
```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

$.ajax({
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/sync?token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "status":"finished",
    "blockChainHeight":855511,
    "syncPercentage":100,
    "height":855511,
    "error":null,
    "type":"bitcore node"
}
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
}

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/sync',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "status":"finished",
    "blockChainHeight":855511,
    "syncPercentage":100,
    "height":855511,
    "error":null,
    "type":"bitcore node"
}
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/sync',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "status":"finished",
    "blockChainHeight":855511,
    "syncPercentage":100,
    "height":855511,
    "error":null,
    "type":"bitcore node"
}
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/sync?token=<TOKEN>");
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
    "status":"finished",
    "blockChainHeight":855511,
    "syncPercentage":100,
    "height":855511,
    "error":null,
    "type":"bitcore node"
}
```

*Get blockchain data sync status*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|token|query|String|True|Token obtained from the ChainRider service|

|Response|
|-----|

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[BlockchainDataSyncObject](#schemeblockchaindatasyncobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

## Budget Proposals

<h3 id="getBudgetProposals">GET /listproposal</h3>

<a id="opIdGetBudgetProposals"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/listproposal?token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
[
    {
        "Hash":"83b86bb19438144468576a257e312e5e674e778a47990c6af6338a3f92536302",
        "DataObject":
        {
            "end_epoch":1526652235,
            "name":"DASH-Venezuela-13-cities-1600-people",
            "payment_address":"Xfm6qvS2ugxL9u1V64SQeqbztYjqNU1qqx",
            "payment_amount":337,
            "start_epoch":1524076755,
            "type":1,
            "url":"https://www.dashcentral.org/p/DASH-Venezuela-13-cities-1600-people"
        },
        "AbsoluteYesCount":69,
        "YesCount":88,
        "NoCount":19,
        "AbstainCount":0
    },
    {
        "Hash":"9de1ad25b9e5e329ff53fc7fc5a2dadb817d1b84bf4578b152f91b931fde9208",
        "DataObject":
        {
            "end_epoch":1518714343,
            "name":"DashRed-Dec2017-Feb2018",
            "payment_address":"XxJLNc5eharc5BtKLTCrZGTXhQaUiQzDws",
            "payment_amount":36,
            "start_epoch":1510987903,
            "type":1,
            "url":"https://www.dashcentral.org/p/DashRed-Dec2017-Feb2018"
        },
        "AbsoluteYesCount":250,
        "YesCount":318,
        "NoCount":68,
        "AbstainCount":15
    }
]
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/listproposal?token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
[
    {
        "Hash":"83b86bb19438144468576a257e312e5e674e778a47990c6af6338a3f92536302",
        "DataObject":
        {
            "end_epoch":1526652235,
            "name":"DASH-Venezuela-13-cities-1600-people",
            "payment_address":"Xfm6qvS2ugxL9u1V64SQeqbztYjqNU1qqx",
            "payment_amount":337,
            "start_epoch":1524076755,
            "type":1,
            "url":"https://www.dashcentral.org/p/DASH-Venezuela-13-cities-1600-people"
        },
        "AbsoluteYesCount":69,
        "YesCount":88,
        "NoCount":19,
        "AbstainCount":0
    },
    {
        "Hash":"9de1ad25b9e5e329ff53fc7fc5a2dadb817d1b84bf4578b152f91b931fde9208",
        "DataObject":
        {
            "end_epoch":1518714343,
            "name":"DashRed-Dec2017-Feb2018",
            "payment_address":"XxJLNc5eharc5BtKLTCrZGTXhQaUiQzDws",
            "payment_amount":36,
            "start_epoch":1510987903,
            "type":1,
            "url":"https://www.dashcentral.org/p/DashRed-Dec2017-Feb2018"
        },
        "AbsoluteYesCount":250,
        "YesCount":318,
        "NoCount":68,
        "AbstainCount":15
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
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/listproposal?token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
[
    {
        "Hash":"83b86bb19438144468576a257e312e5e674e778a47990c6af6338a3f92536302",
        "DataObject":
        {
            "end_epoch":1526652235,
            "name":"DASH-Venezuela-13-cities-1600-people",
            "payment_address":"Xfm6qvS2ugxL9u1V64SQeqbztYjqNU1qqx",
            "payment_amount":337,
            "start_epoch":1524076755,
            "type":1,
            "url":"https://www.dashcentral.org/p/DASH-Venezuela-13-cities-1600-people"
        },
        "AbsoluteYesCount":69,
        "YesCount":88,
        "NoCount":19,
        "AbstainCount":0
    },
    {
        "Hash":"9de1ad25b9e5e329ff53fc7fc5a2dadb817d1b84bf4578b152f91b931fde9208",
        "DataObject":
        {
            "end_epoch":1518714343,
            "name":"DashRed-Dec2017-Feb2018",
            "payment_address":"XxJLNc5eharc5BtKLTCrZGTXhQaUiQzDws",
            "payment_amount":36,
            "start_epoch":1510987903,
            "type":1,
            "url":"https://www.dashcentral.org/p/DashRed-Dec2017-Feb2018"
        },
        "AbsoluteYesCount":250,
        "YesCount":318,
        "NoCount":68,
        "AbstainCount":15
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

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/listproposal',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
[
    {
        "Hash":"83b86bb19438144468576a257e312e5e674e778a47990c6af6338a3f92536302",
        "DataObject":
        {
            "end_epoch":1526652235,
            "name":"DASH-Venezuela-13-cities-1600-people",
            "payment_address":"Xfm6qvS2ugxL9u1V64SQeqbztYjqNU1qqx",
            "payment_amount":337,
            "start_epoch":1524076755,
            "type":1,
            "url":"https://www.dashcentral.org/p/DASH-Venezuela-13-cities-1600-people"
        },
        "AbsoluteYesCount":69,
        "YesCount":88,
        "NoCount":19,
        "AbstainCount":0
    },
    {
        "Hash":"9de1ad25b9e5e329ff53fc7fc5a2dadb817d1b84bf4578b152f91b931fde9208",
        "DataObject":
        {
            "end_epoch":1518714343,
            "name":"DashRed-Dec2017-Feb2018",
            "payment_address":"XxJLNc5eharc5BtKLTCrZGTXhQaUiQzDws",
            "payment_amount":36,
            "start_epoch":1510987903,
            "type":1,
            "url":"https://www.dashcentral.org/p/DashRed-Dec2017-Feb2018"
        },
        "AbsoluteYesCount":250,
        "YesCount":318,
        "NoCount":68,
        "AbstainCount":15
    }
]
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/listproposal',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
[
    {
        "Hash":"83b86bb19438144468576a257e312e5e674e778a47990c6af6338a3f92536302",
        "DataObject":
        {
            "end_epoch":1526652235,
            "name":"DASH-Venezuela-13-cities-1600-people",
            "payment_address":"Xfm6qvS2ugxL9u1V64SQeqbztYjqNU1qqx",
            "payment_amount":337,
            "start_epoch":1524076755,
            "type":1,
            "url":"https://www.dashcentral.org/p/DASH-Venezuela-13-cities-1600-people"
        },
        "AbsoluteYesCount":69,
        "YesCount":88,
        "NoCount":19,
        "AbstainCount":0
    },
    {
        "Hash":"9de1ad25b9e5e329ff53fc7fc5a2dadb817d1b84bf4578b152f91b931fde9208",
        "DataObject":
        {
            "end_epoch":1518714343,
            "name":"DashRed-Dec2017-Feb2018",
            "payment_address":"XxJLNc5eharc5BtKLTCrZGTXhQaUiQzDws",
            "payment_amount":36,
            "start_epoch":1510987903,
            "type":1,
            "url":"https://www.dashcentral.org/p/DashRed-Dec2017-Feb2018"
        },
        "AbsoluteYesCount":250,
        "YesCount":318,
        "NoCount":68,
        "AbstainCount":15
    }
]
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/listproposal?token=<TOKEN>");
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
        "Hash":"83b86bb19438144468576a257e312e5e674e778a47990c6af6338a3f92536302",
        "DataObject":
        {
            "end_epoch":1526652235,
            "name":"DASH-Venezuela-13-cities-1600-people",
            "payment_address":"Xfm6qvS2ugxL9u1V64SQeqbztYjqNU1qqx",
            "payment_amount":337,
            "start_epoch":1524076755,
            "type":1,
            "url":"https://www.dashcentral.org/p/DASH-Venezuela-13-cities-1600-people"
        },
        "AbsoluteYesCount":69,
        "YesCount":88,
        "NoCount":19,
        "AbstainCount":0
    },
    {
        "Hash":"9de1ad25b9e5e329ff53fc7fc5a2dadb817d1b84bf4578b152f91b931fde9208",
        "DataObject":
        {
            "end_epoch":1518714343,
            "name":"DashRed-Dec2017-Feb2018",
            "payment_address":"XxJLNc5eharc5BtKLTCrZGTXhQaUiQzDws",
            "payment_amount":36,
            "start_epoch":1510987903,
            "type":1,
            "url":"https://www.dashcentral.org/p/DashRed-Dec2017-Feb2018"
        },
        "AbsoluteYesCount":250,
        "YesCount":318,
        "NoCount":68,
        "AbstainCount":15
    }
]
```

*List budget proposals for a blockchain*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|token|query|String|True|Token obtained from the ChainRider service|

|Response|
|-----|

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Array [BlockchainProposalsObject](#schemeblockchainproposalsobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

## Budget Proposal by hash

<h3 id="getBudgetProposal">GET /getproposal/< proposal_hash > </h3>

<a id="opIdGetBudgetProposal"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/getproposal/<PROPOSAL_HASH>?token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
[
    {
        "Hash":"83b86bb19438144468576a257e312e5e674e778a47990c6af6338a3f92536302",
        "CollateralHash":"329f3802ebdad3088668f837ad74ab22e8853c03bf2ed15440d4108115d531b8",
        "DataHex":"5b5b2270726f706f73616c222c7b22656e645f65706f6368223a313532363635323233352c226e616d65223a22444153482d56656e657a75656c612d31332d6369746965732d313630302d70656f706c65222c227061796d656e745f61646472657373223a2258666d36717653327567784c39753156363453516571627a74596a714e5531717178222c227061796d656e745f616d6f756e74223a3333372c2273746172745f65706f6368223a313532343037363735352c2274797065223a312c2275726c223a2268747470733a2f2f7777772e6461736863656e7472616c2e6f72672f702f444153482d56656e657a75656c612d31332d6369746965732d313630302d70656f706c65227d5d5d",
        "DataObject":
        {
            "end_epoch":1526652235,
            "name":"DASH-Venezuela-13-cities-1600-people",
            "payment_address":"Xfm6qvS2ugxL9u1V64SQeqbztYjqNU1qqx",
            "payment_amount":337,
            "start_epoch":1524076755,
            "type":1,
            "url":"https://www.dashcentral.org/p/DASH-Venezuela-13-cities-1600-people"
        },
        "CreationTime":1523910440,
        "FundingResult":
        {
            "AbsoluteYesCount":60,
            "YesCount":89,
            "NoCount":29,
            "AbstainCount":0
        },
        "ValidResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        },
        "DeleteResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        },
        "EndorsedResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        }
    }
]
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/getproposal/<PROPOSAL_HASH>?token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
[
    {
        "Hash":"83b86bb19438144468576a257e312e5e674e778a47990c6af6338a3f92536302",
        "CollateralHash":"329f3802ebdad3088668f837ad74ab22e8853c03bf2ed15440d4108115d531b8",
        "DataHex":"5b5b2270726f706f73616c222c7b22656e645f65706f6368223a313532363635323233352c226e616d65223a22444153482d56656e657a75656c612d31332d6369746965732d313630302d70656f706c65222c227061796d656e745f61646472657373223a2258666d36717653327567784c39753156363453516571627a74596a714e5531717178222c227061796d656e745f616d6f756e74223a3333372c2273746172745f65706f6368223a313532343037363735352c2274797065223a312c2275726c223a2268747470733a2f2f7777772e6461736863656e7472616c2e6f72672f702f444153482d56656e657a75656c612d31332d6369746965732d313630302d70656f706c65227d5d5d",
        "DataObject":
        {
            "end_epoch":1526652235,
            "name":"DASH-Venezuela-13-cities-1600-people",
            "payment_address":"Xfm6qvS2ugxL9u1V64SQeqbztYjqNU1qqx",
            "payment_amount":337,
            "start_epoch":1524076755,
            "type":1,
            "url":"https://www.dashcentral.org/p/DASH-Venezuela-13-cities-1600-people"
        },
        "CreationTime":1523910440,
        "FundingResult":
        {
            "AbsoluteYesCount":60,
            "YesCount":89,
            "NoCount":29,
            "AbstainCount":0
        },
        "ValidResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        },
        "DeleteResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        },
        "EndorsedResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        }
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
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/getproposal/<PROPOSAL_HASH>?token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
[
    {
        "Hash":"83b86bb19438144468576a257e312e5e674e778a47990c6af6338a3f92536302",
        "CollateralHash":"329f3802ebdad3088668f837ad74ab22e8853c03bf2ed15440d4108115d531b8",
        "DataHex":"5b5b2270726f706f73616c222c7b22656e645f65706f6368223a313532363635323233352c226e616d65223a22444153482d56656e657a75656c612d31332d6369746965732d313630302d70656f706c65222c227061796d656e745f61646472657373223a2258666d36717653327567784c39753156363453516571627a74596a714e5531717178222c227061796d656e745f616d6f756e74223a3333372c2273746172745f65706f6368223a313532343037363735352c2274797065223a312c2275726c223a2268747470733a2f2f7777772e6461736863656e7472616c2e6f72672f702f444153482d56656e657a75656c612d31332d6369746965732d313630302d70656f706c65227d5d5d",
        "DataObject":
        {
            "end_epoch":1526652235,
            "name":"DASH-Venezuela-13-cities-1600-people",
            "payment_address":"Xfm6qvS2ugxL9u1V64SQeqbztYjqNU1qqx",
            "payment_amount":337,
            "start_epoch":1524076755,
            "type":1,
            "url":"https://www.dashcentral.org/p/DASH-Venezuela-13-cities-1600-people"
        },
        "CreationTime":1523910440,
        "FundingResult":
        {
            "AbsoluteYesCount":60,
            "YesCount":89,
            "NoCount":29,
            "AbstainCount":0
        },
        "ValidResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        },
        "DeleteResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        },
        "EndorsedResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        }
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

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/getproposal/<PROPOSAL_HASH>',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
[
    {
        "Hash":"83b86bb19438144468576a257e312e5e674e778a47990c6af6338a3f92536302",
        "CollateralHash":"329f3802ebdad3088668f837ad74ab22e8853c03bf2ed15440d4108115d531b8",
        "DataHex":"5b5b2270726f706f73616c222c7b22656e645f65706f6368223a313532363635323233352c226e616d65223a22444153482d56656e657a75656c612d31332d6369746965732d313630302d70656f706c65222c227061796d656e745f61646472657373223a2258666d36717653327567784c39753156363453516571627a74596a714e5531717178222c227061796d656e745f616d6f756e74223a3333372c2273746172745f65706f6368223a313532343037363735352c2274797065223a312c2275726c223a2268747470733a2f2f7777772e6461736863656e7472616c2e6f72672f702f444153482d56656e657a75656c612d31332d6369746965732d313630302d70656f706c65227d5d5d",
        "DataObject":
        {
            "end_epoch":1526652235,
            "name":"DASH-Venezuela-13-cities-1600-people",
            "payment_address":"Xfm6qvS2ugxL9u1V64SQeqbztYjqNU1qqx",
            "payment_amount":337,
            "start_epoch":1524076755,
            "type":1,
            "url":"https://www.dashcentral.org/p/DASH-Venezuela-13-cities-1600-people"
        },
        "CreationTime":1523910440,
        "FundingResult":
        {
            "AbsoluteYesCount":60,
            "YesCount":89,
            "NoCount":29,
            "AbstainCount":0
        },
        "ValidResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        },
        "DeleteResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        },
        "EndorsedResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        }
    }
]
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/getproposal/<PROPOSAL_HASH>',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
[
    {
        "Hash":"83b86bb19438144468576a257e312e5e674e778a47990c6af6338a3f92536302",
        "CollateralHash":"329f3802ebdad3088668f837ad74ab22e8853c03bf2ed15440d4108115d531b8",
        "DataHex":"5b5b2270726f706f73616c222c7b22656e645f65706f6368223a313532363635323233352c226e616d65223a22444153482d56656e657a75656c612d31332d6369746965732d313630302d70656f706c65222c227061796d656e745f61646472657373223a2258666d36717653327567784c39753156363453516571627a74596a714e5531717178222c227061796d656e745f616d6f756e74223a3333372c2273746172745f65706f6368223a313532343037363735352c2274797065223a312c2275726c223a2268747470733a2f2f7777772e6461736863656e7472616c2e6f72672f702f444153482d56656e657a75656c612d31332d6369746965732d313630302d70656f706c65227d5d5d",
        "DataObject":
        {
            "end_epoch":1526652235,
            "name":"DASH-Venezuela-13-cities-1600-people",
            "payment_address":"Xfm6qvS2ugxL9u1V64SQeqbztYjqNU1qqx",
            "payment_amount":337,
            "start_epoch":1524076755,
            "type":1,
            "url":"https://www.dashcentral.org/p/DASH-Venezuela-13-cities-1600-people"
        },
        "CreationTime":1523910440,
        "FundingResult":
        {
            "AbsoluteYesCount":60,
            "YesCount":89,
            "NoCount":29,
            "AbstainCount":0
        },
        "ValidResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        },
        "DeleteResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        },
        "EndorsedResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        }
    }
]
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/getproposal/<PROPOSAL_HASH>?token=<TOKEN>");
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
        "Hash":"83b86bb19438144468576a257e312e5e674e778a47990c6af6338a3f92536302",
        "CollateralHash":"329f3802ebdad3088668f837ad74ab22e8853c03bf2ed15440d4108115d531b8",
        "DataHex":"5b5b2270726f706f73616c222c7b22656e645f65706f6368223a313532363635323233352c226e616d65223a22444153482d56656e657a75656c612d31332d6369746965732d313630302d70656f706c65222c227061796d656e745f61646472657373223a2258666d36717653327567784c39753156363453516571627a74596a714e5531717178222c227061796d656e745f616d6f756e74223a3333372c2273746172745f65706f6368223a313532343037363735352c2274797065223a312c2275726c223a2268747470733a2f2f7777772e6461736863656e7472616c2e6f72672f702f444153482d56656e657a75656c612d31332d6369746965732d313630302d70656f706c65227d5d5d",
        "DataObject":
        {
            "end_epoch":1526652235,
            "name":"DASH-Venezuela-13-cities-1600-people",
            "payment_address":"Xfm6qvS2ugxL9u1V64SQeqbztYjqNU1qqx",
            "payment_amount":337,
            "start_epoch":1524076755,
            "type":1,
            "url":"https://www.dashcentral.org/p/DASH-Venezuela-13-cities-1600-people"
        },
        "CreationTime":1523910440,
        "FundingResult":
        {
            "AbsoluteYesCount":60,
            "YesCount":89,
            "NoCount":29,
            "AbstainCount":0
        },
        "ValidResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        },
        "DeleteResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        },
        "EndorsedResult":
        {
            "AbsoluteYesCount":0,
            "YesCount":0,
            "NoCount":0,
            "AbstainCount":0
        }
    }
]
```

*Get budget proposal by proposal hash for a blockchain*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|proposal_hash|path|String|True|Hash of the proposal|
|token|query|String|True|Token obtained from the ChainRider service|


|Response|
|-----|

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[BlockchainProposalObject](#schemeblockchainproposalobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

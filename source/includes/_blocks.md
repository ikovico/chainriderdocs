# Block APIs

This set of APIs provides insight in the blockchain on block level.

## Block by hash

<h3 id="getBlockByHash">GET /block/< block_hash > </h3>

<a id="opIdGetBlockByHash"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/block/<BLOCK_HASH>?token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

// Response example
{
    "hash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
    "size":456,
    "height":855987,
    "version":536870912,
    "merkleroot":"13828491a5dad3b90e167cf0f8e1e94c8df7f2e45068c735e6e4b09fc7141efa",
    "tx":
    [
        "325f86ccdfb528c2302d851351f7ef81e4dd6c786ba140c0efc3983af9730e78",
        "559b49fadb483ef92ad58476bc39301e72f00b12943a0dd2423a7794d6f38f57"
    ],
    "time":1524120132,
    "nonce":1263333077,
    "bits":"19487ec7",
    "difficulty":59243927.02142496,
    "chainwork":"000000000000000000000000000000000000000000000623078cb7febf9ace37",
    "confirmations":8,
    "previousblockhash":"000000000000001c887b1eeab66dd72223a3f4979d38076eacec71d9480a5a01",
    "nextblockhash":"000000000000002ba9667962e9c010c7106998027ff956b27f48d991eb50dc59",
    "reward":"3.34559819",
    "isMainChain":true,
    "poolInfo":
    {
    }
}
```

```php
<?php
$URL = "https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/block/<BLOCK_HASH>?token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "hash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
    "size":456,
    "height":855987,
    "version":536870912,
    "merkleroot":"13828491a5dad3b90e167cf0f8e1e94c8df7f2e45068c735e6e4b09fc7141efa",
    "tx":
    [
        "325f86ccdfb528c2302d851351f7ef81e4dd6c786ba140c0efc3983af9730e78",
        "559b49fadb483ef92ad58476bc39301e72f00b12943a0dd2423a7794d6f38f57"
    ],
    "time":1524120132,
    "nonce":1263333077,
    "bits":"19487ec7",
    "difficulty":59243927.02142496,
    "chainwork":"000000000000000000000000000000000000000000000623078cb7febf9ace37",
    "confirmations":8,
    "previousblockhash":"000000000000001c887b1eeab66dd72223a3f4979d38076eacec71d9480a5a01",
    "nextblockhash":"000000000000002ba9667962e9c010c7106998027ff956b27f48d991eb50dc59",
    "reward":"3.34559819",
    "isMainChain":true,
    "poolInfo":
    {
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
  url: 'https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/block/<BLOCK_HASH>?token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "hash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
    "size":456,
    "height":855987,
    "version":536870912,
    "merkleroot":"13828491a5dad3b90e167cf0f8e1e94c8df7f2e45068c735e6e4b09fc7141efa",
    "tx":
    [
        "325f86ccdfb528c2302d851351f7ef81e4dd6c786ba140c0efc3983af9730e78",
        "559b49fadb483ef92ad58476bc39301e72f00b12943a0dd2423a7794d6f38f57"
    ],
    "time":1524120132,
    "nonce":1263333077,
    "bits":"19487ec7",
    "difficulty":59243927.02142496,
    "chainwork":"000000000000000000000000000000000000000000000623078cb7febf9ace37",
    "confirmations":8,
    "previousblockhash":"000000000000001c887b1eeab66dd72223a3f4979d38076eacec71d9480a5a01",
    "nextblockhash":"000000000000002ba9667962e9c010c7106998027ff956b27f48d991eb50dc59",
    "reward":"3.34559819",
    "isMainChain":true,
    "poolInfo":
    {
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

result = RestClient.get 'https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/block/<BLOCK_HASH>',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "hash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
    "size":456,
    "height":855987,
    "version":536870912,
    "merkleroot":"13828491a5dad3b90e167cf0f8e1e94c8df7f2e45068c735e6e4b09fc7141efa",
    "tx":
    [
        "325f86ccdfb528c2302d851351f7ef81e4dd6c786ba140c0efc3983af9730e78",
        "559b49fadb483ef92ad58476bc39301e72f00b12943a0dd2423a7794d6f38f57"
    ],
    "time":1524120132,
    "nonce":1263333077,
    "bits":"19487ec7",
    "difficulty":59243927.02142496,
    "chainwork":"000000000000000000000000000000000000000000000623078cb7febf9ace37",
    "confirmations":8,
    "previousblockhash":"000000000000001c887b1eeab66dd72223a3f4979d38076eacec71d9480a5a01",
    "nextblockhash":"000000000000002ba9667962e9c010c7106998027ff956b27f48d991eb50dc59",
    "reward":"3.34559819",
    "isMainChain":true,
    "poolInfo":
    {
    }
}
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/block/<BLOCK_HASH>',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "hash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
    "size":456,
    "height":855987,
    "version":536870912,
    "merkleroot":"13828491a5dad3b90e167cf0f8e1e94c8df7f2e45068c735e6e4b09fc7141efa",
    "tx":
    [
        "325f86ccdfb528c2302d851351f7ef81e4dd6c786ba140c0efc3983af9730e78",
        "559b49fadb483ef92ad58476bc39301e72f00b12943a0dd2423a7794d6f38f57"
    ],
    "time":1524120132,
    "nonce":1263333077,
    "bits":"19487ec7",
    "difficulty":59243927.02142496,
    "chainwork":"000000000000000000000000000000000000000000000623078cb7febf9ace37",
    "confirmations":8,
    "previousblockhash":"000000000000001c887b1eeab66dd72223a3f4979d38076eacec71d9480a5a01",
    "nextblockhash":"000000000000002ba9667962e9c010c7106998027ff956b27f48d991eb50dc59",
    "reward":"3.34559819",
    "isMainChain":true,
    "poolInfo":
    {
    }
}
```

```java
URL obj = new URL("https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/block/<BLOCK_HASH>?token=<TOKEN>");
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
    "hash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
    "size":456,
    "height":855987,
    "version":536870912,
    "merkleroot":"13828491a5dad3b90e167cf0f8e1e94c8df7f2e45068c735e6e4b09fc7141efa",
    "tx":
    [
        "325f86ccdfb528c2302d851351f7ef81e4dd6c786ba140c0efc3983af9730e78",
        "559b49fadb483ef92ad58476bc39301e72f00b12943a0dd2423a7794d6f38f57"
    ],
    "time":1524120132,
    "nonce":1263333077,
    "bits":"19487ec7",
    "difficulty":59243927.02142496,
    "chainwork":"000000000000000000000000000000000000000000000623078cb7febf9ace37",
    "confirmations":8,
    "previousblockhash":"000000000000001c887b1eeab66dd72223a3f4979d38076eacec71d9480a5a01",
    "nextblockhash":"000000000000002ba9667962e9c010c7106998027ff956b27f48d991eb50dc59",
    "reward":"3.34559819",
    "isMainChain":true,
    "poolInfo":
    {
    }
}
```

*Get Block by hash*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|block_hash|path|String|True|Hash of the block|
|token|query|String|True|Token obtained from the ChainRider service|


|Response|
|-----|

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[BlockObject](#schemeblockobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

## Block hash by index

<h3 id="getBlockByIndex">GET /blockindex/< block_index > </h3>

<a id="opIdGetBlockByIndex"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/blockindex/<BLOCK_INDEX>?token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

// Response example
{
    "blockHash":"0000000000000023d9d8fefa79adbad2df8cb0b61f7cb5c591f56d719f108159"
}
```

```php
<?php
$URL = "https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/blockindex/<BLOCK_INDEX>?token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "blockHash":"0000000000000023d9d8fefa79adbad2df8cb0b61f7cb5c591f56d719f108159"
}
?>
```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

$.ajax({
  url: 'https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/blockindex/<BLOCK_INDEX>?token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "blockHash":"0000000000000023d9d8fefa79adbad2df8cb0b61f7cb5c591f56d719f108159"
}
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
}

result = RestClient.get 'https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/blockindex/<BLOCK_INDEX>',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "blockHash":"0000000000000023d9d8fefa79adbad2df8cb0b61f7cb5c591f56d719f108159"
}
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/blockindex/<BLOCK_INDEX>',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "blockHash":"0000000000000023d9d8fefa79adbad2df8cb0b61f7cb5c591f56d719f108159"
}
```

```java
URL obj = new URL("https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/blockindex/<BLOCK_INDEX>?token=<TOKEN>");
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
    "blockHash":"0000000000000023d9d8fefa79adbad2df8cb0b61f7cb5c591f56d719f108159"
}
```

*Get Block hash by index*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|block_index|path|String|True|Index of the block|
|token|query|String|True|Token obtained from the ChainRider service|


|Response|
|-----|

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[BlockHashObject](#schemeblockhashobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

## Raw Block by hash

<h3 id="getRawBlockByHash">GET /rawblock/< block_hash > </h3>

<a id="opIdGetRawBlockByHash"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/rawblock/<BLOCK_HASH>?token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

// Response example
{
    "rawblock":"00000020015a0a48d971ecac6e07389d97f4a32322d76db6ea1e7b881c00000000000000fa1e14c79fb0e4e635c76850e4f2f78d4ce9e1f8f07c160eb9d3daa591848213443ad85ac77e4819d5ee4c4b0201000000010000000000000000000000000000000000000000000000000000000000000000ffffffff1f03b30f0d04443ad85a08a4e19361340100000c2f436f696e4d696e65504c2f0000000002de59f909000000001976a914ee5c2e032d02f6f7b08fcc21e0025f0baeb056b088acd759f909000000001976a9149d0d46f36bc90aef04803b53fb5f76c5c4325ced88ac0000000001000000010786d7d9f0dd99cde3bb01064f7de00994b0a5cd0c2b9cb20a829772380b98ec010000006a47304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc012102cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738feffffff0240420f00000000001976a9148a3b9c1327cf24f99f57d95cb0ecf10342a6417c88acccfe4d00000000001976a914e99064a50c9756e7dcef5eff03c4e35fd927bbc088aca10f0d00"
}
```

```php
<?php
$URL = "https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/rawblock/<BLOCK_HASH>?token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "rawblock":"00000020015a0a48d971ecac6e07389d97f4a32322d76db6ea1e7b881c00000000000000fa1e14c79fb0e4e635c76850e4f2f78d4ce9e1f8f07c160eb9d3daa591848213443ad85ac77e4819d5ee4c4b0201000000010000000000000000000000000000000000000000000000000000000000000000ffffffff1f03b30f0d04443ad85a08a4e19361340100000c2f436f696e4d696e65504c2f0000000002de59f909000000001976a914ee5c2e032d02f6f7b08fcc21e0025f0baeb056b088acd759f909000000001976a9149d0d46f36bc90aef04803b53fb5f76c5c4325ced88ac0000000001000000010786d7d9f0dd99cde3bb01064f7de00994b0a5cd0c2b9cb20a829772380b98ec010000006a47304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc012102cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738feffffff0240420f00000000001976a9148a3b9c1327cf24f99f57d95cb0ecf10342a6417c88acccfe4d00000000001976a914e99064a50c9756e7dcef5eff03c4e35fd927bbc088aca10f0d00"
}
?>
```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

$.ajax({
  url: 'https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/rawblock/<BLOCK_HASH>?token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "rawblock":"00000020015a0a48d971ecac6e07389d97f4a32322d76db6ea1e7b881c00000000000000fa1e14c79fb0e4e635c76850e4f2f78d4ce9e1f8f07c160eb9d3daa591848213443ad85ac77e4819d5ee4c4b0201000000010000000000000000000000000000000000000000000000000000000000000000ffffffff1f03b30f0d04443ad85a08a4e19361340100000c2f436f696e4d696e65504c2f0000000002de59f909000000001976a914ee5c2e032d02f6f7b08fcc21e0025f0baeb056b088acd759f909000000001976a9149d0d46f36bc90aef04803b53fb5f76c5c4325ced88ac0000000001000000010786d7d9f0dd99cde3bb01064f7de00994b0a5cd0c2b9cb20a829772380b98ec010000006a47304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc012102cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738feffffff0240420f00000000001976a9148a3b9c1327cf24f99f57d95cb0ecf10342a6417c88acccfe4d00000000001976a914e99064a50c9756e7dcef5eff03c4e35fd927bbc088aca10f0d00"
}
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
}

result = RestClient.get 'https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/rawblock/<BLOCK_HASH>',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "rawblock":"00000020015a0a48d971ecac6e07389d97f4a32322d76db6ea1e7b881c00000000000000fa1e14c79fb0e4e635c76850e4f2f78d4ce9e1f8f07c160eb9d3daa591848213443ad85ac77e4819d5ee4c4b0201000000010000000000000000000000000000000000000000000000000000000000000000ffffffff1f03b30f0d04443ad85a08a4e19361340100000c2f436f696e4d696e65504c2f0000000002de59f909000000001976a914ee5c2e032d02f6f7b08fcc21e0025f0baeb056b088acd759f909000000001976a9149d0d46f36bc90aef04803b53fb5f76c5c4325ced88ac0000000001000000010786d7d9f0dd99cde3bb01064f7de00994b0a5cd0c2b9cb20a829772380b98ec010000006a47304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc012102cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738feffffff0240420f00000000001976a9148a3b9c1327cf24f99f57d95cb0ecf10342a6417c88acccfe4d00000000001976a914e99064a50c9756e7dcef5eff03c4e35fd927bbc088aca10f0d00"
}
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/rawblock/<BLOCK_HASH>',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "rawblock":"00000020015a0a48d971ecac6e07389d97f4a32322d76db6ea1e7b881c00000000000000fa1e14c79fb0e4e635c76850e4f2f78d4ce9e1f8f07c160eb9d3daa591848213443ad85ac77e4819d5ee4c4b0201000000010000000000000000000000000000000000000000000000000000000000000000ffffffff1f03b30f0d04443ad85a08a4e19361340100000c2f436f696e4d696e65504c2f0000000002de59f909000000001976a914ee5c2e032d02f6f7b08fcc21e0025f0baeb056b088acd759f909000000001976a9149d0d46f36bc90aef04803b53fb5f76c5c4325ced88ac0000000001000000010786d7d9f0dd99cde3bb01064f7de00994b0a5cd0c2b9cb20a829772380b98ec010000006a47304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc012102cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738feffffff0240420f00000000001976a9148a3b9c1327cf24f99f57d95cb0ecf10342a6417c88acccfe4d00000000001976a914e99064a50c9756e7dcef5eff03c4e35fd927bbc088aca10f0d00"
}
```

```java
URL obj = new URL("https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/rawblock/<BLOCK_HASH>?token=<TOKEN>");
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
    "rawblock":"00000020015a0a48d971ecac6e07389d97f4a32322d76db6ea1e7b881c00000000000000fa1e14c79fb0e4e635c76850e4f2f78d4ce9e1f8f07c160eb9d3daa591848213443ad85ac77e4819d5ee4c4b0201000000010000000000000000000000000000000000000000000000000000000000000000ffffffff1f03b30f0d04443ad85a08a4e19361340100000c2f436f696e4d696e65504c2f0000000002de59f909000000001976a914ee5c2e032d02f6f7b08fcc21e0025f0baeb056b088acd759f909000000001976a9149d0d46f36bc90aef04803b53fb5f76c5c4325ced88ac0000000001000000010786d7d9f0dd99cde3bb01064f7de00994b0a5cd0c2b9cb20a829772380b98ec010000006a47304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc012102cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738feffffff0240420f00000000001976a9148a3b9c1327cf24f99f57d95cb0ecf10342a6417c88acccfe4d00000000001976a914e99064a50c9756e7dcef5eff03c4e35fd927bbc088aca10f0d00"
}
```

*Get Raw Block by hash*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|block_hash|path|String|True|Hash of the block|
|token|query|String|True|Token obtained from the ChainRider service|


|Response|
|-----|

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[RawBlockObject](#schemerawblockobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

## Blocks by date

<h3 id="getBlocks">GET /blocks</h3>

<a id="opIdGetBlocks"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/blocks?token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

// Response example
{
    "blocks":
    [
        {
            "height":847606,
            "size":11315,
            "hash":"0000000000000011c33a17cffcee559bf18b38f479462c1426cabd71ce57d944",
            "time":1522799887,
            "txlength":21,
            "poolInfo":
            {
                "poolName":"AntMiner",
                "url":"https://bitmaintech.com/"
            }
        },
        {
            "height":847605,
            "size":28153,
            "hash":"000000000000001a28cb810f76361bea791e8d9fb6addda8928916dbb367b5ba",
            "time":1522799546,
            "txlength":14,
            "poolInfo":
            {
            }
        }
    ],
    "length":2,
    "pagination":
    {
        "next":"2018-04-04",
        "prev":"2018-04-02",
        "currentTs":1522799999,
        "current":"2018-04-03",
        "isToday":false,
        "more":true,
        "moreTs":1522800000
    }
}
```

```php
<?php
$URL = "https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/blocks?token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "blocks":
    [
        {
            "height":847606,
            "size":11315,
            "hash":"0000000000000011c33a17cffcee559bf18b38f479462c1426cabd71ce57d944",
            "time":1522799887,
            "txlength":21,
            "poolInfo":
            {
                "poolName":"AntMiner",
                "url":"https://bitmaintech.com/"
            }
        },
        {
            "height":847605,
            "size":28153,
            "hash":"000000000000001a28cb810f76361bea791e8d9fb6addda8928916dbb367b5ba",
            "time":1522799546,
            "txlength":14,
            "poolInfo":
            {
            }
        }
    ],
    "length":2,
    "pagination":
    {
        "next":"2018-04-04",
        "prev":"2018-04-02",
        "currentTs":1522799999,
        "current":"2018-04-03",
        "isToday":false,
        "more":true,
        "moreTs":1522800000
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
  url: 'https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/blocks?token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "blocks":
    [
        {
            "height":847606,
            "size":11315,
            "hash":"0000000000000011c33a17cffcee559bf18b38f479462c1426cabd71ce57d944",
            "time":1522799887,
            "txlength":21,
            "poolInfo":
            {
                "poolName":"AntMiner",
                "url":"https://bitmaintech.com/"
            }
        },
        {
            "height":847605,
            "size":28153,
            "hash":"000000000000001a28cb810f76361bea791e8d9fb6addda8928916dbb367b5ba",
            "time":1522799546,
            "txlength":14,
            "poolInfo":
            {
            }
        }
    ],
    "length":2,
    "pagination":
    {
        "next":"2018-04-04",
        "prev":"2018-04-02",
        "currentTs":1522799999,
        "current":"2018-04-03",
        "isToday":false,
        "more":true,
        "moreTs":1522800000
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

result = RestClient.get 'https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/blocks',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "blocks":
    [
        {
            "height":847606,
            "size":11315,
            "hash":"0000000000000011c33a17cffcee559bf18b38f479462c1426cabd71ce57d944",
            "time":1522799887,
            "txlength":21,
            "poolInfo":
            {
                "poolName":"AntMiner",
                "url":"https://bitmaintech.com/"
            }
        },
        {
            "height":847605,
            "size":28153,
            "hash":"000000000000001a28cb810f76361bea791e8d9fb6addda8928916dbb367b5ba",
            "time":1522799546,
            "txlength":14,
            "poolInfo":
            {
            }
        }
    ],
    "length":2,
    "pagination":
    {
        "next":"2018-04-04",
        "prev":"2018-04-02",
        "currentTs":1522799999,
        "current":"2018-04-03",
        "isToday":false,
        "more":true,
        "moreTs":1522800000
    }
}
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/blocks',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "blocks":
    [
        {
            "height":847606,
            "size":11315,
            "hash":"0000000000000011c33a17cffcee559bf18b38f479462c1426cabd71ce57d944",
            "time":1522799887,
            "txlength":21,
            "poolInfo":
            {
                "poolName":"AntMiner",
                "url":"https://bitmaintech.com/"
            }
        },
        {
            "height":847605,
            "size":28153,
            "hash":"000000000000001a28cb810f76361bea791e8d9fb6addda8928916dbb367b5ba",
            "time":1522799546,
            "txlength":14,
            "poolInfo":
            {
            }
        }
    ],
    "length":2,
    "pagination":
    {
        "next":"2018-04-04",
        "prev":"2018-04-02",
        "currentTs":1522799999,
        "current":"2018-04-03",
        "isToday":false,
        "more":true,
        "moreTs":1522800000
    }
}
```

```java
URL obj = new URL("https://api.chainrider.io.com/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/blocks?token=<TOKEN>");
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
    "blocks":
    [
        {
            "height":847606,
            "size":11315,
            "hash":"0000000000000011c33a17cffcee559bf18b38f479462c1426cabd71ce57d944",
            "time":1522799887,
            "txlength":21,
            "poolInfo":
            {
                "poolName":"AntMiner",
                "url":"https://bitmaintech.com/"
            }
        },
        {
            "height":847605,
            "size":28153,
            "hash":"000000000000001a28cb810f76361bea791e8d9fb6addda8928916dbb367b5ba",
            "time":1522799546,
            "txlength":14,
            "poolInfo":
            {
            }
        }
    ],
    "length":2,
    "pagination":
    {
        "next":"2018-04-04",
        "prev":"2018-04-02",
        "currentTs":1522799999,
        "current":"2018-04-03",
        "isToday":false,
        "more":true,
        "moreTs":1522800000
    }
}
```

*Get Blocks by date*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|limit|query|Intiger|False|Number of blocks to fetch, if omitted all blocks for specified day are returned|
|blockDate|query|Date YYYY-MM-DD |False|If omitted current day is returned|
|token|query|String|True|Token obtained from the ChainRider service|


|Response|
|-----|

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[BlocksPaginatedObject](#schemeblockspaginatedobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

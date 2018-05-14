# Transaction APIs

This set of APIs provides insight into the blockchain on a transaction level.

## Transaction by hash

<h3 id="getTransactionByHash">GET /tx/< tx_hash > </h3>

<a id="opIdGetTransactionByHash"></a>

*Get Transaction by hash*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|tx_hash|path|String|True|Hash of the transaction|
|token|query|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[TransactionObject](#schemetransactionobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<a id="divider"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/tx/<TX_HASH>?token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
{
    "txid":"9ba81f11c028e245c3628fd849907eca0b268520f31420140957593b1d1af04e",
    "version":1,
    "locktime":0,
    "vin":
    [
        {
            "txid":"f2d8b042224c57740e5e867e1b317ed450f85fb2bb69d77bafcf975ca95efbc0",
            "vout":1,
            "sequence":4294967295,
            "n":0,
            "scriptSig":
            {
                "hex":"483045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d012102dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228a",
                "asm":"3045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d[ALL] 02dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228a"
            },
            "addr":"Xoj4Qqx69FU3HbEidASNctRb7JpHDFG9s1",
            "valueSat":48225393,
            "value":0.48225393,
            "doubleSpentTxID":null
        },
        {
            "txid":"2c51645084cbe85a226e48692bb359b58341f49dd0529954a6ec90cdc05228ef",
            "vout":1,
            "sequence":4294967295,
            "n":1,
            "scriptSig":
            {
                "hex":"483045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd27210121023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2",
                "asm":"3045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd2721[ALL] 023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2"
            },
            "addr":"XiCLFh6yty5aeCRrB4H9BGCfvgcd61HtqH",
            "valueSat":410617230,
            "value":4.1061723,
            "doubleSpentTxID":null
        }
    ],
    "vout":
    [
        {
            "value":"4.58822623",
            "n":0,
            "scriptPubKey":
            {
                "hex":"76a914f9a86dca25067c5bf4a784aebd27080f3ec06f4c88ac",
                "asm":"OP_DUP OP_HASH160 f9a86dca25067c5bf4a784aebd27080f3ec06f4c OP_EQUALVERIFY OP_CHECKSIG",
                "addresses":
                [
                    "XySurfMBRDFFXhwWnLRYk6LPzESyamG9c4"
                ],
                "type":"pubkeyhash"
            },
            "spentTxId":"026cd76659232a3440028f1b706756546dfce29875a443a38db91b68d698e958",
            "spentIndex":0,
            "spentHeight":803642
        }
    ],
    "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
    "blockheight":801537,
    "confirmations":54480,
    "time":1515541051,
    "blocktime":1515541051,
    "valueOut":4.58822623,
    "size":340,
    "valueIn":4.58842623,
    "fees":0.0002,
    "txlock":false
}
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/tx/<TX_HASH>?token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "txid":"9ba81f11c028e245c3628fd849907eca0b268520f31420140957593b1d1af04e",
    "version":1,
    "locktime":0,
    "vin":
    [
        {
            "txid":"f2d8b042224c57740e5e867e1b317ed450f85fb2bb69d77bafcf975ca95efbc0",
            "vout":1,
            "sequence":4294967295,
            "n":0,
            "scriptSig":
            {
                "hex":"483045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d012102dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228a",
                "asm":"3045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d[ALL] 02dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228a"
            },
            "addr":"Xoj4Qqx69FU3HbEidASNctRb7JpHDFG9s1",
            "valueSat":48225393,
            "value":0.48225393,
            "doubleSpentTxID":null
        },
        {
            "txid":"2c51645084cbe85a226e48692bb359b58341f49dd0529954a6ec90cdc05228ef",
            "vout":1,
            "sequence":4294967295,
            "n":1,
            "scriptSig":
            {
                "hex":"483045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd27210121023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2",
                "asm":"3045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd2721[ALL] 023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2"
            },
            "addr":"XiCLFh6yty5aeCRrB4H9BGCfvgcd61HtqH",
            "valueSat":410617230,
            "value":4.1061723,
            "doubleSpentTxID":null
        }
    ],
    "vout":
    [
        {
            "value":"4.58822623",
            "n":0,
            "scriptPubKey":
            {
                "hex":"76a914f9a86dca25067c5bf4a784aebd27080f3ec06f4c88ac",
                "asm":"OP_DUP OP_HASH160 f9a86dca25067c5bf4a784aebd27080f3ec06f4c OP_EQUALVERIFY OP_CHECKSIG",
                "addresses":
                [
                    "XySurfMBRDFFXhwWnLRYk6LPzESyamG9c4"
                ],
                "type":"pubkeyhash"
            },
            "spentTxId":"026cd76659232a3440028f1b706756546dfce29875a443a38db91b68d698e958",
            "spentIndex":0,
            "spentHeight":803642
        }
    ],
    "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
    "blockheight":801537,
    "confirmations":54480,
    "time":1515541051,
    "blocktime":1515541051,
    "valueOut":4.58822623,
    "size":340,
    "valueIn":4.58842623,
    "fees":0.0002,
    "txlock":false
}
?>
```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

$.ajax({
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/tx/<TX_HASH>?token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "txid":"9ba81f11c028e245c3628fd849907eca0b268520f31420140957593b1d1af04e",
    "version":1,
    "locktime":0,
    "vin":
    [
        {
            "txid":"f2d8b042224c57740e5e867e1b317ed450f85fb2bb69d77bafcf975ca95efbc0",
            "vout":1,
            "sequence":4294967295,
            "n":0,
            "scriptSig":
            {
                "hex":"483045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d012102dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228a",
                "asm":"3045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d[ALL] 02dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228a"
            },
            "addr":"Xoj4Qqx69FU3HbEidASNctRb7JpHDFG9s1",
            "valueSat":48225393,
            "value":0.48225393,
            "doubleSpentTxID":null
        },
        {
            "txid":"2c51645084cbe85a226e48692bb359b58341f49dd0529954a6ec90cdc05228ef",
            "vout":1,
            "sequence":4294967295,
            "n":1,
            "scriptSig":
            {
                "hex":"483045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd27210121023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2",
                "asm":"3045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd2721[ALL] 023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2"
            },
            "addr":"XiCLFh6yty5aeCRrB4H9BGCfvgcd61HtqH",
            "valueSat":410617230,
            "value":4.1061723,
            "doubleSpentTxID":null
        }
    ],
    "vout":
    [
        {
            "value":"4.58822623",
            "n":0,
            "scriptPubKey":
            {
                "hex":"76a914f9a86dca25067c5bf4a784aebd27080f3ec06f4c88ac",
                "asm":"OP_DUP OP_HASH160 f9a86dca25067c5bf4a784aebd27080f3ec06f4c OP_EQUALVERIFY OP_CHECKSIG",
                "addresses":
                [
                    "XySurfMBRDFFXhwWnLRYk6LPzESyamG9c4"
                ],
                "type":"pubkeyhash"
            },
            "spentTxId":"026cd76659232a3440028f1b706756546dfce29875a443a38db91b68d698e958",
            "spentIndex":0,
            "spentHeight":803642
        }
    ],
    "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
    "blockheight":801537,
    "confirmations":54480,
    "time":1515541051,
    "blocktime":1515541051,
    "valueOut":4.58822623,
    "size":340,
    "valueIn":4.58842623,
    "fees":0.0002,
    "txlock":false
}
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
}

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/tx/<TX_HASH>',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "txid":"9ba81f11c028e245c3628fd849907eca0b268520f31420140957593b1d1af04e",
    "version":1,
    "locktime":0,
    "vin":
    [
        {
            "txid":"f2d8b042224c57740e5e867e1b317ed450f85fb2bb69d77bafcf975ca95efbc0",
            "vout":1,
            "sequence":4294967295,
            "n":0,
            "scriptSig":
            {
                "hex":"483045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d012102dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228a",
                "asm":"3045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d[ALL] 02dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228a"
            },
            "addr":"Xoj4Qqx69FU3HbEidASNctRb7JpHDFG9s1",
            "valueSat":48225393,
            "value":0.48225393,
            "doubleSpentTxID":null
        },
        {
            "txid":"2c51645084cbe85a226e48692bb359b58341f49dd0529954a6ec90cdc05228ef",
            "vout":1,
            "sequence":4294967295,
            "n":1,
            "scriptSig":
            {
                "hex":"483045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd27210121023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2",
                "asm":"3045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd2721[ALL] 023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2"
            },
            "addr":"XiCLFh6yty5aeCRrB4H9BGCfvgcd61HtqH",
            "valueSat":410617230,
            "value":4.1061723,
            "doubleSpentTxID":null
        }
    ],
    "vout":
    [
        {
            "value":"4.58822623",
            "n":0,
            "scriptPubKey":
            {
                "hex":"76a914f9a86dca25067c5bf4a784aebd27080f3ec06f4c88ac",
                "asm":"OP_DUP OP_HASH160 f9a86dca25067c5bf4a784aebd27080f3ec06f4c OP_EQUALVERIFY OP_CHECKSIG",
                "addresses":
                [
                    "XySurfMBRDFFXhwWnLRYk6LPzESyamG9c4"
                ],
                "type":"pubkeyhash"
            },
            "spentTxId":"026cd76659232a3440028f1b706756546dfce29875a443a38db91b68d698e958",
            "spentIndex":0,
            "spentHeight":803642
        }
    ],
    "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
    "blockheight":801537,
    "confirmations":54480,
    "time":1515541051,
    "blocktime":1515541051,
    "valueOut":4.58822623,
    "size":340,
    "valueIn":4.58842623,
    "fees":0.0002,
    "txlock":false
}
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/tx/<TX_HASH>',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "txid":"9ba81f11c028e245c3628fd849907eca0b268520f31420140957593b1d1af04e",
    "version":1,
    "locktime":0,
    "vin":
    [
        {
            "txid":"f2d8b042224c57740e5e867e1b317ed450f85fb2bb69d77bafcf975ca95efbc0",
            "vout":1,
            "sequence":4294967295,
            "n":0,
            "scriptSig":
            {
                "hex":"483045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d012102dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228a",
                "asm":"3045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d[ALL] 02dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228a"
            },
            "addr":"Xoj4Qqx69FU3HbEidASNctRb7JpHDFG9s1",
            "valueSat":48225393,
            "value":0.48225393,
            "doubleSpentTxID":null
        },
        {
            "txid":"2c51645084cbe85a226e48692bb359b58341f49dd0529954a6ec90cdc05228ef",
            "vout":1,
            "sequence":4294967295,
            "n":1,
            "scriptSig":
            {
                "hex":"483045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd27210121023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2",
                "asm":"3045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd2721[ALL] 023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2"
            },
            "addr":"XiCLFh6yty5aeCRrB4H9BGCfvgcd61HtqH",
            "valueSat":410617230,
            "value":4.1061723,
            "doubleSpentTxID":null
        }
    ],
    "vout":
    [
        {
            "value":"4.58822623",
            "n":0,
            "scriptPubKey":
            {
                "hex":"76a914f9a86dca25067c5bf4a784aebd27080f3ec06f4c88ac",
                "asm":"OP_DUP OP_HASH160 f9a86dca25067c5bf4a784aebd27080f3ec06f4c OP_EQUALVERIFY OP_CHECKSIG",
                "addresses":
                [
                    "XySurfMBRDFFXhwWnLRYk6LPzESyamG9c4"
                ],
                "type":"pubkeyhash"
            },
            "spentTxId":"026cd76659232a3440028f1b706756546dfce29875a443a38db91b68d698e958",
            "spentIndex":0,
            "spentHeight":803642
        }
    ],
    "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
    "blockheight":801537,
    "confirmations":54480,
    "time":1515541051,
    "blocktime":1515541051,
    "valueOut":4.58822623,
    "size":340,
    "valueIn":4.58842623,
    "fees":0.0002,
    "txlock":false
}
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/tx/<TX_HASH>?token=<TOKEN>");
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
    "txid":"9ba81f11c028e245c3628fd849907eca0b268520f31420140957593b1d1af04e",
    "version":1,
    "locktime":0,
    "vin":
    [
        {
            "txid":"f2d8b042224c57740e5e867e1b317ed450f85fb2bb69d77bafcf975ca95efbc0",
            "vout":1,
            "sequence":4294967295,
            "n":0,
            "scriptSig":
            {
                "hex":"483045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d012102dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228a",
                "asm":"3045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d[ALL] 02dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228a"
            },
            "addr":"Xoj4Qqx69FU3HbEidASNctRb7JpHDFG9s1",
            "valueSat":48225393,
            "value":0.48225393,
            "doubleSpentTxID":null
        },
        {
            "txid":"2c51645084cbe85a226e48692bb359b58341f49dd0529954a6ec90cdc05228ef",
            "vout":1,
            "sequence":4294967295,
            "n":1,
            "scriptSig":
            {
                "hex":"483045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd27210121023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2",
                "asm":"3045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd2721[ALL] 023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2"
            },
            "addr":"XiCLFh6yty5aeCRrB4H9BGCfvgcd61HtqH",
            "valueSat":410617230,
            "value":4.1061723,
            "doubleSpentTxID":null
        }
    ],
    "vout":
    [
        {
            "value":"4.58822623",
            "n":0,
            "scriptPubKey":
            {
                "hex":"76a914f9a86dca25067c5bf4a784aebd27080f3ec06f4c88ac",
                "asm":"OP_DUP OP_HASH160 f9a86dca25067c5bf4a784aebd27080f3ec06f4c OP_EQUALVERIFY OP_CHECKSIG",
                "addresses":
                [
                    "XySurfMBRDFFXhwWnLRYk6LPzESyamG9c4"
                ],
                "type":"pubkeyhash"
            },
            "spentTxId":"026cd76659232a3440028f1b706756546dfce29875a443a38db91b68d698e958",
            "spentIndex":0,
            "spentHeight":803642
        }
    ],
    "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
    "blockheight":801537,
    "confirmations":54480,
    "time":1515541051,
    "blocktime":1515541051,
    "valueOut":4.58822623,
    "size":340,
    "valueIn":4.58842623,
    "fees":0.0002,
    "txlock":false
}
```

## Raw Transaction by hash

<h3 id="getRawTxByHash">GET /rawtx/< tx_hash > </h3>

<a id="opIdGetRawTxByHash"></a>

*Get Raw Transaction by hash*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|tx_hash|path|String|True|Hash of the transaction|
|token|query|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[RawTxObject](#schemerawtxobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<a id="divider"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/rawtx/<TX_HASH>?token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
{
    "rawtx":"0100000002c0fb5ea95c97cfaf7bd769bbb25ff850d47e311b7e865e0e74574c2242b0d8f2010000006b483045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d012102dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228affffffffef2852c0cd90eca6549952d09df44183b559b32b69486e225ae8cb845064512c010000006b483045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd27210121023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2ffffffff01df13591b000000001976a914f9a86dca25067c5bf4a784aebd27080f3ec06f4c88ac00000000"
}
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/rawtx/<TX_HASH>?token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "rawtx":"0100000002c0fb5ea95c97cfaf7bd769bbb25ff850d47e311b7e865e0e74574c2242b0d8f2010000006b483045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d012102dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228affffffffef2852c0cd90eca6549952d09df44183b559b32b69486e225ae8cb845064512c010000006b483045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd27210121023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2ffffffff01df13591b000000001976a914f9a86dca25067c5bf4a784aebd27080f3ec06f4c88ac00000000"
}
?>
```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

$.ajax({
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/rawtx/<TX_HASH>?token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "rawtx":"0100000002c0fb5ea95c97cfaf7bd769bbb25ff850d47e311b7e865e0e74574c2242b0d8f2010000006b483045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d012102dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228affffffffef2852c0cd90eca6549952d09df44183b559b32b69486e225ae8cb845064512c010000006b483045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd27210121023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2ffffffff01df13591b000000001976a914f9a86dca25067c5bf4a784aebd27080f3ec06f4c88ac00000000"
}
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
}

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/rawtx/<TX_HASH>',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "rawtx":"0100000002c0fb5ea95c97cfaf7bd769bbb25ff850d47e311b7e865e0e74574c2242b0d8f2010000006b483045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d012102dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228affffffffef2852c0cd90eca6549952d09df44183b559b32b69486e225ae8cb845064512c010000006b483045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd27210121023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2ffffffff01df13591b000000001976a914f9a86dca25067c5bf4a784aebd27080f3ec06f4c88ac00000000"
}
```

```python
import requests

headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
}

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/rawtx/<TX_HASH>',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "rawtx":"0100000002c0fb5ea95c97cfaf7bd769bbb25ff850d47e311b7e865e0e74574c2242b0d8f2010000006b483045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d012102dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228affffffffef2852c0cd90eca6549952d09df44183b559b32b69486e225ae8cb845064512c010000006b483045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd27210121023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2ffffffff01df13591b000000001976a914f9a86dca25067c5bf4a784aebd27080f3ec06f4c88ac00000000"
}
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/rawtx/<TX_HASH>?token=<TOKEN>");
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
    "rawtx":"0100000002c0fb5ea95c97cfaf7bd769bbb25ff850d47e311b7e865e0e74574c2242b0d8f2010000006b483045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d012102dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228affffffffef2852c0cd90eca6549952d09df44183b559b32b69486e225ae8cb845064512c010000006b483045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd27210121023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2ffffffff01df13591b000000001976a914f9a86dca25067c5bf4a784aebd27080f3ec06f4c88ac00000000"
}
```

## Transactions for Block

<h3 id="getTransactionsBlock">GET /txs</h3>

<a id="opIdGetTransactionsBlock"></a>

*Get Transactions for a Block*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|block|query|String|True|Block hash|
|token|query|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[TxBlockObject](#schemetxblockobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<a id="divider"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/txs?block=<BLOCK_HASH>&token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
{
    "pagesTotal":1,
    "txs":
    [
        {
            "txid":"325f86ccdfb528c2302d851351f7ef81e4dd6c786ba140c0efc3983af9730e78",
            "version":1,
            "locktime":0,
            "vin":
            [
                {
                    "coinbase":"03b30f0d04443ad85a08a4e19361340100000c2f436f696e4d696e65504c2f",
                    "sequence":0,
                    "n":0
                }
            ],
            "vout":
            [
                {
                    "value":"1.67336414",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a914ee5c2e032d02f6f7b08fcc21e0025f0baeb056b088ac",
                        "asm":"OP_DUP OP_HASH160 ee5c2e032d02f6f7b08fcc21e0025f0baeb056b0 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XxRB5fnF8KpB9jjRRb7M7pq4qtyL8xbUou"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                },
                {
                    "value":"1.67336407",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9149d0d46f36bc90aef04803b53fb5f76c5c4325ced88ac",
                        "asm":"OP_DUP OP_HASH160 9d0d46f36bc90aef04803b53fb5f76c5c4325ced OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xq1FptCQXMfmjfsN6QxYUeGhzCFm94TrQj"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                }
            ],
            "blockhash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
            "blockheight":855987,
            "confirmations":47,
            "time":1524120132,
            "blocktime":1524120132,
            "isCoinBase":true,
            "valueOut":3.34672821,
            "size":150,
            "txlock":false
        },
        {
            "txid":"559b49fadb483ef92ad58476bc39301e72f00b12943a0dd2423a7794d6f38f57",
            "version":1,
            "locktime":855969,
            "vin":
            [
                {
                    "txid":"ec980b387297820ab29c2b0ccda5b09409e07d4f0601bbe3cd99ddf0d9d78607",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc012102cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738",
                        "asm":"304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc[ALL] 02cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738"
                    },
                    "addr":"Xd5KDD6kjC2iyQGjWqZWi3HWoMqC92faUp",
                    "valueSat":6224500,
                    "value":0.062245,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.01000000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148a3b9c1327cf24f99f57d95cb0ecf10342a6417c88ac",
                        "asm":"OP_DUP OP_HASH160 8a3b9c1327cf24f99f57d95cb0ecf10342a6417c OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoHkVUhRtpQCWPTTH6veSuPrjFq3rdJv6b"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                },
                {
                    "value":"0.05111500",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a914e99064a50c9756e7dcef5eff03c4e35fd927bbc088ac",
                        "asm":"OP_DUP OP_HASH160 e99064a50c9756e7dcef5eff03c4e35fd927bbc0 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XwypFZWwD3Le91Smtw7shA52rQqFcoF3bv"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"dc2cc56bfc11d1afea9e1407923fe6879963b66de6f3069b59afd7f27f22f514",
                    "spentIndex":0,
                    "spentHeight":855991
                }
            ],
            "blockhash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
            "blockheight":855987,
            "confirmations":47,
            "time":1524120132,
            "blocktime":1524120132,
            "valueOut":0.061115,
            "size":225,
            "valueIn":0.062245,
            "fees":0.00113,
            "txlock":false
        }
    ]
}
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/txs?block=<BLOCK_HASH>&token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "pagesTotal":1,
    "txs":
    [
        {
            "txid":"325f86ccdfb528c2302d851351f7ef81e4dd6c786ba140c0efc3983af9730e78",
            "version":1,
            "locktime":0,
            "vin":
            [
                {
                    "coinbase":"03b30f0d04443ad85a08a4e19361340100000c2f436f696e4d696e65504c2f",
                    "sequence":0,
                    "n":0
                }
            ],
            "vout":
            [
                {
                    "value":"1.67336414",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a914ee5c2e032d02f6f7b08fcc21e0025f0baeb056b088ac",
                        "asm":"OP_DUP OP_HASH160 ee5c2e032d02f6f7b08fcc21e0025f0baeb056b0 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XxRB5fnF8KpB9jjRRb7M7pq4qtyL8xbUou"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                },
                {
                    "value":"1.67336407",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9149d0d46f36bc90aef04803b53fb5f76c5c4325ced88ac",
                        "asm":"OP_DUP OP_HASH160 9d0d46f36bc90aef04803b53fb5f76c5c4325ced OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xq1FptCQXMfmjfsN6QxYUeGhzCFm94TrQj"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                }
            ],
            "blockhash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
            "blockheight":855987,
            "confirmations":47,
            "time":1524120132,
            "blocktime":1524120132,
            "isCoinBase":true,
            "valueOut":3.34672821,
            "size":150,
            "txlock":false
        },
        {
            "txid":"559b49fadb483ef92ad58476bc39301e72f00b12943a0dd2423a7794d6f38f57",
            "version":1,
            "locktime":855969,
            "vin":
            [
                {
                    "txid":"ec980b387297820ab29c2b0ccda5b09409e07d4f0601bbe3cd99ddf0d9d78607",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc012102cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738",
                        "asm":"304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc[ALL] 02cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738"
                    },
                    "addr":"Xd5KDD6kjC2iyQGjWqZWi3HWoMqC92faUp",
                    "valueSat":6224500,
                    "value":0.062245,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.01000000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148a3b9c1327cf24f99f57d95cb0ecf10342a6417c88ac",
                        "asm":"OP_DUP OP_HASH160 8a3b9c1327cf24f99f57d95cb0ecf10342a6417c OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoHkVUhRtpQCWPTTH6veSuPrjFq3rdJv6b"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                },
                {
                    "value":"0.05111500",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a914e99064a50c9756e7dcef5eff03c4e35fd927bbc088ac",
                        "asm":"OP_DUP OP_HASH160 e99064a50c9756e7dcef5eff03c4e35fd927bbc0 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XwypFZWwD3Le91Smtw7shA52rQqFcoF3bv"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"dc2cc56bfc11d1afea9e1407923fe6879963b66de6f3069b59afd7f27f22f514",
                    "spentIndex":0,
                    "spentHeight":855991
                }
            ],
            "blockhash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
            "blockheight":855987,
            "confirmations":47,
            "time":1524120132,
            "blocktime":1524120132,
            "valueOut":0.061115,
            "size":225,
            "valueIn":0.062245,
            "fees":0.00113,
            "txlock":false
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
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/txs?block=<BLOCK_HASH>&token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "pagesTotal":1,
    "txs":
    [
        {
            "txid":"325f86ccdfb528c2302d851351f7ef81e4dd6c786ba140c0efc3983af9730e78",
            "version":1,
            "locktime":0,
            "vin":
            [
                {
                    "coinbase":"03b30f0d04443ad85a08a4e19361340100000c2f436f696e4d696e65504c2f",
                    "sequence":0,
                    "n":0
                }
            ],
            "vout":
            [
                {
                    "value":"1.67336414",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a914ee5c2e032d02f6f7b08fcc21e0025f0baeb056b088ac",
                        "asm":"OP_DUP OP_HASH160 ee5c2e032d02f6f7b08fcc21e0025f0baeb056b0 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XxRB5fnF8KpB9jjRRb7M7pq4qtyL8xbUou"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                },
                {
                    "value":"1.67336407",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9149d0d46f36bc90aef04803b53fb5f76c5c4325ced88ac",
                        "asm":"OP_DUP OP_HASH160 9d0d46f36bc90aef04803b53fb5f76c5c4325ced OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xq1FptCQXMfmjfsN6QxYUeGhzCFm94TrQj"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                }
            ],
            "blockhash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
            "blockheight":855987,
            "confirmations":47,
            "time":1524120132,
            "blocktime":1524120132,
            "isCoinBase":true,
            "valueOut":3.34672821,
            "size":150,
            "txlock":false
        },
        {
            "txid":"559b49fadb483ef92ad58476bc39301e72f00b12943a0dd2423a7794d6f38f57",
            "version":1,
            "locktime":855969,
            "vin":
            [
                {
                    "txid":"ec980b387297820ab29c2b0ccda5b09409e07d4f0601bbe3cd99ddf0d9d78607",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc012102cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738",
                        "asm":"304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc[ALL] 02cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738"
                    },
                    "addr":"Xd5KDD6kjC2iyQGjWqZWi3HWoMqC92faUp",
                    "valueSat":6224500,
                    "value":0.062245,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.01000000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148a3b9c1327cf24f99f57d95cb0ecf10342a6417c88ac",
                        "asm":"OP_DUP OP_HASH160 8a3b9c1327cf24f99f57d95cb0ecf10342a6417c OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoHkVUhRtpQCWPTTH6veSuPrjFq3rdJv6b"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                },
                {
                    "value":"0.05111500",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a914e99064a50c9756e7dcef5eff03c4e35fd927bbc088ac",
                        "asm":"OP_DUP OP_HASH160 e99064a50c9756e7dcef5eff03c4e35fd927bbc0 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XwypFZWwD3Le91Smtw7shA52rQqFcoF3bv"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"dc2cc56bfc11d1afea9e1407923fe6879963b66de6f3069b59afd7f27f22f514",
                    "spentIndex":0,
                    "spentHeight":855991
                }
            ],
            "blockhash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
            "blockheight":855987,
            "confirmations":47,
            "time":1524120132,
            "blocktime":1524120132,
            "valueOut":0.061115,
            "size":225,
            "valueIn":0.062245,
            "fees":0.00113,
            "txlock":false
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

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/txs',
         params: {'block': <BLOCK_HASH>, 'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "pagesTotal":1,
    "txs":
    [
        {
            "txid":"325f86ccdfb528c2302d851351f7ef81e4dd6c786ba140c0efc3983af9730e78",
            "version":1,
            "locktime":0,
            "vin":
            [
                {
                    "coinbase":"03b30f0d04443ad85a08a4e19361340100000c2f436f696e4d696e65504c2f",
                    "sequence":0,
                    "n":0
                }
            ],
            "vout":
            [
                {
                    "value":"1.67336414",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a914ee5c2e032d02f6f7b08fcc21e0025f0baeb056b088ac",
                        "asm":"OP_DUP OP_HASH160 ee5c2e032d02f6f7b08fcc21e0025f0baeb056b0 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XxRB5fnF8KpB9jjRRb7M7pq4qtyL8xbUou"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                },
                {
                    "value":"1.67336407",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9149d0d46f36bc90aef04803b53fb5f76c5c4325ced88ac",
                        "asm":"OP_DUP OP_HASH160 9d0d46f36bc90aef04803b53fb5f76c5c4325ced OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xq1FptCQXMfmjfsN6QxYUeGhzCFm94TrQj"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                }
            ],
            "blockhash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
            "blockheight":855987,
            "confirmations":47,
            "time":1524120132,
            "blocktime":1524120132,
            "isCoinBase":true,
            "valueOut":3.34672821,
            "size":150,
            "txlock":false
        },
        {
            "txid":"559b49fadb483ef92ad58476bc39301e72f00b12943a0dd2423a7794d6f38f57",
            "version":1,
            "locktime":855969,
            "vin":
            [
                {
                    "txid":"ec980b387297820ab29c2b0ccda5b09409e07d4f0601bbe3cd99ddf0d9d78607",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc012102cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738",
                        "asm":"304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc[ALL] 02cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738"
                    },
                    "addr":"Xd5KDD6kjC2iyQGjWqZWi3HWoMqC92faUp",
                    "valueSat":6224500,
                    "value":0.062245,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.01000000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148a3b9c1327cf24f99f57d95cb0ecf10342a6417c88ac",
                        "asm":"OP_DUP OP_HASH160 8a3b9c1327cf24f99f57d95cb0ecf10342a6417c OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoHkVUhRtpQCWPTTH6veSuPrjFq3rdJv6b"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                },
                {
                    "value":"0.05111500",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a914e99064a50c9756e7dcef5eff03c4e35fd927bbc088ac",
                        "asm":"OP_DUP OP_HASH160 e99064a50c9756e7dcef5eff03c4e35fd927bbc0 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XwypFZWwD3Le91Smtw7shA52rQqFcoF3bv"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"dc2cc56bfc11d1afea9e1407923fe6879963b66de6f3069b59afd7f27f22f514",
                    "spentIndex":0,
                    "spentHeight":855991
                }
            ],
            "blockhash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
            "blockheight":855987,
            "confirmations":47,
            "time":1524120132,
            "blocktime":1524120132,
            "valueOut":0.061115,
            "size":225,
            "valueIn":0.062245,
            "fees":0.00113,
            "txlock":false
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

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/txs',
                  params={'block': <BLOCK_HASH>, 'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "pagesTotal":1,
    "txs":
    [
        {
            "txid":"325f86ccdfb528c2302d851351f7ef81e4dd6c786ba140c0efc3983af9730e78",
            "version":1,
            "locktime":0,
            "vin":
            [
                {
                    "coinbase":"03b30f0d04443ad85a08a4e19361340100000c2f436f696e4d696e65504c2f",
                    "sequence":0,
                    "n":0
                }
            ],
            "vout":
            [
                {
                    "value":"1.67336414",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a914ee5c2e032d02f6f7b08fcc21e0025f0baeb056b088ac",
                        "asm":"OP_DUP OP_HASH160 ee5c2e032d02f6f7b08fcc21e0025f0baeb056b0 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XxRB5fnF8KpB9jjRRb7M7pq4qtyL8xbUou"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                },
                {
                    "value":"1.67336407",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9149d0d46f36bc90aef04803b53fb5f76c5c4325ced88ac",
                        "asm":"OP_DUP OP_HASH160 9d0d46f36bc90aef04803b53fb5f76c5c4325ced OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xq1FptCQXMfmjfsN6QxYUeGhzCFm94TrQj"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                }
            ],
            "blockhash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
            "blockheight":855987,
            "confirmations":47,
            "time":1524120132,
            "blocktime":1524120132,
            "isCoinBase":true,
            "valueOut":3.34672821,
            "size":150,
            "txlock":false
        },
        {
            "txid":"559b49fadb483ef92ad58476bc39301e72f00b12943a0dd2423a7794d6f38f57",
            "version":1,
            "locktime":855969,
            "vin":
            [
                {
                    "txid":"ec980b387297820ab29c2b0ccda5b09409e07d4f0601bbe3cd99ddf0d9d78607",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc012102cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738",
                        "asm":"304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc[ALL] 02cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738"
                    },
                    "addr":"Xd5KDD6kjC2iyQGjWqZWi3HWoMqC92faUp",
                    "valueSat":6224500,
                    "value":0.062245,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.01000000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148a3b9c1327cf24f99f57d95cb0ecf10342a6417c88ac",
                        "asm":"OP_DUP OP_HASH160 8a3b9c1327cf24f99f57d95cb0ecf10342a6417c OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoHkVUhRtpQCWPTTH6veSuPrjFq3rdJv6b"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                },
                {
                    "value":"0.05111500",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a914e99064a50c9756e7dcef5eff03c4e35fd927bbc088ac",
                        "asm":"OP_DUP OP_HASH160 e99064a50c9756e7dcef5eff03c4e35fd927bbc0 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XwypFZWwD3Le91Smtw7shA52rQqFcoF3bv"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"dc2cc56bfc11d1afea9e1407923fe6879963b66de6f3069b59afd7f27f22f514",
                    "spentIndex":0,
                    "spentHeight":855991
                }
            ],
            "blockhash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
            "blockheight":855987,
            "confirmations":47,
            "time":1524120132,
            "blocktime":1524120132,
            "valueOut":0.061115,
            "size":225,
            "valueIn":0.062245,
            "fees":0.00113,
            "txlock":false
        }
    ]
}
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/txs?block=<BLOCK_HASH>&token=<TOKEN>");
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
    "pagesTotal":1,
    "txs":
    [
        {
            "txid":"325f86ccdfb528c2302d851351f7ef81e4dd6c786ba140c0efc3983af9730e78",
            "version":1,
            "locktime":0,
            "vin":
            [
                {
                    "coinbase":"03b30f0d04443ad85a08a4e19361340100000c2f436f696e4d696e65504c2f",
                    "sequence":0,
                    "n":0
                }
            ],
            "vout":
            [
                {
                    "value":"1.67336414",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a914ee5c2e032d02f6f7b08fcc21e0025f0baeb056b088ac",
                        "asm":"OP_DUP OP_HASH160 ee5c2e032d02f6f7b08fcc21e0025f0baeb056b0 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XxRB5fnF8KpB9jjRRb7M7pq4qtyL8xbUou"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                },
                {
                    "value":"1.67336407",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9149d0d46f36bc90aef04803b53fb5f76c5c4325ced88ac",
                        "asm":"OP_DUP OP_HASH160 9d0d46f36bc90aef04803b53fb5f76c5c4325ced OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xq1FptCQXMfmjfsN6QxYUeGhzCFm94TrQj"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                }
            ],
            "blockhash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
            "blockheight":855987,
            "confirmations":47,
            "time":1524120132,
            "blocktime":1524120132,
            "isCoinBase":true,
            "valueOut":3.34672821,
            "size":150,
            "txlock":false
        },
        {
            "txid":"559b49fadb483ef92ad58476bc39301e72f00b12943a0dd2423a7794d6f38f57",
            "version":1,
            "locktime":855969,
            "vin":
            [
                {
                    "txid":"ec980b387297820ab29c2b0ccda5b09409e07d4f0601bbe3cd99ddf0d9d78607",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc012102cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738",
                        "asm":"304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc[ALL] 02cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738"
                    },
                    "addr":"Xd5KDD6kjC2iyQGjWqZWi3HWoMqC92faUp",
                    "valueSat":6224500,
                    "value":0.062245,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.01000000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148a3b9c1327cf24f99f57d95cb0ecf10342a6417c88ac",
                        "asm":"OP_DUP OP_HASH160 8a3b9c1327cf24f99f57d95cb0ecf10342a6417c OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoHkVUhRtpQCWPTTH6veSuPrjFq3rdJv6b"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":null,
                    "spentIndex":null,
                    "spentHeight":null
                },
                {
                    "value":"0.05111500",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a914e99064a50c9756e7dcef5eff03c4e35fd927bbc088ac",
                        "asm":"OP_DUP OP_HASH160 e99064a50c9756e7dcef5eff03c4e35fd927bbc0 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XwypFZWwD3Le91Smtw7shA52rQqFcoF3bv"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"dc2cc56bfc11d1afea9e1407923fe6879963b66de6f3069b59afd7f27f22f514",
                    "spentIndex":0,
                    "spentHeight":855991
                }
            ],
            "blockhash":"000000000000003d34c3254c70afb7ecefe0cb5952dfcc8b43f63c65f0054176",
            "blockheight":855987,
            "confirmations":47,
            "time":1524120132,
            "blocktime":1524120132,
            "valueOut":0.061115,
            "size":225,
            "valueIn":0.062245,
            "fees":0.00113,
            "txlock":false
        }
    ]
}
```

## Transactions for Address

<h3 id="getTransactionsAddress">GET /txs</h3>

<a id="opIdGetTransactionsAddress"></a>

*Get Transactions for an Address*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|address|query|String|True|Address string|
|token|query|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[TxAddressObject](#schemetxaddressobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<a id="divider"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/txs?address=<ADDRESS>&token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
{
    "pagesTotal":1,
    "txs":
    [
        {
            "txid":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
            "version":1,
            "locktime":801535,
            "vin":
            [
                {
                    "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb896495501210366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0",
                        "asm":"304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb8964955[ALL] 0366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0"
                    },
                    "addr":"XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA",
                    "valueSat":4339433988,
                    "value":43.39433988,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.52760000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9147d412940d1dce226cb39f9aade2b45a8139410c388ac",
                        "asm":"OP_DUP OP_HASH160 7d412940d1dce226cb39f9aade2b45a8139410c3 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xn78Mi21PMiHt9WP4L53jGM4YmFJW1Byt1"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"cbdad5342e7adf96653ebd0cb975c87c968d9a42183c6ca9f89a352f440bfe1f",
                    "spentIndex":1,
                    "spentHeight":819533
                },
                {
                    "value":"42.86671328",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9148c20711bed045fe94b1594bef74d1e70a122088388ac",
                        "asm":"OP_DUP OP_HASH160 8c20711bed045fe94b1594bef74d1e70a1220883 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoTmJD185yqptsbpB8P86iUDepNc7ew9dC"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"517ac0dcde42d24e1a9738ca2a3a74aea67a9f8a2eab1c64caa8b1efe08de0e9",
                    "spentIndex":0,
                    "spentHeight":801545
                }
            ],
            "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
            "blockheight":801537,
            "confirmations":54498,
            "time":1515541051,
            "blocktime":1515541051,
            "valueOut":43.39431328,
            "size":225,
            "valueIn":43.39433988,
            "fees":0.0000266,
            "txlock":false
        },
        {
            "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
            "version":1,
            "locktime":801405,
            "vin":
            [
                {
                    "txid":"ce2c051f45574c447cbb1508437acaf760e79236b7f86c97a15ff11d0ab8e33e",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e01210294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a",
                        "asm":"304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e[ALL] 0294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a"
                    },
                    "addr":"XnVQXrresaPrAA81qcYhCrHRpkAvDGixus",
                    "valueSat":4345623837,
                    "value":43.45623837,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.06187190",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148b82df11f146d6203ca9ce7a67e75f37444c408b88ac",
                        "asm":"OP_DUP OP_HASH160 8b82df11f146d6203ca9ce7a67e75f37444c408b OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoQWY27FwvCzyiLgpgxfDGHToBCehz8Dp4"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"a36a7ef65a34b1205142aad9f7e4a1cccb972c3e685d0e205174ff98c2f3ce07",
                    "spentIndex":0,
                    "spentHeight":801900
                },
                {
                    "value":"43.39433988",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a91469ddad658bc7e99ece553836f0139db1ea55c33988ac",
                        "asm":"OP_DUP OP_HASH160 69ddad658bc7e99ece553836f0139db1ea55c339 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
                    "spentIndex":0,
                    "spentHeight":801537
                }
            ],
            "blockhash":"000000000000001af3534c0f771f9342a02818821fe98dad10f309ae56855c86",
            "blockheight":801407,
            "confirmations":54628,
            "time":1515520337,
            "blocktime":1515520337,
            "valueOut":43.45621178,
            "size":225,
            "valueIn":43.45623837,
            "fees":0.00002659,
            "txlock":false
        }
    ]
}
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/txs?address=<ADDRESS>&token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "pagesTotal":1,
    "txs":
    [
        {
            "txid":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
            "version":1,
            "locktime":801535,
            "vin":
            [
                {
                    "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb896495501210366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0",
                        "asm":"304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb8964955[ALL] 0366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0"
                    },
                    "addr":"XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA",
                    "valueSat":4339433988,
                    "value":43.39433988,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.52760000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9147d412940d1dce226cb39f9aade2b45a8139410c388ac",
                        "asm":"OP_DUP OP_HASH160 7d412940d1dce226cb39f9aade2b45a8139410c3 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xn78Mi21PMiHt9WP4L53jGM4YmFJW1Byt1"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"cbdad5342e7adf96653ebd0cb975c87c968d9a42183c6ca9f89a352f440bfe1f",
                    "spentIndex":1,
                    "spentHeight":819533
                },
                {
                    "value":"42.86671328",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9148c20711bed045fe94b1594bef74d1e70a122088388ac",
                        "asm":"OP_DUP OP_HASH160 8c20711bed045fe94b1594bef74d1e70a1220883 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoTmJD185yqptsbpB8P86iUDepNc7ew9dC"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"517ac0dcde42d24e1a9738ca2a3a74aea67a9f8a2eab1c64caa8b1efe08de0e9",
                    "spentIndex":0,
                    "spentHeight":801545
                }
            ],
            "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
            "blockheight":801537,
            "confirmations":54498,
            "time":1515541051,
            "blocktime":1515541051,
            "valueOut":43.39431328,
            "size":225,
            "valueIn":43.39433988,
            "fees":0.0000266,
            "txlock":false
        },
        {
            "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
            "version":1,
            "locktime":801405,
            "vin":
            [
                {
                    "txid":"ce2c051f45574c447cbb1508437acaf760e79236b7f86c97a15ff11d0ab8e33e",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e01210294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a",
                        "asm":"304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e[ALL] 0294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a"
                    },
                    "addr":"XnVQXrresaPrAA81qcYhCrHRpkAvDGixus",
                    "valueSat":4345623837,
                    "value":43.45623837,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.06187190",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148b82df11f146d6203ca9ce7a67e75f37444c408b88ac",
                        "asm":"OP_DUP OP_HASH160 8b82df11f146d6203ca9ce7a67e75f37444c408b OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoQWY27FwvCzyiLgpgxfDGHToBCehz8Dp4"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"a36a7ef65a34b1205142aad9f7e4a1cccb972c3e685d0e205174ff98c2f3ce07",
                    "spentIndex":0,
                    "spentHeight":801900
                },
                {
                    "value":"43.39433988",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a91469ddad658bc7e99ece553836f0139db1ea55c33988ac",
                        "asm":"OP_DUP OP_HASH160 69ddad658bc7e99ece553836f0139db1ea55c339 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
                    "spentIndex":0,
                    "spentHeight":801537
                }
            ],
            "blockhash":"000000000000001af3534c0f771f9342a02818821fe98dad10f309ae56855c86",
            "blockheight":801407,
            "confirmations":54628,
            "time":1515520337,
            "blocktime":1515520337,
            "valueOut":43.45621178,
            "size":225,
            "valueIn":43.45623837,
            "fees":0.00002659,
            "txlock":false
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
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/txs?address=<ADDRESS>&token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "pagesTotal":1,
    "txs":
    [
        {
            "txid":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
            "version":1,
            "locktime":801535,
            "vin":
            [
                {
                    "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb896495501210366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0",
                        "asm":"304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb8964955[ALL] 0366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0"
                    },
                    "addr":"XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA",
                    "valueSat":4339433988,
                    "value":43.39433988,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.52760000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9147d412940d1dce226cb39f9aade2b45a8139410c388ac",
                        "asm":"OP_DUP OP_HASH160 7d412940d1dce226cb39f9aade2b45a8139410c3 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xn78Mi21PMiHt9WP4L53jGM4YmFJW1Byt1"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"cbdad5342e7adf96653ebd0cb975c87c968d9a42183c6ca9f89a352f440bfe1f",
                    "spentIndex":1,
                    "spentHeight":819533
                },
                {
                    "value":"42.86671328",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9148c20711bed045fe94b1594bef74d1e70a122088388ac",
                        "asm":"OP_DUP OP_HASH160 8c20711bed045fe94b1594bef74d1e70a1220883 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoTmJD185yqptsbpB8P86iUDepNc7ew9dC"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"517ac0dcde42d24e1a9738ca2a3a74aea67a9f8a2eab1c64caa8b1efe08de0e9",
                    "spentIndex":0,
                    "spentHeight":801545
                }
            ],
            "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
            "blockheight":801537,
            "confirmations":54498,
            "time":1515541051,
            "blocktime":1515541051,
            "valueOut":43.39431328,
            "size":225,
            "valueIn":43.39433988,
            "fees":0.0000266,
            "txlock":false
        },
        {
            "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
            "version":1,
            "locktime":801405,
            "vin":
            [
                {
                    "txid":"ce2c051f45574c447cbb1508437acaf760e79236b7f86c97a15ff11d0ab8e33e",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e01210294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a",
                        "asm":"304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e[ALL] 0294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a"
                    },
                    "addr":"XnVQXrresaPrAA81qcYhCrHRpkAvDGixus",
                    "valueSat":4345623837,
                    "value":43.45623837,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.06187190",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148b82df11f146d6203ca9ce7a67e75f37444c408b88ac",
                        "asm":"OP_DUP OP_HASH160 8b82df11f146d6203ca9ce7a67e75f37444c408b OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoQWY27FwvCzyiLgpgxfDGHToBCehz8Dp4"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"a36a7ef65a34b1205142aad9f7e4a1cccb972c3e685d0e205174ff98c2f3ce07",
                    "spentIndex":0,
                    "spentHeight":801900
                },
                {
                    "value":"43.39433988",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a91469ddad658bc7e99ece553836f0139db1ea55c33988ac",
                        "asm":"OP_DUP OP_HASH160 69ddad658bc7e99ece553836f0139db1ea55c339 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
                    "spentIndex":0,
                    "spentHeight":801537
                }
            ],
            "blockhash":"000000000000001af3534c0f771f9342a02818821fe98dad10f309ae56855c86",
            "blockheight":801407,
            "confirmations":54628,
            "time":1515520337,
            "blocktime":1515520337,
            "valueOut":43.45621178,
            "size":225,
            "valueIn":43.45623837,
            "fees":0.00002659,
            "txlock":false
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

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/txs',
         params: {'address': <ADDRESS>, 'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "pagesTotal":1,
    "txs":
    [
        {
            "txid":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
            "version":1,
            "locktime":801535,
            "vin":
            [
                {
                    "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb896495501210366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0",
                        "asm":"304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb8964955[ALL] 0366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0"
                    },
                    "addr":"XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA",
                    "valueSat":4339433988,
                    "value":43.39433988,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.52760000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9147d412940d1dce226cb39f9aade2b45a8139410c388ac",
                        "asm":"OP_DUP OP_HASH160 7d412940d1dce226cb39f9aade2b45a8139410c3 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xn78Mi21PMiHt9WP4L53jGM4YmFJW1Byt1"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"cbdad5342e7adf96653ebd0cb975c87c968d9a42183c6ca9f89a352f440bfe1f",
                    "spentIndex":1,
                    "spentHeight":819533
                },
                {
                    "value":"42.86671328",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9148c20711bed045fe94b1594bef74d1e70a122088388ac",
                        "asm":"OP_DUP OP_HASH160 8c20711bed045fe94b1594bef74d1e70a1220883 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoTmJD185yqptsbpB8P86iUDepNc7ew9dC"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"517ac0dcde42d24e1a9738ca2a3a74aea67a9f8a2eab1c64caa8b1efe08de0e9",
                    "spentIndex":0,
                    "spentHeight":801545
                }
            ],
            "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
            "blockheight":801537,
            "confirmations":54498,
            "time":1515541051,
            "blocktime":1515541051,
            "valueOut":43.39431328,
            "size":225,
            "valueIn":43.39433988,
            "fees":0.0000266,
            "txlock":false
        },
        {
            "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
            "version":1,
            "locktime":801405,
            "vin":
            [
                {
                    "txid":"ce2c051f45574c447cbb1508437acaf760e79236b7f86c97a15ff11d0ab8e33e",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e01210294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a",
                        "asm":"304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e[ALL] 0294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a"
                    },
                    "addr":"XnVQXrresaPrAA81qcYhCrHRpkAvDGixus",
                    "valueSat":4345623837,
                    "value":43.45623837,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.06187190",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148b82df11f146d6203ca9ce7a67e75f37444c408b88ac",
                        "asm":"OP_DUP OP_HASH160 8b82df11f146d6203ca9ce7a67e75f37444c408b OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoQWY27FwvCzyiLgpgxfDGHToBCehz8Dp4"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"a36a7ef65a34b1205142aad9f7e4a1cccb972c3e685d0e205174ff98c2f3ce07",
                    "spentIndex":0,
                    "spentHeight":801900
                },
                {
                    "value":"43.39433988",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a91469ddad658bc7e99ece553836f0139db1ea55c33988ac",
                        "asm":"OP_DUP OP_HASH160 69ddad658bc7e99ece553836f0139db1ea55c339 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
                    "spentIndex":0,
                    "spentHeight":801537
                }
            ],
            "blockhash":"000000000000001af3534c0f771f9342a02818821fe98dad10f309ae56855c86",
            "blockheight":801407,
            "confirmations":54628,
            "time":1515520337,
            "blocktime":1515520337,
            "valueOut":43.45621178,
            "size":225,
            "valueIn":43.45623837,
            "fees":0.00002659,
            "txlock":false
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

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/txs',
                  params={'address': <ADDRESS>, 'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "pagesTotal":1,
    "txs":
    [
        {
            "txid":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
            "version":1,
            "locktime":801535,
            "vin":
            [
                {
                    "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb896495501210366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0",
                        "asm":"304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb8964955[ALL] 0366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0"
                    },
                    "addr":"XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA",
                    "valueSat":4339433988,
                    "value":43.39433988,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.52760000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9147d412940d1dce226cb39f9aade2b45a8139410c388ac",
                        "asm":"OP_DUP OP_HASH160 7d412940d1dce226cb39f9aade2b45a8139410c3 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xn78Mi21PMiHt9WP4L53jGM4YmFJW1Byt1"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"cbdad5342e7adf96653ebd0cb975c87c968d9a42183c6ca9f89a352f440bfe1f",
                    "spentIndex":1,
                    "spentHeight":819533
                },
                {
                    "value":"42.86671328",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9148c20711bed045fe94b1594bef74d1e70a122088388ac",
                        "asm":"OP_DUP OP_HASH160 8c20711bed045fe94b1594bef74d1e70a1220883 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoTmJD185yqptsbpB8P86iUDepNc7ew9dC"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"517ac0dcde42d24e1a9738ca2a3a74aea67a9f8a2eab1c64caa8b1efe08de0e9",
                    "spentIndex":0,
                    "spentHeight":801545
                }
            ],
            "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
            "blockheight":801537,
            "confirmations":54498,
            "time":1515541051,
            "blocktime":1515541051,
            "valueOut":43.39431328,
            "size":225,
            "valueIn":43.39433988,
            "fees":0.0000266,
            "txlock":false
        },
        {
            "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
            "version":1,
            "locktime":801405,
            "vin":
            [
                {
                    "txid":"ce2c051f45574c447cbb1508437acaf760e79236b7f86c97a15ff11d0ab8e33e",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e01210294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a",
                        "asm":"304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e[ALL] 0294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a"
                    },
                    "addr":"XnVQXrresaPrAA81qcYhCrHRpkAvDGixus",
                    "valueSat":4345623837,
                    "value":43.45623837,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.06187190",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148b82df11f146d6203ca9ce7a67e75f37444c408b88ac",
                        "asm":"OP_DUP OP_HASH160 8b82df11f146d6203ca9ce7a67e75f37444c408b OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoQWY27FwvCzyiLgpgxfDGHToBCehz8Dp4"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"a36a7ef65a34b1205142aad9f7e4a1cccb972c3e685d0e205174ff98c2f3ce07",
                    "spentIndex":0,
                    "spentHeight":801900
                },
                {
                    "value":"43.39433988",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a91469ddad658bc7e99ece553836f0139db1ea55c33988ac",
                        "asm":"OP_DUP OP_HASH160 69ddad658bc7e99ece553836f0139db1ea55c339 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
                    "spentIndex":0,
                    "spentHeight":801537
                }
            ],
            "blockhash":"000000000000001af3534c0f771f9342a02818821fe98dad10f309ae56855c86",
            "blockheight":801407,
            "confirmations":54628,
            "time":1515520337,
            "blocktime":1515520337,
            "valueOut":43.45621178,
            "size":225,
            "valueIn":43.45623837,
            "fees":0.00002659,
            "txlock":false
        }
    ]
}
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/txs?address=<ADDRESS>&token=<TOKEN>");
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
    "pagesTotal":1,
    "txs":
    [
        {
            "txid":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
            "version":1,
            "locktime":801535,
            "vin":
            [
                {
                    "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb896495501210366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0",
                        "asm":"304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb8964955[ALL] 0366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0"
                    },
                    "addr":"XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA",
                    "valueSat":4339433988,
                    "value":43.39433988,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.52760000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9147d412940d1dce226cb39f9aade2b45a8139410c388ac",
                        "asm":"OP_DUP OP_HASH160 7d412940d1dce226cb39f9aade2b45a8139410c3 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xn78Mi21PMiHt9WP4L53jGM4YmFJW1Byt1"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"cbdad5342e7adf96653ebd0cb975c87c968d9a42183c6ca9f89a352f440bfe1f",
                    "spentIndex":1,
                    "spentHeight":819533
                },
                {
                    "value":"42.86671328",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9148c20711bed045fe94b1594bef74d1e70a122088388ac",
                        "asm":"OP_DUP OP_HASH160 8c20711bed045fe94b1594bef74d1e70a1220883 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoTmJD185yqptsbpB8P86iUDepNc7ew9dC"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"517ac0dcde42d24e1a9738ca2a3a74aea67a9f8a2eab1c64caa8b1efe08de0e9",
                    "spentIndex":0,
                    "spentHeight":801545
                }
            ],
            "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
            "blockheight":801537,
            "confirmations":54498,
            "time":1515541051,
            "blocktime":1515541051,
            "valueOut":43.39431328,
            "size":225,
            "valueIn":43.39433988,
            "fees":0.0000266,
            "txlock":false
        },
        {
            "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
            "version":1,
            "locktime":801405,
            "vin":
            [
                {
                    "txid":"ce2c051f45574c447cbb1508437acaf760e79236b7f86c97a15ff11d0ab8e33e",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e01210294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a",
                        "asm":"304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e[ALL] 0294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a"
                    },
                    "addr":"XnVQXrresaPrAA81qcYhCrHRpkAvDGixus",
                    "valueSat":4345623837,
                    "value":43.45623837,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.06187190",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148b82df11f146d6203ca9ce7a67e75f37444c408b88ac",
                        "asm":"OP_DUP OP_HASH160 8b82df11f146d6203ca9ce7a67e75f37444c408b OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoQWY27FwvCzyiLgpgxfDGHToBCehz8Dp4"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"a36a7ef65a34b1205142aad9f7e4a1cccb972c3e685d0e205174ff98c2f3ce07",
                    "spentIndex":0,
                    "spentHeight":801900
                },
                {
                    "value":"43.39433988",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a91469ddad658bc7e99ece553836f0139db1ea55c33988ac",
                        "asm":"OP_DUP OP_HASH160 69ddad658bc7e99ece553836f0139db1ea55c339 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
                    "spentIndex":0,
                    "spentHeight":801537
                }
            ],
            "blockhash":"000000000000001af3534c0f771f9342a02818821fe98dad10f309ae56855c86",
            "blockheight":801407,
            "confirmations":54628,
            "time":1515520337,
            "blocktime":1515520337,
            "valueOut":43.45621178,
            "size":225,
            "valueIn":43.45623837,
            "fees":0.00002659,
            "txlock":false
        }
    ]
}
```

## Transactions for multiple Addresses - GET

<h3 id="getTransactionsAddresses">GET /addrs/< address1 >,< address2 >,...,< addressn >/txs</h3>

<a id="opIdGetTransactionsAddresses"></a>

*Get Transactions for multiple Addresses*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|addr|path|String Aray(address)|True|Array of comma separated address strings|
|from|query|Integer|False|Starting number of tx|
|to|query|Integer|False|Ending number of tx|
|noAsm|query|Integer|False|Default is 0. If set to 1 Asm info will be ommitted for tx.|
|noScriptSig|query|Integer|False|Default is 0. If set to 1 Script Signature info will be ommitted for tx.|
|noSpent|query|Integer|False|Default is 0. If set to 1 Spent info will be ommitted for tx.|
|token|query|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[TxAddressesObject](#schemetxaddressesobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<a id="divider"></a>

> Code samples

```shell
curl -X GET https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/addrs/<ADDRESS1>,<ADDRESS2>,..,<ADDRESSn>/txs?token=<TOKEN> \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

# Response example
{
    "totalItems":2,
    "from":0,
    "to":2,
    "items":
    [
        {
            "txid":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
            "version":1,
            "locktime":801535,
            "vin":
            [
                {
                    "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb896495501210366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0",
                        "asm":"304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb8964955[ALL] 0366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0"
                    },
                    "addr":"XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA",
                    "valueSat":4339433988,
                    "value":43.39433988,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.52760000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9147d412940d1dce226cb39f9aade2b45a8139410c388ac",
                        "asm":"OP_DUP OP_HASH160 7d412940d1dce226cb39f9aade2b45a8139410c3 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xn78Mi21PMiHt9WP4L53jGM4YmFJW1Byt1"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"cbdad5342e7adf96653ebd0cb975c87c968d9a42183c6ca9f89a352f440bfe1f",
                    "spentIndex":1,
                    "spentHeight":819533
                },
                {
                    "value":"42.86671328",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9148c20711bed045fe94b1594bef74d1e70a122088388ac",
                        "asm":"OP_DUP OP_HASH160 8c20711bed045fe94b1594bef74d1e70a1220883 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoTmJD185yqptsbpB8P86iUDepNc7ew9dC"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"517ac0dcde42d24e1a9738ca2a3a74aea67a9f8a2eab1c64caa8b1efe08de0e9",
                    "spentIndex":0,
                    "spentHeight":801545
                }
            ],
            "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
            "blockheight":801537,
            "confirmations":54505,
            "time":1515541051,
            "blocktime":1515541051,
            "valueOut":43.39431328,
            "size":225,
            "valueIn":43.39433988,
            "fees":0.0000266,
            "txlock":false
        },
        {
            "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
            "version":1,
            "locktime":801405,
            "vin":
            [
                {
                    "txid":"ce2c051f45574c447cbb1508437acaf760e79236b7f86c97a15ff11d0ab8e33e",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e01210294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a",
                        "asm":"304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e[ALL] 0294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a"
                    },
                    "addr":"XnVQXrresaPrAA81qcYhCrHRpkAvDGixus",
                    "valueSat":4345623837,
                    "value":43.45623837,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.06187190",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148b82df11f146d6203ca9ce7a67e75f37444c408b88ac",
                        "asm":"OP_DUP OP_HASH160 8b82df11f146d6203ca9ce7a67e75f37444c408b OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoQWY27FwvCzyiLgpgxfDGHToBCehz8Dp4"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"a36a7ef65a34b1205142aad9f7e4a1cccb972c3e685d0e205174ff98c2f3ce07",
                    "spentIndex":0,
                    "spentHeight":801900
                },
                {
                    "value":"43.39433988",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a91469ddad658bc7e99ece553836f0139db1ea55c33988ac",
                        "asm":"OP_DUP OP_HASH160 69ddad658bc7e99ece553836f0139db1ea55c339 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
                    "spentIndex":0,
                    "spentHeight":801537
                }
            ],
            "blockhash":"000000000000001af3534c0f771f9342a02818821fe98dad10f309ae56855c86",
            "blockheight":801407,
            "confirmations":54635,
            "time":1515520337,
            "blocktime":1515520337,
            "valueOut":43.45621178,
            "size":225,
            "valueIn":43.45623837,
            "fees":0.00002659,
            "txlock":false
        }
    ]
}
```

```php
<?php
$URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/addrs/<ADDRESS1>,<ADDRESS2>,..,<ADDRESSn>/txs?token=<TOKEN>";

$aHTTP['http']['method']  = 'GET';

$aHTTP['http']['header']  = "Content-Type: application/json\r\nAccept: application/json\r\n";

$context = stream_context_create($aHTTP);

$response = file_get_contents($URL, false, $context);

// Response example
{
    "totalItems":2,
    "from":0,
    "to":2,
    "items":
    [
        {
            "txid":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
            "version":1,
            "locktime":801535,
            "vin":
            [
                {
                    "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb896495501210366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0",
                        "asm":"304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb8964955[ALL] 0366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0"
                    },
                    "addr":"XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA",
                    "valueSat":4339433988,
                    "value":43.39433988,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.52760000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9147d412940d1dce226cb39f9aade2b45a8139410c388ac",
                        "asm":"OP_DUP OP_HASH160 7d412940d1dce226cb39f9aade2b45a8139410c3 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xn78Mi21PMiHt9WP4L53jGM4YmFJW1Byt1"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"cbdad5342e7adf96653ebd0cb975c87c968d9a42183c6ca9f89a352f440bfe1f",
                    "spentIndex":1,
                    "spentHeight":819533
                },
                {
                    "value":"42.86671328",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9148c20711bed045fe94b1594bef74d1e70a122088388ac",
                        "asm":"OP_DUP OP_HASH160 8c20711bed045fe94b1594bef74d1e70a1220883 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoTmJD185yqptsbpB8P86iUDepNc7ew9dC"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"517ac0dcde42d24e1a9738ca2a3a74aea67a9f8a2eab1c64caa8b1efe08de0e9",
                    "spentIndex":0,
                    "spentHeight":801545
                }
            ],
            "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
            "blockheight":801537,
            "confirmations":54505,
            "time":1515541051,
            "blocktime":1515541051,
            "valueOut":43.39431328,
            "size":225,
            "valueIn":43.39433988,
            "fees":0.0000266,
            "txlock":false
        },
        {
            "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
            "version":1,
            "locktime":801405,
            "vin":
            [
                {
                    "txid":"ce2c051f45574c447cbb1508437acaf760e79236b7f86c97a15ff11d0ab8e33e",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e01210294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a",
                        "asm":"304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e[ALL] 0294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a"
                    },
                    "addr":"XnVQXrresaPrAA81qcYhCrHRpkAvDGixus",
                    "valueSat":4345623837,
                    "value":43.45623837,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.06187190",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148b82df11f146d6203ca9ce7a67e75f37444c408b88ac",
                        "asm":"OP_DUP OP_HASH160 8b82df11f146d6203ca9ce7a67e75f37444c408b OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoQWY27FwvCzyiLgpgxfDGHToBCehz8Dp4"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"a36a7ef65a34b1205142aad9f7e4a1cccb972c3e685d0e205174ff98c2f3ce07",
                    "spentIndex":0,
                    "spentHeight":801900
                },
                {
                    "value":"43.39433988",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a91469ddad658bc7e99ece553836f0139db1ea55c33988ac",
                        "asm":"OP_DUP OP_HASH160 69ddad658bc7e99ece553836f0139db1ea55c339 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
                    "spentIndex":0,
                    "spentHeight":801537
                }
            ],
            "blockhash":"000000000000001af3534c0f771f9342a02818821fe98dad10f309ae56855c86",
            "blockheight":801407,
            "confirmations":54635,
            "time":1515520337,
            "blocktime":1515520337,
            "valueOut":43.45621178,
            "size":225,
            "valueIn":43.45623837,
            "fees":0.00002659,
            "txlock":false
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
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/addrs/<ADDRESS1>,<ADDRESS2>,..,<ADDRESSn>/txs?token=<TOKEN>',
  method: 'get',
  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
});

// Response example
{
    "totalItems":2,
    "from":0,
    "to":2,
    "items":
    [
        {
            "txid":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
            "version":1,
            "locktime":801535,
            "vin":
            [
                {
                    "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb896495501210366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0",
                        "asm":"304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb8964955[ALL] 0366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0"
                    },
                    "addr":"XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA",
                    "valueSat":4339433988,
                    "value":43.39433988,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.52760000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9147d412940d1dce226cb39f9aade2b45a8139410c388ac",
                        "asm":"OP_DUP OP_HASH160 7d412940d1dce226cb39f9aade2b45a8139410c3 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xn78Mi21PMiHt9WP4L53jGM4YmFJW1Byt1"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"cbdad5342e7adf96653ebd0cb975c87c968d9a42183c6ca9f89a352f440bfe1f",
                    "spentIndex":1,
                    "spentHeight":819533
                },
                {
                    "value":"42.86671328",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9148c20711bed045fe94b1594bef74d1e70a122088388ac",
                        "asm":"OP_DUP OP_HASH160 8c20711bed045fe94b1594bef74d1e70a1220883 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoTmJD185yqptsbpB8P86iUDepNc7ew9dC"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"517ac0dcde42d24e1a9738ca2a3a74aea67a9f8a2eab1c64caa8b1efe08de0e9",
                    "spentIndex":0,
                    "spentHeight":801545
                }
            ],
            "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
            "blockheight":801537,
            "confirmations":54505,
            "time":1515541051,
            "blocktime":1515541051,
            "valueOut":43.39431328,
            "size":225,
            "valueIn":43.39433988,
            "fees":0.0000266,
            "txlock":false
        },
        {
            "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
            "version":1,
            "locktime":801405,
            "vin":
            [
                {
                    "txid":"ce2c051f45574c447cbb1508437acaf760e79236b7f86c97a15ff11d0ab8e33e",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e01210294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a",
                        "asm":"304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e[ALL] 0294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a"
                    },
                    "addr":"XnVQXrresaPrAA81qcYhCrHRpkAvDGixus",
                    "valueSat":4345623837,
                    "value":43.45623837,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.06187190",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148b82df11f146d6203ca9ce7a67e75f37444c408b88ac",
                        "asm":"OP_DUP OP_HASH160 8b82df11f146d6203ca9ce7a67e75f37444c408b OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoQWY27FwvCzyiLgpgxfDGHToBCehz8Dp4"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"a36a7ef65a34b1205142aad9f7e4a1cccb972c3e685d0e205174ff98c2f3ce07",
                    "spentIndex":0,
                    "spentHeight":801900
                },
                {
                    "value":"43.39433988",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a91469ddad658bc7e99ece553836f0139db1ea55c33988ac",
                        "asm":"OP_DUP OP_HASH160 69ddad658bc7e99ece553836f0139db1ea55c339 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
                    "spentIndex":0,
                    "spentHeight":801537
                }
            ],
            "blockhash":"000000000000001af3534c0f771f9342a02818821fe98dad10f309ae56855c86",
            "blockheight":801407,
            "confirmations":54635,
            "time":1515520337,
            "blocktime":1515520337,
            "valueOut":43.45621178,
            "size":225,
            "valueIn":43.45623837,
            "fees":0.00002659,
            "txlock":false
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

result = RestClient.get 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/addrs/<ADDRESS1>,<ADDRESS2>,..,<ADDRESSn>/txs',
         params: {'token': <TOKEN>}, headers: headers

p JSON.parse(result)

# Response example
{
    "totalItems":2,
    "from":0,
    "to":2,
    "items":
    [
        {
            "txid":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
            "version":1,
            "locktime":801535,
            "vin":
            [
                {
                    "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb896495501210366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0",
                        "asm":"304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb8964955[ALL] 0366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0"
                    },
                    "addr":"XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA",
                    "valueSat":4339433988,
                    "value":43.39433988,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.52760000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9147d412940d1dce226cb39f9aade2b45a8139410c388ac",
                        "asm":"OP_DUP OP_HASH160 7d412940d1dce226cb39f9aade2b45a8139410c3 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xn78Mi21PMiHt9WP4L53jGM4YmFJW1Byt1"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"cbdad5342e7adf96653ebd0cb975c87c968d9a42183c6ca9f89a352f440bfe1f",
                    "spentIndex":1,
                    "spentHeight":819533
                },
                {
                    "value":"42.86671328",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9148c20711bed045fe94b1594bef74d1e70a122088388ac",
                        "asm":"OP_DUP OP_HASH160 8c20711bed045fe94b1594bef74d1e70a1220883 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoTmJD185yqptsbpB8P86iUDepNc7ew9dC"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"517ac0dcde42d24e1a9738ca2a3a74aea67a9f8a2eab1c64caa8b1efe08de0e9",
                    "spentIndex":0,
                    "spentHeight":801545
                }
            ],
            "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
            "blockheight":801537,
            "confirmations":54505,
            "time":1515541051,
            "blocktime":1515541051,
            "valueOut":43.39431328,
            "size":225,
            "valueIn":43.39433988,
            "fees":0.0000266,
            "txlock":false
        },
        {
            "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
            "version":1,
            "locktime":801405,
            "vin":
            [
                {
                    "txid":"ce2c051f45574c447cbb1508437acaf760e79236b7f86c97a15ff11d0ab8e33e",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e01210294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a",
                        "asm":"304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e[ALL] 0294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a"
                    },
                    "addr":"XnVQXrresaPrAA81qcYhCrHRpkAvDGixus",
                    "valueSat":4345623837,
                    "value":43.45623837,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.06187190",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148b82df11f146d6203ca9ce7a67e75f37444c408b88ac",
                        "asm":"OP_DUP OP_HASH160 8b82df11f146d6203ca9ce7a67e75f37444c408b OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoQWY27FwvCzyiLgpgxfDGHToBCehz8Dp4"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"a36a7ef65a34b1205142aad9f7e4a1cccb972c3e685d0e205174ff98c2f3ce07",
                    "spentIndex":0,
                    "spentHeight":801900
                },
                {
                    "value":"43.39433988",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a91469ddad658bc7e99ece553836f0139db1ea55c33988ac",
                        "asm":"OP_DUP OP_HASH160 69ddad658bc7e99ece553836f0139db1ea55c339 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
                    "spentIndex":0,
                    "spentHeight":801537
                }
            ],
            "blockhash":"000000000000001af3534c0f771f9342a02818821fe98dad10f309ae56855c86",
            "blockheight":801407,
            "confirmations":54635,
            "time":1515520337,
            "blocktime":1515520337,
            "valueOut":43.45621178,
            "size":225,
            "valueIn":43.45623837,
            "fees":0.00002659,
            "txlock":false
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

r = requests.get('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/addrs/<ADDRESS1>,<ADDRESS2>,..,<ADDRESSn>/txs',
                  params={'token': <TOKEN>}, headers = headers)

print r.json()

# Response example
{
    "totalItems":2,
    "from":0,
    "to":2,
    "items":
    [
        {
            "txid":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
            "version":1,
            "locktime":801535,
            "vin":
            [
                {
                    "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb896495501210366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0",
                        "asm":"304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb8964955[ALL] 0366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0"
                    },
                    "addr":"XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA",
                    "valueSat":4339433988,
                    "value":43.39433988,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.52760000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9147d412940d1dce226cb39f9aade2b45a8139410c388ac",
                        "asm":"OP_DUP OP_HASH160 7d412940d1dce226cb39f9aade2b45a8139410c3 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xn78Mi21PMiHt9WP4L53jGM4YmFJW1Byt1"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"cbdad5342e7adf96653ebd0cb975c87c968d9a42183c6ca9f89a352f440bfe1f",
                    "spentIndex":1,
                    "spentHeight":819533
                },
                {
                    "value":"42.86671328",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9148c20711bed045fe94b1594bef74d1e70a122088388ac",
                        "asm":"OP_DUP OP_HASH160 8c20711bed045fe94b1594bef74d1e70a1220883 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoTmJD185yqptsbpB8P86iUDepNc7ew9dC"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"517ac0dcde42d24e1a9738ca2a3a74aea67a9f8a2eab1c64caa8b1efe08de0e9",
                    "spentIndex":0,
                    "spentHeight":801545
                }
            ],
            "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
            "blockheight":801537,
            "confirmations":54505,
            "time":1515541051,
            "blocktime":1515541051,
            "valueOut":43.39431328,
            "size":225,
            "valueIn":43.39433988,
            "fees":0.0000266,
            "txlock":false
        },
        {
            "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
            "version":1,
            "locktime":801405,
            "vin":
            [
                {
                    "txid":"ce2c051f45574c447cbb1508437acaf760e79236b7f86c97a15ff11d0ab8e33e",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e01210294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a",
                        "asm":"304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e[ALL] 0294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a"
                    },
                    "addr":"XnVQXrresaPrAA81qcYhCrHRpkAvDGixus",
                    "valueSat":4345623837,
                    "value":43.45623837,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.06187190",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148b82df11f146d6203ca9ce7a67e75f37444c408b88ac",
                        "asm":"OP_DUP OP_HASH160 8b82df11f146d6203ca9ce7a67e75f37444c408b OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoQWY27FwvCzyiLgpgxfDGHToBCehz8Dp4"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"a36a7ef65a34b1205142aad9f7e4a1cccb972c3e685d0e205174ff98c2f3ce07",
                    "spentIndex":0,
                    "spentHeight":801900
                },
                {
                    "value":"43.39433988",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a91469ddad658bc7e99ece553836f0139db1ea55c33988ac",
                        "asm":"OP_DUP OP_HASH160 69ddad658bc7e99ece553836f0139db1ea55c339 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
                    "spentIndex":0,
                    "spentHeight":801537
                }
            ],
            "blockhash":"000000000000001af3534c0f771f9342a02818821fe98dad10f309ae56855c86",
            "blockheight":801407,
            "confirmations":54635,
            "time":1515520337,
            "blocktime":1515520337,
            "valueOut":43.45621178,
            "size":225,
            "valueIn":43.45623837,
            "fees":0.00002659,
            "txlock":false
        }
    ]
}
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/addrs/<ADDRESS1>,<ADDRESS2>,..,<ADDRESSn>/txs?token=<TOKEN>");
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
    "totalItems":2,
    "from":0,
    "to":2,
    "items":
    [
        {
            "txid":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
            "version":1,
            "locktime":801535,
            "vin":
            [
                {
                    "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb896495501210366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0",
                        "asm":"304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb8964955[ALL] 0366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0"
                    },
                    "addr":"XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA",
                    "valueSat":4339433988,
                    "value":43.39433988,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.52760000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9147d412940d1dce226cb39f9aade2b45a8139410c388ac",
                        "asm":"OP_DUP OP_HASH160 7d412940d1dce226cb39f9aade2b45a8139410c3 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xn78Mi21PMiHt9WP4L53jGM4YmFJW1Byt1"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"cbdad5342e7adf96653ebd0cb975c87c968d9a42183c6ca9f89a352f440bfe1f",
                    "spentIndex":1,
                    "spentHeight":819533
                },
                {
                    "value":"42.86671328",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9148c20711bed045fe94b1594bef74d1e70a122088388ac",
                        "asm":"OP_DUP OP_HASH160 8c20711bed045fe94b1594bef74d1e70a1220883 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoTmJD185yqptsbpB8P86iUDepNc7ew9dC"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"517ac0dcde42d24e1a9738ca2a3a74aea67a9f8a2eab1c64caa8b1efe08de0e9",
                    "spentIndex":0,
                    "spentHeight":801545
                }
            ],
            "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
            "blockheight":801537,
            "confirmations":54505,
            "time":1515541051,
            "blocktime":1515541051,
            "valueOut":43.39431328,
            "size":225,
            "valueIn":43.39433988,
            "fees":0.0000266,
            "txlock":false
        },
        {
            "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
            "version":1,
            "locktime":801405,
            "vin":
            [
                {
                    "txid":"ce2c051f45574c447cbb1508437acaf760e79236b7f86c97a15ff11d0ab8e33e",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e01210294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a",
                        "asm":"304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e[ALL] 0294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a"
                    },
                    "addr":"XnVQXrresaPrAA81qcYhCrHRpkAvDGixus",
                    "valueSat":4345623837,
                    "value":43.45623837,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.06187190",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148b82df11f146d6203ca9ce7a67e75f37444c408b88ac",
                        "asm":"OP_DUP OP_HASH160 8b82df11f146d6203ca9ce7a67e75f37444c408b OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoQWY27FwvCzyiLgpgxfDGHToBCehz8Dp4"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"a36a7ef65a34b1205142aad9f7e4a1cccb972c3e685d0e205174ff98c2f3ce07",
                    "spentIndex":0,
                    "spentHeight":801900
                },
                {
                    "value":"43.39433988",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a91469ddad658bc7e99ece553836f0139db1ea55c33988ac",
                        "asm":"OP_DUP OP_HASH160 69ddad658bc7e99ece553836f0139db1ea55c339 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
                    "spentIndex":0,
                    "spentHeight":801537
                }
            ],
            "blockhash":"000000000000001af3534c0f771f9342a02818821fe98dad10f309ae56855c86",
            "blockheight":801407,
            "confirmations":54635,
            "time":1515520337,
            "blocktime":1515520337,
            "valueOut":43.45621178,
            "size":225,
            "valueIn":43.45623837,
            "fees":0.00002659,
            "txlock":false
        }
    ]
}
```

## Transactions for multiple Addresses - POST

<h3 id="postTransactionsAddresses">POST /addrs/txs </h3>

<a id="opIdpostTransactionsAddresses"></a>

*Get Transactions for multiple Addresses by using POST method*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|addrs|body|String Aray(address)|True|Array of comma separated address strings|
|from|body|Integer|False|Starting number of tx|
|to|body|Integer|False|Ending number of tx|
|noAsm|body|Integer|False|Default is 0. If set to 1 Asm info will be ommitted for tx.|
|noScriptSig|body|Integer|False|Default is 0. If set to 1 Script Signature info will be ommitted for tx.|
|noSpent|body|Integer|False|Default is 0. If set to 1 Spent info will be ommitted for tx.|
|token|body|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[TxAddressesObject](#schemetxaddressesobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<a id="divider"></a>

> Code samples

```shell
curl -X POST https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/addrs/txs \
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
    $URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/addrs/txs";
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
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/addrs/txs',
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

result = RestClient.post 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/addrs/txs',
         payload:<body_here>, headers: headers

p JSON.parse(result)
```

```python
import requests

headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/addrs/txs',
                  data=<body_here>, params={}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/addrs/txs");
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
"addrs": "XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA,XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA,XxRB5fnF8KpB9jjRRb7M7pq4qtyL8xbUou",
"token": <TOKEN>
}
```

> Example response

```json
{
    "totalItems":2,
    "from":0,
    "to":2,
    "items":
    [
        {
            "txid":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
            "version":1,
            "locktime":801535,
            "vin":
            [
                {
                    "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb896495501210366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0",
                        "asm":"304402202e06975207a5326fe4ade7ed08216d5cf06f26f0adc31953dafa1ea7b2097733022005c179c4f7433f5141d3010a6cf79f36f6548c18ea01537ca7cdd22fb8964955[ALL] 0366f76060de6b69852732eaf3e97ec1152da0a785394441a669fe1bb8d0f1f0c0"
                    },
                    "addr":"XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA",
                    "valueSat":4339433988,
                    "value":43.39433988,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.52760000",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9147d412940d1dce226cb39f9aade2b45a8139410c388ac",
                        "asm":"OP_DUP OP_HASH160 7d412940d1dce226cb39f9aade2b45a8139410c3 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "Xn78Mi21PMiHt9WP4L53jGM4YmFJW1Byt1"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"cbdad5342e7adf96653ebd0cb975c87c968d9a42183c6ca9f89a352f440bfe1f",
                    "spentIndex":1,
                    "spentHeight":819533
                },
                {
                    "value":"42.86671328",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a9148c20711bed045fe94b1594bef74d1e70a122088388ac",
                        "asm":"OP_DUP OP_HASH160 8c20711bed045fe94b1594bef74d1e70a1220883 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoTmJD185yqptsbpB8P86iUDepNc7ew9dC"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"517ac0dcde42d24e1a9738ca2a3a74aea67a9f8a2eab1c64caa8b1efe08de0e9",
                    "spentIndex":0,
                    "spentHeight":801545
                }
            ],
            "blockhash":"000000000000002067162ba82c79256015f8cbbab7d62c79f2393e026674307e",
            "blockheight":801537,
            "confirmations":54505,
            "time":1515541051,
            "blocktime":1515541051,
            "valueOut":43.39431328,
            "size":225,
            "valueIn":43.39433988,
            "fees":0.0000266,
            "txlock":false
        },
        {
            "txid":"62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66",
            "version":1,
            "locktime":801405,
            "vin":
            [
                {
                    "txid":"ce2c051f45574c447cbb1508437acaf760e79236b7f86c97a15ff11d0ab8e33e",
                    "vout":1,
                    "sequence":4294967294,
                    "n":0,
                    "scriptSig":
                    {
                        "hex":"47304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e01210294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a",
                        "asm":"304402207d37e412bf8e6566ae1943655a8a243af34fccfd7c8f34f61c36a4994a670ba30220239db5c02e257733ed05b9d2c02f7f189501617055836f59e93a45f5e145031e[ALL] 0294ab06f824009afde98adceb3bc8839dbf3caeb2a337fbb2a6df8060d5bc2f9a"
                    },
                    "addr":"XnVQXrresaPrAA81qcYhCrHRpkAvDGixus",
                    "valueSat":4345623837,
                    "value":43.45623837,
                    "doubleSpentTxID":null
                }
            ],
            "vout":
            [
                {
                    "value":"0.06187190",
                    "n":0,
                    "scriptPubKey":
                    {
                        "hex":"76a9148b82df11f146d6203ca9ce7a67e75f37444c408b88ac",
                        "asm":"OP_DUP OP_HASH160 8b82df11f146d6203ca9ce7a67e75f37444c408b OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XoQWY27FwvCzyiLgpgxfDGHToBCehz8Dp4"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"a36a7ef65a34b1205142aad9f7e4a1cccb972c3e685d0e205174ff98c2f3ce07",
                    "spentIndex":0,
                    "spentHeight":801900
                },
                {
                    "value":"43.39433988",
                    "n":1,
                    "scriptPubKey":
                    {
                        "hex":"76a91469ddad658bc7e99ece553836f0139db1ea55c33988ac",
                        "asm":"OP_DUP OP_HASH160 69ddad658bc7e99ece553836f0139db1ea55c339 OP_EQUALVERIFY OP_CHECKSIG",
                        "addresses":
                        [
                            "XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA"
                        ],
                        "type":"pubkeyhash"
                    },
                    "spentTxId":"58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
                    "spentIndex":0,
                    "spentHeight":801537
                }
            ],
            "blockhash":"000000000000001af3534c0f771f9342a02818821fe98dad10f309ae56855c86",
            "blockheight":801407,
            "confirmations":54635,
            "time":1515520337,
            "blocktime":1515520337,
            "valueOut":43.45621178,
            "size":225,
            "valueIn":43.45623837,
            "fees":0.00002659,
            "txlock":false
        }
    ]
}
```

## Send Raw Transaction

<h3 id="sendRawTx">POST /tx/send </h3>

<a id="opIdSendRawTx"></a>

*Send/broadcast Raw Transaction*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|rawtx|body|String|True|Raw signed transaction as hex string|
|token|body|String|True|Token obtained from the ChainRider service|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[TxSendObject](#schemetxsendobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<a id="divider"></a>

> Code samples

```shell
curl -X POST https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/tx/send \
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
    $URL = "https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/tx/send";
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
  url: 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/tx/send',
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

result = RestClient.post 'https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/tx/send',
         payload:<body_here>, headers: headers

p JSON.parse(result)
```

```python
import requests

headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/tx/send',
                  data=<body_here>, params={}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.chainrider.io/v1/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/tx/send");
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
  "rawtx": "01000000017b1eabe0209b1fe794124575ef807057c77ada2138ae4fa8d6c4de0398a14f3f00000000494830450221008949f0cb400094ad2b5eb399d59d01c14d73d8fe6e96df1a7150deb388ab8935022079656090d7f6bac4c9a94e0aad311a4268e082a725f8aeae0573fb12ff866a5f01ffffffff01f0ca052a010000001976a914cbc20a7664f2f69e5355aa427045bc15e7c6c77288ac00000000",
  "token": <TOKEN>
}
```

> Example response

```json
{
  "txid": "c7736a0a0046d5a8cc61c8c3c2821d4d7517f5de2bc66a966011aaa79965ffba"
}
```

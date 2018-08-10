
# Data Objects

<a id="divider">

<h2 id="tocTokenUsage">Token Usage</h2>

<a id="schemetokenusageobject"></a>

|Name|Type|Description|
|---|---|---|
|message|JSON|Message object containing all relevant token usage data.|
|hour|[Usage object](#schemeusageobject)|Provides info regarding API usage for current hour|
|day|[Usage object](#schemeusageobject)|Provides info regarding API usage for current day|
|forward|[Usage object](#schemeusageobject)|Provides info regarding payment forward API usage for current month|

> Example

```json
{
  "message":{
      "hour":{
          "usage":2,
          "limit":300,
          "time_left":1857
      },
      "day":{
          "usage":2,
          "limit":3000,
          "time_left":34257
      },
      "forward":{
          "usage":0,
          "limit":3,
          "time_left":1675857
      }
  }
}
```

<h2 id="tocUsageObject">UsageObject</h2>

<a id="schemeusageobject"></a>

|Name|Type|Description|
|---|---|---|
|usage|Integer|Number of used API calls within corresponding period|
|limit|Integer|Total number of available API calls within corresponding period|
|time_left|Integer|Time left in seconds before the counting is restarted|

> Example

```json
{
  "usage":2,
  "limit":300,
  "time_left":1857
}
```

<h2 id="tocBlockchainInfoObject">BlockchainInfoObject</h2>

<a id="schemeblockchaininfoobject"></a>

|Name|Type|Description|
|---|---|---|
|info|JSON|Info object|
|version|Integer|Bitcore version|
|insightversion|String|Insight API version|
|protocolversion|Integer|Blockchain protocol version|
|blocks|Integer|Number of blocks|
|timeoffset|Integer|Time offset|
|connections|Integer|Number of connections to other nodes|
|proxy|String|Proxy used for connecting|
|difficulty|Float|Current mining difficulty|
|testnet|Boolean|Is it the testnet version of the blockchain|
|relayfee|Float|Minimum relay fee in DASH|
|errors|String|Error description|
|network|String|Blockchain type ENUM {"livenet", "testnet"}|

<a id="divider"></a>

> Example

```json
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

<h2 id="tocBlockchainDifficultyObject">BlockchainDifficultyObject</h2>

<a id="schemeblockchaindifficultyobject"></a>

|Name|Type|Description|
|---|---|---|
|difficulty|Float|Current mining difficulty|

> Example



```json
{
    "difficulty": 41610185.00844856
}
```

<h2 id="tocBlockchainBestBlockObject">BlockchainBestBlockObject</h2>

<a id="schemeblockchainbestblockobject"></a>

|Name|Type|Description|
|---|---|---|
|bestblockhash|String (HEX)|Hash of the best block|

<a id="divider"></a>

> Example

```json
{
    "bestblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
```

<h2 id="tocBlockchainLastBlockObject">BlockchainLastBlockObject</h2>

<a id="schemeblockchainlastblockobject"></a>

|Name|Type|Description|
|---|---|---|
|syncTipHash|String (HEX)|Hash of the block up to which the sync has been done|
|lastblockhash|String (HEX)|Hash of the last block|

<a id="divider"></a>

> Example

```json
{
    "syncTipHash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5",
    "lastblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
```

<h2 id="tocBlockchainDataSyncObject">BlockchainDataSyncObject</h2>

<a id="schemeblockchaindatasyncobject"></a>

|Name|Type|Description|
|---|---|---|
|status|String|Sync status|
|blockChainHeight|Integer|Current blockchain height|
|syncPercentage|Integer|Sync status as persentage |
|height|Integer|Blockchain height (last block index)|
|error|String|Error description|
|type|String|Sync type|

<a id="divider"></a>

> Example

```json
{
    "status":"finished",
    "blockChainHeight":855511,
    "syncPercentage":100,
    "height":855511,
    "error":null,
    "type":"bitcore node"
}
```

<h2 id="tocBlockchainProposalsObject">BlockchainProposalsObject</h2>

<a id="schemeblockchainproposalsobject"></a>

|Name|Type|Description|
|---|---|---|
|Hash|String (HEX)|Proposal hash|
|DataObject|JSON|[Proposal data object](#schemeproposaldataobject)|
|AbsoluteYesCount|Integer|Number of Absolute Yes Votes|
|YesCount|Integer|Number of Yes Votes|
|NoCount|Integer|Number of No Votes|
|AbstainCount|Integer|Number of Abstain Votes|

<a id="divider"></a>

> Example

```json
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
}
```

<h2 id="tocProposalDataObject">ProposalDataObject</h2>

<a id="schemeproposaldataobject"></a>

|Name|Type|Description|
|---|---|---|
|end_epoch|Integer|End time (epoch)|
|name|String|Name of the proposal|
|payment_address|String|Payment address of the proposal|
|payment_amount|Integer|Proposal Amount in DASH|
|start_epoch|Integer|Start time (epoch)|
|type|Integer|Type of teh proposal|
|url|String|URL of the proposal|

<a id="divider"></a>

> Example

```json

{
    "end_epoch":1526652235,
    "name":"DASH-Venezuela-13-cities-1600-people",
    "payment_address":"Xfm6qvS2ugxL9u1V64SQeqbztYjqNU1qqx",
    "payment_amount":337,
    "start_epoch":1524076755,
    "type":1,
    "url":"https://www.dashcentral.org/p/DASH-Venezuela-13-cities-1600-people"
}
```

<h2 id="tocBlockchainProposalObject">BlockchainProposalObject</h2>

<a id="schemeblockchainproposalobject"></a>

|Name|Type|Description|
|---|---|---|
|Hash|String (HEX)|Proposal hash|
|CollateralHash|String (HEX)|Colateral Proposal hash|
|DataHex|String (HEX)|Hashed Proposal Data|
|DataObject|JSON|[Proposal data object](#schemeproposaldataobject)|
|CreationTime|Integer|Proposal creation time (epoch)|
|FundingResult|JSON|[VoteCountObject](#schemevotecountobject)|
|ValidResult|JSON|[VoteCountObject](#schemevotecountobject)|
|DeleteResult|JSON|[VoteCountObject](#schemevotecountobject)|
|EndorsedResult|JSON|[VoteCountObject](#schemevotecountobject)|

<a id="divider"></a>

> Example

```json
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

<h2 id="tocVoteCountObject">VoteCountObject</h2>

<a id="schemevotecountobject"></a>

|Name|Type|Description|
|---|---|---|
|AbsoluteYesCount|Integer|Number of Absolute Yes Votes|
|YesCount|Integer|Number of Yes Votes|
|NoCount|Integer|Number of No Votes|
|AbstainCount|Integer|Number of Abstain Votes|

<a id="divider"></a>

> Example

```json
{
    "AbsoluteYesCount":60,
    "YesCount":89,
    "NoCount":29,
    "AbstainCount":0
}
```

<h2 id="tocBlockObject">BlockObject</h2>

<a id="schemeblockobject"></a>

|Name|Type|Description|
|---|---|---|
|hash|String (HEX)|Hash of the block|
|size|Integer|Size of the block|
|height|Integer|Block height in the chain|
|version|Integer|Block version number|
|merkleroot|String (HEX)|256-bit hash based on all of the transactions in the block |
|tx|Array of Strings|Array of tx hashes in the block|
|time|Integer|Timestamp as seconds since 1970-01-01T00:00 UTC|
|nonce|Integer|32-bit number (starts at 0)|
|bits|String (Hex)|Current target in compact format|
|difficulty|Float|Difficulty at which the block was mined|
|chainwork|String (HEX)|Total number of hashes that are expected to have been necessary to produce the current chain|
|confirmations|Integer|Number of confirmations|
|previousblockhash|String (HEX)|256-bit hash of the previous block header|
|nextblockhash|String (HEX)|256-bit hash of the next block header|
|reward|String|Reward received|
|isMainChain|Boolean|Is the block part of the main chain|
|poolInfo|[PoolObject](#schemepoolobject)|Information about the pool on which the block was mined|

<a id="divider"></a>

> Example

```json
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

<h2 id="tocPoolObject">PoolObject</h2>

<a id="schemepoolobject"></a>

|Name|Type|Description|
|---|---|---|
|poolName|String|Name if the pool|
|url|String|Pool URL|

<a id="divider"></a>

> Example

```json
{
    "poolName":"AntMiner",
    "url":"https://bitmaintech.com/"
}
```

<h2 id="tocBlockHashObject">BlockHashObject</h2>

<a id="schemeblockhashobject"></a>

|Name|Type|Description|
|---|---|---|
|blockHash|String (HEX)|256-bit hash of the block|

<a id="divider"></a>

> Example

```json
{
    "blockHash":"0000000000000023d9d8fefa79adbad2df8cb0b61f7cb5c591f56d719f108159"
}
```

<h2 id="tocRawBlockObject">RawBlockObject</h2>

<a id="schemerawblockobject"></a>

|Name|Type|Description|
|---|---|---|
|rawblock|String (HEX)|Raw block data|

<a id="divider"></a>

> Example

```json
{
    "rawblock":"00000020015a0a48d971ecac6e07389d97f4a32322d76db6ea1e7b881c00000000000000fa1e14c79fb0e4e635c76850e4f2f78d4ce9e1f8f07c160eb9d3daa591848213443ad85ac77e4819d5ee4c4b0201000000010000000000000000000000000000000000000000000000000000000000000000ffffffff1f03b30f0d04443ad85a08a4e19361340100000c2f436f696e4d696e65504c2f0000000002de59f909000000001976a914ee5c2e032d02f6f7b08fcc21e0025f0baeb056b088acd759f909000000001976a9149d0d46f36bc90aef04803b53fb5f76c5c4325ced88ac0000000001000000010786d7d9f0dd99cde3bb01064f7de00994b0a5cd0c2b9cb20a829772380b98ec010000006a47304402206322cd2d5e63641c79ca9024c6999625ffc9abe906b2ad3384951676697eced4022063084ce0f306f5e808c04077663077eebe100d1a03f997ec2b95a784811debfc012102cce17aebe0a7984c1a95823df914152daee65bd64f2625d7f82eadde54521738feffffff0240420f00000000001976a9148a3b9c1327cf24f99f57d95cb0ecf10342a6417c88acccfe4d00000000001976a914e99064a50c9756e7dcef5eff03c4e35fd927bbc088aca10f0d00"
}
```

<h2 id="tocBlocksPaginatedObject">BlocksPaginatedObject</h2>

<a id="schemeblockspaginatedobject"></a>

|Name|Type|Description|
|---|---|---|
|block|Array of [BlockPagObject](#schemeblockpagobject)|Array of BlockPagObjects|
|length|Integer|Number of blocks|
|pagination|[PaginationObject](#schemepagintionobject)|Pagination metadata|

<a id="divider"></a>

> Example

```json
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

<h2 id="tocBlocksPagObject">BlocksPagObject</h2>

<a id="schemeblockpagobject"></a>

|Name|Type|Description|
|---|---|---|
|height|Integer|Block height in the chain|
|size|Integer|Size of the block|
|hash|String (HEX)|Hash of the block|
|time|Integer|Timestamp as seconds since 1970-01-01T00:00 UTC|
|txlength|Integer|Number of transactions in the block|
|poolInfo|[PoolObject](#schemepoolobject)|Information about the pool on which the block was mined|

<a id="divider"></a>

> Example

```json
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
}
```

<h2 id="tocPaginationObject">PaginationObject</h2>

<a id="schemepagintionobject"></a>

|Name|Type|Description|
|---|---|---|
|next|String|Next date in format YYYY-MM-DD|
|prev|String|Previous date in format YYYY-MM-DD|
|currentTs|Integer|Current timestamp since epoch|
|current|String|Current date in format YYYY-MM-DD|
|isToday|Boolean|Is current day from the request today|
|more|Boolean|Is there more than specified number of resources|
|moreTs|Integer|Timestamp since epoch|

<a id="divider"></a>

> Example

```json
{
      "next":"2018-04-04",
      "prev":"2018-04-02",
      "currentTs":1522799999,
      "current":"2018-04-03",
      "isToday":false,
      "more":true,
      "moreTs":1522800000
}
```

<h2 id="tocTransactionObject">TransactionObject</h2>

<a id="schemetransactionobject"></a>

|Name|Type|Description|
|---|---|---|
|txid|String (HEX)|Hash of the transaction|
|version|Integer|Version|
|locktime|Integer|Timestamp since epoch - time at which a particular transaction can be added to the blockchain.|
|vin|Array of [TxIN](#schemetxinobject)|Array of TxIN Objects - input transactions|
|vout|Array of [TxOUT](#schemetxoutobject)|Array of TxOUT Objects - output transactions|
|blockhash|String (HEX)|Hash of the block containing tx|
|blockheight|Integer|Height of the block containing the transaction|
|confirmations|Integer|Number of confirmations|
|time|Integer|Timestamp of the transaction since epoch|
|blocktime|Integer|Block timestamp since epoch|
|valueOut|Float|Output Value in DASH|
|size|Integer|Size of the tx in bytes|
|valueIn|Float|Input Value in DASH|
|fees|Float|Network fee for the transaction|
|isCoinBase|Boolean|Is the transaction general one created by miner/first in a block.|
|txlock|Boolean|If the transaction is sent and verified via Instant Send the value will be True|

<a id="divider"></a>

> Example

```json
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

<h2 id="tocTxIN">TxIN</h2>

<a id="schemetxinobject"></a>

|Name|Type|Description|
|---|---|---|
|txid|String (HEX)|Hash of the transaction|
|vout|Integer|The index of the output being spent within the transaction. Zero based.|
|sequence|Integer|Legacy 4-byte sequence number. A number intended to allow unconfirmed time-locked transactions to be updated before being finalized;|
|n|Integer ||
|scriptSig|[ScriptSig Object](#schemescriptsigobject)|Signature script - a script included in the input which complies with conditions set by ScriptPubKey in order to spend funds.|
|addr|String (HEX) |Address associated with the output of the previous transaction|
|valueSat|Integer|Value in duffs|
|value|Float|Value in DASH|
|doubleSpentTxID|String (HEX)|ID of the double spend tx; Double spends are not currently tracked|

<a id="divider"></a>

> Example

```json
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
}
```

<h2 id="tocTxOUT">TxOUT</h2>

<a id="schemetxoutobject"></a>

|Name|Type|Description|
|---|---|---|
|value|Float|Value in DASH|
|n|Integer|The index of the output being spent within the transaction. Zero based.|
|scriptPubKey|[ScriptPubKey Object](#shemescriptpubkeyobject)|A script included in outputs which sets the conditions that must be fulfilled for funds to be spent.|
|spentTxId|String (HEX) |Id of the transaction spending funds|
|spentIndex|Integer|The main purpose is to efficiently determine the address and amount of an input's previous output. The second purpose is to be able to determine which input spent an output.|
|spentHeight|Integer|Height of the block which includes the transaction|

<a id="divider"></a>

> Example

```json
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
```

<h2 id="tocScriptSigObject">ScriptSig</h2>

<a id="schemescriptsigobject"></a>

|Name|Type|Description|
|---|---|---|
|hex|String (HEX)|Serialised form of the script in hex encoding.|
|asm|String|De-serialised form of the script, with well-known tokens parsed as script tokens.|

<a id="divider"></a>

> Example

```json
{
    "hex":"483045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d012102dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228a",
    "asm":"3045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d[ALL] 02dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228a"
}
```

<h2 id="tocScriptPubKeyObject">ScriptPubKey</h2>

<a id="schemescriptpubkeyobject"></a>

|Name|Type|Description|
|---|---|---|
|hex|String (HEX)|Serialised form of the script in hex encoding.|
|asm|String|De-serialised form of the script, with well-known tokens parsed as script tokens.|
|address|Array of Strings|Public addresses|
|type|String|Type of the script|

<a id="divider"></a>

> Example

```json
{
    "hex":"76a914f9a86dca25067c5bf4a784aebd27080f3ec06f4c88ac",
    "asm":"OP_DUP OP_HASH160 f9a86dca25067c5bf4a784aebd27080f3ec06f4c OP_EQUALVERIFY OP_CHECKSIG",
    "addresses":
    [
        "XySurfMBRDFFXhwWnLRYk6LPzESyamG9c4"
    ],
    "type":"pubkeyhash"
}
```

<h2 id="tocTxBlockObject">TxBlockObject</h2>

<a id="schemetxblockobject"></a>

|Name|Type|Description|
|---|---|---|
|pagesTotal|Integer|Total number of pages.|
|txs|Array of [TransactionObject] (#schemetransactionobject)|Array of Transactions in the block|


<a id="divider"></a>

> Example

```json
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

<h2 id="tocTxAddressesObject">TxAddressesObject</h2>

<a id="schemetxaddressesobject"></a>

|Name|Type|Description|
|---|---|---|
|totalItems|Integer|Total number of transactions.|
|from|Integer|Start number (zero based index)|
|to|Integer|End number (zero based index)|
|items|Array of [TransactionObject] (#schemetransactionobject)|Array of Transactions|


<a id="divider"></a>

> Example

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

<h2 id="tocRawTxObject">RawTxObject</h2>

<a id="schemerawtxobject"></a>

|Name|Type|Description|
|---|---|---|
|rawtx|String (HEX)|Raw transaction|

<a id="divider"></a>

> Example

```json
{
    "rawtx":"0100000002c0fb5ea95c97cfaf7bd769bbb25ff850d47e311b7e865e0e74574c2242b0d8f2010000006b483045022100f52b7a776e0cd7c398fc794d46119a2b2a9273b88d9c044f79e694b5d1e97880022072eb161ca507eb5af20c63024404c44b0e691c45df6acdc4e2f7bf8229c84d4d012102dfc9f8086e802047a5cefb745c3191c84f57bed47816f07a7bbe41ab134e228affffffffef2852c0cd90eca6549952d09df44183b559b32b69486e225ae8cb845064512c010000006b483045022100be8867da8d87cccc9bda5c5430be3407be7d234d68edce900284f8381ece875a02204737ae7a055378e8f864d5549595afe5a1d8cb2f255f58fd846b9c300cdd27210121023e11be15d95f6e21698bd05084d67db390dd7a774a379322e2bbdf3801faa6a2ffffffff01df13591b000000001976a914f9a86dca25067c5bf4a784aebd27080f3ec06f4c88ac00000000"
}
```

<h2 id="tocTxSendObject">TxSendObject</h2>

<a id="schemetxsendobject"></a>

|Name|Type|Description|
|---|---|---|
|txid|String (HEX)|HASH of transmitted/sent transaction on the blockchain|

<a id="divider"></a>

> Example

```json
{
  "txid": "c7736a0a0046d5a8cc61c8c3c2821d4d7517f5de2bc66a966011aaa79965ffba"
}
```

<h2 id="tocAddressObject">AddressObject</h2>

<a id="schemeaddressobject"></a>

|Name|Type|Description|
|---|---|---|
|addrStr|String|A string representing the address|
|balance|Float|Current balance of the address in DASH|
|balanceSat|Integer|Current balance of the address in duffs|
|totalReceived|Float|Total amount in DASH received at the address|
|totalReceivedSat|Integer|Total amount in duffs received at the address|
|totalSent|Float|Total amount in DASH sent from the address|
|totalSentSat|Integer|Total amount in duffs sent from the address|
|unconfirmedBalance|Float|Unconfirmed balance of the address in DASH|
|unconfirmedBalanceSat|Integer|Unconfirmed balance of the address in duffs|
|unconfirmedTxApperances|Integer|Number of unconfirmed transactions in which address participated|
|txApperances|Integer|Number of transactions in which address participated|
|transactions|Array of Strings|Array of transaction transactions in which address participated|

<a id="divider"></a>

> Example

```json
{
    "addrStr":"XkLcLoji7FT8ALmpC3wCy6mTwPp3mMkonA",
    "balance":0,
    "balanceSat":0,
    "totalReceived":43.39433988,
    "totalReceivedSat":4339433988,
    "totalSent":43.39433988,
    "totalSentSat":4339433988,
    "unconfirmedBalance":0,
    "unconfirmedBalanceSat":0,
    "unconfirmedTxApperances":0,
    "txApperances":2,
    "transactions":
    [
        "58987677dcf85dd7fb949da5d283abddb561f131dfc554d95fa193dfa2242382",
        "62ffe74e1cbeb5f537830b199a7d0700cecd3ae5476ec0fbada12c5c1129fe66"
    ]
}
```

<h2 id="tocUnspentOutputObject">UnspentOutputObject</h2>

<a id="schemeunspentoutputobject"></a>

|Name|Type|Description|
|---|---|---|
|address|String|A string representing the address|
|txid|String (HEX)|Hash of the transaction|
|vout|Integer|Index of the output|
|scriptPubKey|String (HEX)|Script public key|
|amount|Float|Total unspent amount in DASH|
|satoshis|Integer|Total unspent amount in duffs|
|height|Integer|Height of the block in which the transaction is included|
|confirmations|Integer|Number of confirmations for the transaction|

<a id="divider"></a>

> Example

```json
{
    "address":"XoQWY27FwvCzyiLgpgxfDGHToBCehz8Dp4",
    "txid":"1606ffd2df5655b99ffc746d3a70d7f7e7ff6877b565a73f2138abc372409897",
    "vout":0,
    "scriptPubKey":"76a9148b82df11f146d6203ca9ce7a67e75f37444c408b88ac",
    "amount":0.03690789,
    "satoshis":3690789,
    "height":846205,
    "confirmations":10369
}
```

<h2 id="tocPaymentForwardObject">PaymentForwardObject</h2>

<a id="schemepaymentforwardobject"></a>

|Name|Type|Description|
|---|---|---|
|paymentforward_id|String|Payment forward unique id|
|payment_address|String|String representing payment address. DASH received to payment address are automatically forwarded to destination address (and optionally to commission address in case one is specified in a predefined way during payment forward creation.) |
|destination_address|String|String representing destination address. DASH received at payment address will be forwarded to the destination address.|
|commission_address|String|String representing commission address. In case a commission address is specified part of the payment will be forwarded to this address each time a payment is received at payment address, based on predefined parameters (commission_fee_percent or commission_fee_duffs)|
|commission_fee_percent|Float|Percentage of the payment which will be forwarded to commission address each time a payment is received at payment address. Min value 0.001. Max value 0.999. |
|commission_fee_duffs|Integer|Fixed amount in duffs which will be forwarded to commission address each time a payment is received at payment address.|
|created_date|String - Datetime in YYYY-MM-DDTHH:MM:SS.MMMZ format|Datetime of the creation of payment forward|
|callback_url|String|URL to which the notification about processed transactions is sent. Each time new payment is sent to payment address, notification is posted to this |
|mining_fee_duffs|Integer|Mining fee for the payment forward transaction. Default is 10 000. Maximum is 150 000. Minimum is 10 000. In case of set commission_fee_percent, mining fee is subtracted from commission amount.|
|processed_txs|Array of [ProcessedTxObject](#schemeprocessedtxobject)|Array of processed transactions by the payment forward. In case of retrieving a list of payment forwards, this parameter is omitted.|

<a id="divider"></a>

> Example

```json
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

<h2 id="tocEventObject">EventObject</h2>

<a id="schemeeventobject"></a>

|Name|Type|Description|
|---|---|---|
|event_id|String|Event unique id|
|event_type|String|Type of the event - ENUM {'ADDRESS', 'BLOCK', 'TRANSACTION', 'IX_TRANSACTION'}. Please refer to [Event Types](#eventtypesheader) for more details.|
|callback_url|String|The URL to which the notification will be posted once the event is triggered. The notification payload is delivered in JSON format by using method POST. The response status code must be set to 200 in order to acknowledge the notification delivery.|
|address|String|This parameter is present for `ADDRESS` event types. For other event types it's set to empty string. It represents an address for which you want to be notified on balance change.|
|confirmations|Integer|This parameter is present for `ADDRESS` event types. For other types it's set to 0. In case it's larger than 0, you will receive notifications for detected transactions involving specified address each time until detected transaction receives specified number of confirmations.|
|retry|Integer|How many retry cycles have been attempted. When it reaches 112 the event is disabled|
|created_date|String|Datetime when event has been created. Format: YYYY-mm-DDTHH:MM:SS.MMMZ|
|enabled|Integer|By default when an event is created it's set to 1. In case maximum number of retry cycles is reached, event is disabled and it's set to 0. If enabled is 0, event will not generate/deliver new notifications|

<a id="divider"></a>

> Example

```json
{
    "event_id": "ZjWQQkQzv91XqUiskvXv5wlK8bETvpdx",
    "event_type": "BLOCK",
    "callback_url": "http://blockvlf.requestcatcher.com/test",
    "address": "",
    "confirmations": 0,
    "retry": 0,
    "created_date": "2018-08-10T07:28:35.000Z",
    "enabled": 1
}
```

<h2 id="tocEventIdObject">EventIdObject</h2>

<a id="schemeeventidobject"></a>

|Name|Type|Description|
|---|---|---|
|event_id|String|Event unique id|

<a id="divider"></a>

> Example

```json
{
    "event_id": "ZjWQQkQzv91XqUiskvXv5wlK8bETvpdx"
}
```

<h2 id="tocProcessedTxObject">ProcessedTxObject</h2>

<a id="schemeprocessedtxobject"></a>

|Name|Type|Description|
|---|---|---|
|input_transaction_hash|String (HEX)|Hash of the input transaction. Input transaction is the transaction which occurs when a payment is sent to payment address.|
|received_amount_duffs|Integer|Amount received to payment forward destination address in duffs|
|transaction_hash|String (HEX)|Hash of the output transaction. Output transaction is the transaction which occurs when a payment is forwarded from payment address to destination address (and comission address in case one is specified for particular payment forward)|
|processed_date|String - Datetime in YYYY-MM-DDTHH:MM:SS.MMMZ format|Datetime when the payment was forwarded. |

<a id="divider"></a>

> Example

```json
{
    "input_transaction_hash":"6e3648463d26ee5af215fa3b61e976bf06cc7b1c6d2c034253967be65fc1c889",
    "received_amount_duffs":5000000,
    "transaction_hash":"7c89d485e06f295de6fb1d676311340be35148dfc1a54de13b57e785227da78f",
    "processed_date":"2018-04-13T11:04:19.000Z"
}
```

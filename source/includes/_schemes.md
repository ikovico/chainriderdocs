# Data Objects

<h2 id="tocBlockchainInfoObject">BlockchainInfoObject</h2>

<a id="schemeblockchaininfoobject"></a>

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


<h2 id="tocBlockchainDifficultyObject">BlockchainDifficultyObject</h2>

<a id="schemeblockchaindifficultyobject"></a>

> Example

```json
{
    "difficulty": 41610185.00844856
}
```

|Name|Type|Description|
|---|---|---|
|difficulty|Float|Current mining difficulty|


<h2 id="tocBlockchainBestBlockObject">BlockchainBestBlockObject</h2>

<a id="schemeblockchainbestblockobject"></a>

> Example

```json
{
    "bestblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
```

|Name|Type|Description|
|---|---|---|
|bestblockhash|String (HEX)|Hash of the best block|


<h2 id="tocBlockchainLastBlockObject">BlockchainLastBlockObject</h2>

<a id="schemeblockchainlastblockobject"></a>

> Example

```json
{
    "syncTipHash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5",
    "lastblockhash":"000000000000005d1718d7539c0a5313b7660b8e7c66d1dccc263a225f9848f5"
}
```

|Name|Type|Description|
|---|---|---|
|syncTipHash|String (HEX)|Hash of the block up to which the sync has been done|
|lastblockhash|String (HEX)|Hash of the last block|


<h2 id="tocBlockchainDataSyncObject">BlockchainDataSyncObject</h2>

<a id="schemeblockchaindatasyncobject"></a>

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

|Name|Type|Description|
|---|---|---|
|status|String|Sync status|
|blockChainHeight|Integer|Current blockchain height|
|syncPercentage|Integer|Sync status as persentage |
|height|Integer|Blockchain height (last block index)|
|error|String|Error description|
|type|String|Sync type|


<h2 id="tocBlockchainProposalsObject">BlockchainProposalsObject</h2>

<a id="schemeblockchainproposalsobject"></a>

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

|Name|Type|Description|
|---|---|---|
|Hash|String (HEX)|Proposal hash|
|DataObject|JSON|[Proposal data object](#schemeproposaldataobject)|
|AbsoluteYesCount|Integer|Number of Absolute Yes Votes|
|YesCount|Integer|Number of Yes Votes|
|NoCount|Integer|Number of No Votes|
|AbstainCount|Integer|Number of Abstain Votes|


<h2 id="tocProposalDataObject">ProposalDataObject</h2>

<a id="schemeproposaldataobject"></a>

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

|Name|Type|Description|
|---|---|---|
|end_epoch|Integer|End time (epoch)|
|name|String|Name of the proposal|
|payment_address|String|Payment address of the proposal|
|payment_amount|Integer|Proposal Amount in DASH|
|start_epoch|Integer|Start time (epoch)|
|type|Integer|Type of teh proposal|
|url|String|URL of the proposal|


<h2 id="tocBlockchainProposalObject">BlockchainProposalObject</h2>

<a id="schemeblockchainproposalobject"></a>

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


<h2 id="tocVoteCountObject">VoteCountObject</h2>

<a id="schemevotecountobject"></a>

> Example

```json
{
    "AbsoluteYesCount":60,
    "YesCount":89,
    "NoCount":29,
    "AbstainCount":0
}
```

|Name|Type|Description|
|---|---|---|
|AbsoluteYesCount|Integer|Number of Absolute Yes Votes|
|YesCount|Integer|Number of Yes Votes|
|NoCount|Integer|Number of No Votes|
|AbstainCount|Integer|Number of Abstain Votes|

# Introduction

## About the platform

[ChainRider](https://chainrider.io/) API is a cloud service for BTC and DASH blockchain management and exploration. We offer RESTful API services to enable other applications to easily and safely explore multiple blockchains. This includes receiving notifications of predefined events or transactions, customizing payment forwarding options, and other rich functionality for BTC and DASH payment processors. ChainRider supports cross-origin resource sharing (CORS), to allow for secure interactions within your application. Our services are often invaluable for distributed applications based on smart contracts. ChainRider integrates with the Ethereum smart contract oracle service, [Oraclize](http://www.oraclize.it/), in order to ease the use of BTC and Dash as the digital currency of choice for settling smart contract transactions. This enables notarization of data obtained from the ChainRider API and use of payment forwarding, event detection and other ChainRider services for full confidence within your smart contracts.

## Registration
Registration on the platform is straightforward and requires minimum effort from your side. You can register [here](https://chainrider.io) and obtain a free token for testing the API. Once the registration form has been submitted you will receive a verification email. Please verify your email address in order to speed up the onboarding process and start using the APIs

## Authentication

The ChainRider service uses web tokens for authentication. The token is passed as a parameter to all GET and DELETE requests. For all POST and PUT requests, token should be added in the request body.

The token could be obtained by signing up for an account at [ChainRider](https://chainrider.io).

The URL examples throughout this documentation use `<token>` as a placeholder. For these examples to work, you need to substitute the value with your own access token.


## API Resources and versions

All available resources follow the same URL pattern shown below:

  * `https://api-dot-chainrider.io/<API_VERSION>/<DIGITAL_CURRENCY>/<BLOCKCHAIN>/`

Currently, only `v1` version of ChainRider API exists. Any future updates to the API which might implicate breaking API compatibility will result in introducing new API versions accordingly. The API versioning will ensure maintaining backwards compatibility with existing integrations.

Currently supported blockchains are provided within the table below:

Digital currency | Blockchain | Base URL
-------------    | -------    | ---------------
Dash             | Main       | `https://api-dot-chainrider.io/v1/dash/main`
Dash             | Testnet    | `https://api-dot-chainrider.io/v1/dash/testnet`

## Token usage

The following API allows you to check current status of your web token including information about token usage on hourly and daily base.
This API does not follow abovementioned URL pattern as the same token is used for all resources.

<h3 id="postCheckToken">POST /v1/ratelimit/ </h3>

<a id="opIdpostCheckToken"></a>

*Get token usage*

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|token|body|String|True|Web token for which current rate limit and status is requested.|

<h3 id="response">Response</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[TokenUsageObject](#schemetokenusageobject)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<a id="divider">

> Code samples

```shell
curl -X POST https://api.chainrider.io/v1/ratelimit/ \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -D '<body_here>'
```

```php

    $body="<body_here>";
    $opts = array('http' =>
      array(
        'method'  => 'POST',
        'header'  => Content-Type: application/json\r\nAccept: application/json\r\n",
        'content' => $body
      )
    );
    $context  = stream_context_create($opts);
    $URL = "https://api.chainrider.io/v1/ratelimit/";
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
  url: 'https://api.chainrider.io/v1/ratelimit/',
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

result = RestClient.post 'https://api.chainrider.io/v1/ratelimit/',
         payload:<body_here>, headers: headers

p JSON.parse(result)
```

```python
import requests

headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://api.chainrider.io/v1/ratelimit/',
                  data=<body_here>, params={}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.chainrider.io/v1/ratelimit/");
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
    "token": "o2IEP1p50pe1jfDtz8osOc7RpWZkwbfp"
}
```

> Example response

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

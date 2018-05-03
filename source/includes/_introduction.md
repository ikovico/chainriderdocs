
# Introduction
## About the platform

ChainRider is a cloud service providing set of APIs for [DASH](https://www.dash.org/) digital currency management and exploring. The full benefits of the platform could be harvested by integrating with ChainRider API which is [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) based API. The main purpose of the API is to allow you to easily and securely explore DASH blockchain, receive different type of notifications from the DASH blockchain based on predefined events, forward your DASH digital currency payments, set up a payment processor, etc.
The cross-origin resource sharing is supported, allowing you to interact securely with the REST API from your client web application.

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

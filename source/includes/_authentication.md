
#Authentication

The ChainRider service uses web tokens for authentication. The token is passed as a parameter to all GET and DELETE requests. For all POST and PUT requests, token should be added in the request body.

The token could be obtained by signing up for an account at [ChainRider](https://chainrider.io).

The URL examples throughout this documentation use `<token>` as a placeholder. For these examples to work, you need to substitute the value with your own access token.

The base URL for ChainRider APIs is:

  * `https://api-dot-chainrider.io`

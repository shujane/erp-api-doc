# Authentication

The Liftians ERP API uses Basic HTTP authentication. Use your Liftian ERP API Key as the username and API Secret as the password. Your API Key and API Secret will be provide by Liftians.

The Authorization header is constructed as follows:

- Username (API KEY) and password (API Secret) are combined into a string "username:password".

- The resulting string is then encoded using the RFC2045-MIME variant of Base64, except not limited to 76 char/line

- The authorization method and a space i.e. "Basic " is then put before the encoded string. 

For example, if the API KEY given is `LiftiansAGV` and the API Secret is `ForTheWin` then the header is formed as follows:

- `Authorization: Basic TGlmdGlhbnNBR1Y6Rm9yVGhlV2lu`
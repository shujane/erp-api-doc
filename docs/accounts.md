# Intro

Account represent each user's client. It can be ShipStation, Whiplash, or any other data source.
Liftians ERP requires user to provide the account list. 
User should only create one account if they do not have multiple clients

*Please check the model page for the data model that is being used.*

# Push Multiple Accounts

**Method:** `POST`

**End Point:** `http://{server url}/api/v1/accounts`

**Request Data:**
```json
[
  {
    "accountNo": 100,
    "accountName": "Assembly",
    "description": "Assembly Whiplash",
    "active": true,
    "createDate": "2018-06-17T11:16:24.227",
    "modifyDate": "2018-06-17T11:16:24.327"
  },
  ...
]
```
**PK: accountNo**

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | success       |


# Get List of Accounts

**Method:** `GET`

**End Point:** `http://{server url}/v1/accounts`

**Response Data:**
```json
[
  {
    "accountNo": 100,
    "accountName": "CINDER",
    "description": "",
    "active": true,
    "createDate": "2018-06-17T11:16:24.227",
    "modifyDate": "2018-06-17T11:16:24.327"
  },
  ...
]
```

**With Parameter**

```
/accounts?accountNo={accountNo}
```

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | success       |

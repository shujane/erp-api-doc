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
[{
		"appId": 100,
		"userId": 100,
		"userNumber": "Assembly",
		"nickName": "Assembly",
		"password": "2333433",
		"userCard": "3243432A",
		"stat": 1,
		"createTime": "1580782707928",
		"updateTime": "1580782707928"
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

**End Point:** `http://{server url}/v1/accounts?appId=100`

**Response Data:**
```json
[
 {
		"appId": 100,
		"userId": 100,
		"userNumber": "Assembly",
		"nickName": "Assembly",
		"password": "2333433",
		"userCard": "3243432A",
		"stat": 1,
		"createTime": "1580782707928",
		"updateTime": "1580782707928"
	},
  ...
]
```



# Get account of Accounts

**Method:** `GET`

**End Point:** `http://{server url}/v1/accounts?appId=100&userId=100`

**Response Data:**
```json
{
    "id": 1,
    "appId": 100,
    "userId": 100,
    "userNumber": "Assembly",
    "userName": null,
    "nickName": "Assembly",
    "password": "23334353",
    "userCard": "3243432A",
    "stat": 1,
    "createTime": 1580782708000,
    "updateTime": 1580782708000
}
```


**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | success       |

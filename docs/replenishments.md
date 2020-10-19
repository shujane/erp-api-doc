# Intro
Each Replenishment item represent a replenishment bill.


*Please check the model page for the data model that is being used.*

# Push Multiple Replenishments

This endpoint can be used to create or update multiple replenishment bill in one request.

NOTE: **All items being pushed MUST also be in Liftians' ERP system**. Otherwise the item will be marked as "Cancel" until the product has been added.

**Method:** `POST`

**End Point:** `http://{server url}/api/v1/receive`

**Request Data:**
```json
[{
	"appId": 100,                        |int|NOT|
	"orderNo": 4999,                     |int|NOT|
	"customOrder": "944845530",          |String|NULL|
	"wareHouseId": 4999,                 |int|NOT|
	"priority": 1,                       |int|NOT|default =1|
	"orderStatus": "1",                  |String|NOT|default = "1"|
	"purchaseOrder": "232435454",  |String|NULL|
	"receiveDate": "2018-09-22T16:15:18",
	"createDate": "2017-04-22T09:15:18",
	"modifyDate": "2017-04-22T09:15:18",
	"items": [{
		"productId": "47902",
		"sku": "WAF1200",
		"name": "Removable Cooking Plates - Accessory - Waffle",
		"lotNo": "20180101",
		"locationCode": "D8V231432543",
		"productDate": "2016-04-21T00:00:00",
		"expiredDate": "2022-04-22T00:00:00",
		"area": 1,
		"caseNbr": ["33", "333"],
		"unitNum": 1,
		"quantity": 100
	}]
}]
```
**PK: (accountNo,requestNo)**

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | success       |

# Get List of Replenishments

Lists all Replenishmenet bill that is in Liftians ERP system.


**Method:** `GET`

**End Point:** `http://{server url}/api/v1/receive?appId=100&orderNo=4999`


**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | success       |
| `400`   | Invalid param |

```json
{
    "id": 6,
    "orderNo": 4999,
    "appId": 100,
    "wareHouseId": 4999,
    "purchaseOrder": "232435454",
    "priority": 1,
    "stationId": 0,
    "pallet": 0,
    "orderStatus": "1",
    "receiveDate": "2018-09-22 16:15:18",
    "createDate": "2017-04-22 09:15:18",
    "modifyDate": "2017-04-22 09:15:18",
    "items": [
        {
            "itemId": 6,
            "orderId": 4999,
            "productId": null,
            "sku": "WAF1200",
            "name": "Removable Cooking Plates - Accessory - Waffle",
            "lotNo": "20180101",
            "locationCode": null,
            "productDate": null,
            "expiredDate": null,
            "caseNbr": [
                "33",
                "333"
            ],
            "unitNum": 1,
            "quantity": 100,
            "area": 1,
            "processStatus": null,
            "updateTime": null
        },
        {
            "itemId": 6,
            "orderId": 4999,
            "productId": null,
            "sku": "WAF1201",
            "name": "Removable Cooking Plates - Accessory - Pancake",
            "lotNo": "20180101",
            "locationCode": null,
            "productDate": null,
            "expiredDate": null,
            "caseNbr": [
                "39392"
            ],
            "unitNum": 1,
            "quantity": 50,
            "area": 0,
            "processStatus": null,
            "updateTime": null
        }
    ]
}
   
```


# Cancel receive order

This endpoint can be used to cancel order

NOTE: **The task can be canceled before being assigned to the AGV.

**Method:** `GET`

**End Point:** `http://{server url}/api/v1/cancel/receive?appId=100&orderNo=4999`

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | success       |

```json
{
    "msgId": null,
    "result": "3",
    "data": "The current state does not allow this operation",
    "messageType": null
}
```
```json
{
    "msgId": null,
    "result": "1",
    "data": "Success",
    "messageType": null
}
```


# resume receive order

This endpoint can be used to resume order

**Method:** `GET`

**End Point:** `http://{server url}/api/v1/resume/receive?orderNo=552195`

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | success       |


```json
{
    "msgId": null,
    "result": "1",
    "data": "Success",
    "messageType": null
}
```

# Update receive order

This endpoint can be used to update order

NOTE: **The task can be canceled before being assigned to the AGV.

**Method:** `Post`

**End Point:** `http://{server url}/api/v1/update/receive`
**Request Data:**
```json
{
	"appId": 100,
	"orderNo": 4999,
	"wareHouseId": "4999",
	"priority": 2,
	"orderStatus": "1",
	"purchaseOrder": "232435454",
	"receiveDate": "2018-09-22T16:15:18",
	"createDate": "2017-04-22T09:15:18",
	"modifyDate": "2017-04-22T09:15:18",
	"items": [{
		"productId": "47902",
		"sku": "WAF12003",
		"name": "Removable Cooking Plates - Accessory - Waffle",
		"lotNo": "20180101",
		"locationCode": "D8V231432543",
		"productDate": "2016-04-21T00:00:00",
		"expiredDate": "2022-04-22T00:00:00",
		"area": 1,
		"caseNbr": ["33", "333"],
		"unitNum": 1,
		"quantity": 100
	}, {
		"productId": "47903",
		"sku": "WAF1202",
		"name": "Removable Cooking Plates - Accessory - Pancake",
		"lotNo": "20180101",
		"locationCode": "D8V231432543",
		"productDate": "2016-04-21T00:00:00",
		"expiredDate": "2022-04-22T00:00:00",
		"caseNbr": "39392",
		"unitNum": 1,
		"quantity": 50
	}]
}


```

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | success       |

```json
{
    "msgId": null,
    "result": "3",
    "data": "The current state does not allow this operation",
    "messageType": null
}
```
```json
{
    "msgId": null,
    "result": "1",
    "data": "Success",
    "messageType": null
}
```

# Intro

Once the order item is been picked. Liftians EPR system will not accept cancellation.

*Please check the model page for the data model that is being used.*

# Push Multiple Deliveries

This endpoint can be used to create or update multiple orders in one request.

**Method:** `POST`

**End Point:** `http://{server url}/api/v1/delivery`

**Request Data:**
```json
[{

	"appId": 100,
	"orderNo": 4999,
	"wareHouseId": "4999",
	"priority": 2,
	"orderStatus": "1",
	"orderDate": "2017-04-22 09:15:18",
	"createDate": "2017-04-22 09:15:18",
	"modifyDate": "2017-04-22 09:15:18",
	"items": [{
			"productId": "47902",
			"sku": "WAF1200",
			"name": "Removable Cooking Plates - Accessory - Waffle",
			"unitNum": 1,
			"quantity": 1
		},
		{
			"productId": "47903",
			"sku": "WAF1201",
			"name": "Removable Cooking Plates - Accessory - Pancake",
			"unitNum": 1,
			"quantity": 3
		}
	]
}]

```

**PK: (appId,orderNo)**
appId=100

**Result Data:**
```json
{
    "success": true,
    "recordProcessed": 1,
    "recordModified": -1,
    "recordRejected": 0,
    "startTime": 1580817115233,
    "endTime": 1580817115247,
    "desc": []
}
```

# Get List of Orders

Lists all orders that is in Liftians ERP system.


**Method:** `GET`

**End Point:** `http://{server url}/api/v1/delivery?orderNo=4999&appId=100`
**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | Success       |
| `400`   | Invalid param |

```json

{
    "id": 10,
    "appId": 100,
    "wareHouseId": 4999,
    "orderNo": 4999,
    "priority": 2,
    "stationId": 0,
    "orderStatus": "1",
    "orderDate": "2017-04-22 09:15:18",
    "createDate": "2017-04-22 09:15:18",
    "modifyDate": "2017-04-22 09:15:18",
    "items": [
        {
            "itemId": 10,
            "productId": 47902,
            "orderId": 4999,
            "sku": "WAF1200",
            "name": "Removable Cooking Plates - Accessory - Waffle",
            "quantity": 1,
            "unitNum": 1,
            "processStatus": null,
            "updateTime": null
        },
        {
            "itemId": 10,
            "productId": 47903,
            "orderId": 4999,
            "sku": "WAF1201",
            "name": "Removable Cooking Plates - Accessory - Pancake",
            "quantity": 3,
            "unitNum": 1,
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

**End Point:** `http://{server url}/api/v1/cancel/delivery?orderNo=4999&appId=100`

**PK: (accountNo,requestNo)**

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

**End Point:** `http://{server url}/api/v1/resume/delivery?orderNo=4999&appId=100`

**PK: (accountNo,requestNo)**

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

**End Point:** `http://{server url}/api/v1/update/delivery`

**Request Data:**
```json
{

	"appId": 100,
	"orderNo": 4999,
	"wareHouseId": "4999",
	"priority": 2,
	"orderStatus": "1",
	"orderDate": "2017-04-22 09:15:18",
	"createDate": "2017-04-22 09:15:18",
	"modifyDate": "2017-04-22 09:15:18",
	"items": [{
			"productId": "47902",
			"sku": "WAF1200",
			"name": "Removable Cooking Plates - Accessory - Waffle",
			"unitNum": 1,
			"quantity": 1
		},
		{
			"productId": "47903",
			"sku": "WAF1201",
			"name": "Removable Cooking Plates - Accessory - Pancake",
			"unitNum": 1,
			"quantity": 3
		}
	]
}
```

**PK: (accountNo,requestNo)**

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | success       |

```json
{
    "msgId": null,
    "result": null,
    "data": "UPDATE_ERROR",
    "messageType": null
}
```

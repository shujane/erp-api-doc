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
	"orderStatus": "awaiting_shipment",
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

**End Point:** `http://{server url}/api/v1/delivery?orderNo=4113822`
**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | Success       |
| `400`   | Invalid param |

```json

 {
    "msgId": null,
    "result": "1",
    "data": {
        "id": 4113760,
        "accountNo": 100,
        "orderNo": "4113760",
        "priority": 2,
        "orderStatus": "awaiting_shipment",
        "orderDate": "2019-06-19 00:00:00",
        "createDate": "2019-06-24 12:03:08",
        "modifyDate": "2019-06-24 12:03:08",
        "items": [
            {
                "itemId": 41011,
                "lineItemKey": null,
                "orderId": "4113760",
                "sku": "ORC-BTA-402-BK",
                "name": "Audio-Technica ATH-DSR9BT Wireless Over-Ear Headphones",
                "quantity": 1,
                "unitNum": 1,
                "processStatus": null,
                "pickedQty": null,
                "lotNo": null,
                "updateTime": null
            },
            {
                "itemId": 41015,
                "lineItemKey": null,
                "orderId": "4113760",
                "sku": "HDWD120UZSVA",
                "name": "Toshiba P300 2TB 7200RPM 64MB 3.5in SATA Hard Drive",
                "quantity": 1,
                "unitNum": 1,
                "processStatus": null,
                "pickedQty": null,
                "lotNo": null,
                "updateTime": null
            },
            {
                "itemId": 40310,
                "lineItemKey": null,
                "orderId": "4113760",
                "sku": "BD717673",
                "name": "Beyerdynamic Impacto Universal DAC/ AMP for iPhone/ Android",
                "quantity": 1,
                "unitNum": 1,
                "processStatus": null,
                "pickedQty": null,
                "lotNo": null,
                "updateTime": null
            }
        ]
    },
    "messageType": null
}

```

# Cancel receive order

This endpoint can be used to cancel order

NOTE: **The task can be canceled before being assigned to the AGV.

**Method:** `GET`

**End Point:** `http://{server url}/api/v1/cancel/delivery?orderNo=552195`

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

**End Point:** `http://{server url}/api/v1/resume/delivery?orderNo=552195`

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
	"accountNo": 100,
	"orderNo": "4113760",
	"priority": 3,
	"orderStatus": "0",
	"orderDate": "2019-06-19T00:00:00",
	"createDate": "2019-06-24T12:03:08",
	"modifyDate": "2019-06-24T12:03:08",
	"items": [{
		"lineItemKey": "41011",
		"sku": "ORC-BTA-402-BK",
		"name": "Audio-Technica ATH-DSR9BT Wireless Over-Ear Headphones",
		"unitNum": 1,
		"quantity": "1"
	}, {
		"lineItemKey": "41015",
		"sku": "HDWD120UZSVA",
		"name": "Toshiba P300 2TB 7200RPM 64MB 3.5in SATA Hard Drive",
		"unitNum": 1,
		"quantity": "1"
	}, {
		"lineItemKey": "40310",
		"sku": "BD717673",
		"name": "Beyerdynamic Impacto Universal DAC\/ AMP for iPhone\/ Android",
		"unitNum": 1,
		"quantity": "1"
	}]
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

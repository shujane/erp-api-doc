# Intro

Once the order item is been picked. Liftians EPR system will not accept cancellation.

*Please check the model page for the data model that is being used.*

# Push Multiple Deliveries

This endpoint can be used to create or update multiple orders in one request.

**Method:** `POST`

**End Point:** `http://{server url}/api/v1/delivery`

**Request Data:**
```json
[
  {
    "accountNo": 100,
    "orderNo": "CINDER4999",
    "priority": 2,
    "orderStatus": "awaiting_shipment",
    "orderDate": "2017-04-22 09:15:18",
    "createDate": "2017-04-22 09:15:18",
    "modifyDate": "2017-04-22 09:15:18",
    "items": [
      {
        "lineItemKey": "129193912",
        "sku": "WAF1200",
        "name": "Removable Cooking Plates - Accessory - Waffle",
        "unitNum": 1,
        "quantity": 1
      },
      {
        "lineItemKey": "129193913",
        "sku": "WAF1201",
        "name": "Removable Cooking Plates - Accessory - Pancake",
        "unitNum": 1,
        "quantity": 3
      }
    ]
  },
  ...
]

```

**PK: (accountNo,orderNo)**

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `201`   | Created       |
| `400`   | Invalid JSON format |

# Get List of Orders

Lists all orders that is in Liftians ERP system.


**Method:** `GET`

**End Point:** `http://{server url}/api/v1/delivery?orderNo=4113822`

**Response Data:**
```json
{
    "msgId": null,
    "result": "1",
    "data": {
        "id": 4113822,
        "accountNo": 100,
        "orderNo": "4113822",
        "priority": 2,
        "orderStatus": "awaiting_shipment",
        "orderDate": "2019-07-15 00:00:00",
        "createDate": "2019-07-15 15:35:57",
        "modifyDate": "2019-07-15 15:35:57",
        "items": [
            {
                "itemId": 47984,
                "lineItemKey": null,
                "orderId": "4113822",
                "sku": "AK-K7012-IL",
                "name": "AKRacing K7012 Gaming Chair Purple",
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
**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | Success       |
| `400`   | Invalid param |



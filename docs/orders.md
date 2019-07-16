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

Default page size is 20 and page number is 1.

**Method:** `GET`

**End Point:** `http://{server url}/api/v1/delivery?`

**Response Data:**
```json
{
  orders: [
    {
      "accountNo": 100,
      "orderNo": "CINDER4999",
      "priority": 2,
      "orderDate": "2017-04-22 09:15:18",
      "createDate": "2017-04-22 09:15:18",
      "modifyDate": "2017-04-22 09:15:18",
      "orderStatus": "awaiting_shipment",
      "items": [
        {
            "lineItemKey": "129193912",
            "sku": "WAF1200",
            "name": "Removable Cooking Plates - Accessory - Waffle",
            "unitNum": 1,
            "quantity": 1,
            "processStatus": "Finished",
            "pickedQty": 1
        },
        {
          "lineItemKey": "129193913",
          "sku": "WAF1201",
          "name": "Removable Cooking Plates - Accessory - Pancake",
          "unitNum": 1,
          "quantity": 3,
          "processStatus": "Being processed",
          "pickedQty": 2
		 }
      ],
      "binInfos": [
        {
          "binBarcode": "300001",
          "binTypeId": 1,
          "binTypeName": "Small Plastic Bin",
          "size": "12.5 X 11 X 17.5 inches",
          "colorName": "blue",
          "hexCode": "#778899"
        },
        ...
      ]
    },
    ...
  ]

}

```

**With Parameter**

Orders can be filtered by some parameters.
Filter with create date will return orders that is created after the input date.

```
/orders?pageSize={pageSize}
&pageNum={pageNum}
&uniqueId={uniqueId}
&accountNo={accountNo}
&orderNo={orderNo}
&createDate={createDate}
&processStatus={processStatus}
```

Example:
```
/orders?pageSize=3
&pageNum=2
&uniqueId=11112
&accountNo=99
&orderNo=CINDER4999
&createDate=2016-06-01 13:52
&processStatus=Finished
```


**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | Success       |
| `400`   | Invalid param |



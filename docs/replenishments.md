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
[
  {
    "accountNo": 100,
    "requestNo": "R1000",
    "priority": 1,
    "receiveDate": "2018-09-22T16:15:18",
    "createDate": "2017-04-22T09:15:18",
    "modifyDate": "2017-04-22T09:15:18",
    "items": [
      {
        "itemId": "129193912",
        "sku": "WAF1200",
        "name": "Removable Cooking Plates - Accessory - Waffle",
        "lotNo": "20180101", 
        "productDate": "2016-04-21T00:00:00",
        "expiredDate": "2022-04-22T00:00:00",
        "caseNbr": "124325",
        "unitNum": 1,
        "quantity": 100
      }, {
        "itemId": "129193913",
        "sku": "WAF1201",
        "name": "Removable Cooking Plates - Accessory - Pancake",
        "lotNo": "20180101", 
        "productDate": "2016-04-21T00:00:00",
        "expiredDate": "2022-04-22T00:00:00",
        "caseNbr": "39392",
        "unitNum": 1,
        "quantity": 50
      }
    ]
  }
]
```
**PK: (accountNo,requestNo)**

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | success       |

# Get List of Replenishments

Lists all Replenishmenet bill that is in Liftians ERP system.


**Method:** `GET`

**End Point:** `http://{server url}/api/v1/receive?orderNo=552195`

**Response Data:**
```json
{
    "msgId": null,
    "result": "1",
    "data": {
        "id": 552195,
        "orderNo": 552195,
        "accountNo": 100,
        "requestNo": null,
        "priority": 1,
        "orderStatus": null,
        "receiveDate": "2019-06-24 12:08:27",
        "createDate": "2019-06-24 12:08:27",
        "modifyDate": "2019-06-24 12:08:27",
        "items": [
            {
                "itemId": "39126",
                "orderId": "552195",
                "sku": "3588US3-BK",
                "name": "Orico 3588US3-BK 3.5 USB3.0 SATA HDD External Enclosure Black",
                "lotNo": "552193",
                "productDate": null,
                "expiredDate": null,
                "caseNbr": "1",
                "unitNum": 1,
                "quantity": 1,
                "processStatus": null,
                "updateTime": null
            },
            {
                "itemId": "40310",
                "orderId": "552195",
                "sku": "L95SS",
                "name": "Orico Aluminium L95SS Laptop CD-ROM Bay Drive Bracket For 2.5 SATA Drive ",
                "lotNo": "5522",
                "productDate": null,
                "expiredDate": null,
                "caseNbr": "1",
                "unitNum": 1,
                "quantity": 2,
                "processStatus": null,
                "updateTime": null
            },
            {
                "itemId": "44045",
                "orderId": "552195",
                "sku": "ORC-7688C3-BK",
                "name": "Orico Black Aluminium 7688C3 3.5\" Type-C External Hard Drive Enclosure",
                "lotNo": "552234",
                "productDate": null,
                "expiredDate": null,
                "caseNbr": "1",
                "unitNum": 1,
                "quantity": 1,
                "processStatus": null,
                "updateTime": null
            },
            {
                "itemId": "45393",
                "orderId": "552195",
                "sku": "ORC-BTA-402-BK",
                "name": "Orico Black BTA-402 USB Bluetooth 4.0 Adapter",
                "lotNo": "552277",
                "productDate": null,
                "expiredDate": null,
                "caseNbr": "1",
                "unitNum": 1,
                "quantity": 1,
                "processStatus": null,
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
| `200`   | success       |
| `400`   | Invalid param |

# Cancel receive order

This endpoint can be used to cancel order

NOTE: **The task can be canceled before being assigned to the AGV.

**Method:** `GET`

**End Point:** `http://{server url}/api/v1/cancel/receive?orderNo=552195`

**Request Data:**
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

**PK: (accountNo,requestNo)**

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | success       |

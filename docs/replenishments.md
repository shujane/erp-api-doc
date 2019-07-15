# Intro
Each Replenishment item represent a replenishment bill.


*Please check the model page for the data model that is being used.*

# Push Multiple Replenishments

This endpoint can be used to create or update multiple replenishment bill in one request.

NOTE: **All items being pushed MUST also be in Liftians' ERP system**. Otherwise the item will be marked as "Cancel" until the product has been added.

**Method:** `POST`

**End Point:** `http://{server url}/v1/replenishments`

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

Default page size is 20 and page number is 1.

**Method:** `GET`

**End Point:** `http://{server url}/v1/replenishments`

**Response Data:**
```json
{
  "replenishments": [
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
    },
    ...
  ],
  "total": 3,
  "page": 1,
  "pages": 1
}
```

**With Parameter**

```
/replenishments?pageSize={pageSize}
&pageNum={pageNum}
accountNo={accountNo}
&requestNo={requestNo}
&createDate={createDate}
&modifyDate={modifyDate}
&processStatus={processStatus}
```

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | success       |
| `400`   | Invalid param |

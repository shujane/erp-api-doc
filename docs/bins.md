# Intro


*Please check the model page for the data model that is being used.*

# Get Order from Bin barcode

Retreive the order's info which the bin is associated to.

**Method:** `GET`

**End Point:** `http://{server url}/v1/info/BinOrder/bin/{binBarcode}`

**Success Response Data:**
```json
{
  "success": true,
  "order": {
    "uniqueId": 1023,
    "accountNo": 100,
    "orderNo": "CINDER4999",
    "createDate": "2017-04-22 09:15:18",
    "priority": 2,
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
  }
}
```

**No Order Found Response**
{
  "success": false,
  "message": "No order is currently linked with this bin"
}

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | success       |
| `400`   | Invalid param |

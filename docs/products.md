# Intro

All the items in the orders must be added into the product table.

*Please check the model page for the data model that is being used.*

# Push Multiple Products

NOTE: **Any duplicate SKU record will be replaced by the later added record.**

**Method:** `POST`

**End Point:** `http://{server url}/api/v1/product`

**Request Data:**
```json
[
  {
    "productId":"2111",
    "accountNo":100,
    "sku":"AH-780-BLACK",
    "name":"Amour Home Diffuser Black Humidifier",
    "barcode":"A293EEH5",
    "length":3,
    "width":5,
    "height":3,
    "weight":10,
    "unitVolume":0.01,
    "active": true,
    "productImgUrl": "https://google.com",
    "packageImgUrl": "https://liftians.com",
    "createDate":"2017-08-21T08:32:22.443",
    "modifyDate":"2017-08-21T08:32:22.443"
  }
  ...
]
```

**PK: (accountNo,productId)**

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `201`   | created       |


# Get Product by productId and accountNo

**Method:** `GET`

**End Point:** `http://{server url}/api/v1/product`

**With Parameter**

```
/product?Id={productId}
&accountNo={accountNo}
```

**Response Data:**
```json
{
    "msgId": null,
    "result": "1",
    "data": {
        "uniqueId": null,
        "id": 47984,
        "accountNo": 100,
        "sku": "AK-K7012-IL",
        "name": "AKRacing K7012 Gaming Chair Purple",
        "barcode": "XXX47984",
        "length": 400.0,
        "width": 700.0,
        "height": 900.0,
        "weight": 28.0,
        "unitVolume": 0.01,
        "active": true,
        "productImgUrl": "",
        "packageImgUrl": "",
        "createDate": "2019-07-15 15:31:21",
        "modifyDate": "2019-07-15 15:31:21"
    },
    "messageType": null
}
```
**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | Success       |
| `404`   | Product Not Found |

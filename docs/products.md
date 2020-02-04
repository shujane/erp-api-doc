# Intro

All the items in the orders must be added into the product table.

*Please check the model page for the data model that is being used.*

# Push Multiple Products

NOTE: **Any duplicate appId,productId record will be replaced by the later added record.**

**Method:** `POST`

**End Point:** `http://{server url}/api/v1/product`

**Request Data:**
```json
[
  {
    "productId":"2111",
    "appId":100,
    "wareHouseId":100,
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


# Get Product by productId and appId

**Method:** `GET`

**End Point:** `http://{server url}/api/v1/product?appId=47984&productId=12123`

**Response Data:**
```json
{
	"msgId": null,
	"result": "1",
	"data": {
		"productId": "2111",
		"appId": 100,
		"wareHouseId": 100,
		"sku": "AH-780-BLACK",
		"name": "Amour Home Diffuser Black Humidifier",
		"barcode": "A293EEH5",
		"length": 3,
		"width": 5,
		"height": 3,
		"weight": 10,
		"unitVolume": 0.01,
		"active": true,
		"productImgUrl": "https://google.com",
		"packageImgUrl": "https://liftians.com",
		"createDate": "2017-08-21T08:32:22.443",
		"modifyDate": "2017-08-21T08:32:22.443"
	},
	"messageType": null
}
```
**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | Success       |
| `404`   | Product Not Found |

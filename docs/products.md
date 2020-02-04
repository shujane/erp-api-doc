# Intro

All the items in the orders must be added into the product table.

*Please check the model page for the data model that is being used.*

# Push Multiple Products

NOTE: **Any duplicate appId,productId record will be replaced by the later added record.**

**Method:** `POST`

**End Point:** `http://{server url}/api/v1/product`

**Request Data:**
```json
[{
		"productId": "47902",
		"appId": 100,
		"wareHouseId": 3,
		"sku": "PR1000ELAA",
		"name": "shujane testing 2",
		"barcode": "1234567",
		"length": "500",
		"width": "400",
		"height": "400",
		"weight": "20",
		"unitVolume": 31,
		"active": true,
		"productImgUrl": "shujane updated image",
		"packageImgUrl": "shujane packageImage",
		"createDate": "1580796651141",
		"modifyDate": "1580796651141"
	},
	{
		"productId": "47903",
		"appId": 100,
		"wareHouseId": 3,
		"sku": "11223",
		"name": "shujane testing 2",
		"barcode": "1234567",
		"length": "500",
		"width": "400",
		"height": "400",
		"weight": "20",
		"unitVolume": 31,
		"active": true,
		"productImgUrl": "shujane updated image",
		"packageImgUrl": "shujane packageImage",
		"createDate": "1580796651141",
		"modifyDate": "1580796651141"
	}
]
```

**PK: (accountNo,productId)**

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `201`   | created       |


# Get Product by productId and appId

**Method:** `GET`

**End Point:** `http://{server url}/api/v1/product?appId=100&productId=47902`

**Response Data:**
```json
{
    "msgId": null,
    "result": "1",
    "data": {
        "productId": 47902,
        "appId": 100,
        "wareHouseId": 3,
        "sku": "PR1000ELAA",
        "name": "shujane testing 2",
        "barcode": "1234567",
        "length": 500,
        "width": 400,
        "height": 400,
        "weight": 20,
        "unitVolume": 31,
        "active": true,
        "productImgUrl": "shujane updated image",
        "packageImgUrl": "shujane packageImage",
        "createDate": 1580796651000,
        "modifyDate": 1580796651000
    },
    "messageType": null
}
```
**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | Success       |
| `404`   | Product Not Found |

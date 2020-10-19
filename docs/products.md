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
		"productId": "47902",      |int|NOT|
		"appId": 100,              |int|NOT|default = 100|
		"wareHouseId": 3,          |int|NOT|default = 3|
		"sku": "PR1000ELAA",       |varchar|NOT|
		"name": "shujane testing 2",   |varchar|NOT|
		"barcode": "1234567",    |varchar|NOT|
		"length": 500,          |int|NOT|
		"width":  400,          |int|NOT|
		"height": 400,          |int|NOT|
		"weight": 20,           |int|NOT|
		"unitVolume": 31,       |int|NOT|
		"active": true,         |bool|NOT| 
		"productImgUrl": "https://assets.umart.com.au/newsite/images/201807/goods_img/35_P_1531698737088.jpg",  |String|null| 
		"packageImgUrl": "https://assets.umart.com.au/newsite/images/201807/goods_img/35_P_1531698737088.jpg",  |String|null| 
		"manageType": 1,      |int|null| 
		"createDate": "1580796651141", |timespan|null| 
		"modifyDate": "1580796651141"  |timespan|null| 
	}
]
```
**manageType Code**

|   Code  | Description   |
| :-----: | ------------- |
| 1  | One type of product is kept in only one locationBox |
| 2  | One type of product kept in multiple locationBox |

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
	"manageType": 1,
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

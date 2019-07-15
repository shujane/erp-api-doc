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

**End Point:** `http://{server url}/api/v1/products`

**With Parameter**

```
/products?Id={productId}
&accountNo={accountNo}
```

**Response Data:**

Object of Product

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | Success       |
| `404`   | Product Not Found |



# Get List of Products w/ parameter

Lists all products that is in Liftians ERP system.

Default page size is 20 and page number is 1.

**Method:** `GET`

**End Point:** `http://{server url}/v1/products`


**Response Data:**
```json
{
  "products": [
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
/products?pageSize={pageSize}
&pageNum={pageNum}
&accountNo={accountNo}
&active={active}
&createDate={createDate}
&modifyDate={modifyDate}
```

**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | Success       |
| `400`   | Invalid param |

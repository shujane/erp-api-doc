# Get List of Replenishments

Lists all Replenishmenet bill that is in Liftians ERP system.


**Method:** `GET`

**End Point:** `http://{server url}/api/v1/inventory/query?productId=552195&batch=12fdss`


**Response Code**

|   Code  | Description   |
| :-----: | ------------- |
| `200`   | success       |
| `400`   | Invalid param |

```json
 [
        {
            "id": 11410,
            "locationBarCode": "D8V212AF1L",
            "store": "umart",
            "batch": "5522",
            "productid": 40310,
            "quantity": 11000.0,
            "createtime": 1562681832000,
            "updatetime": 1562916370000,
            "remander": null
        },
        {
            "id": 11416,
            "locationBarCode": "D8V228AD3S",
            "store": "umart",
            "batch": "5522",
            "productid": 40310,
            "quantity": 2.0,
            "createtime": 1562917137000,
            "updatetime": 1562917137000,
            "remander": null
        },
        {
            "id": 11419,
            "locationBarCode": "D8V202BA4S",
            "store": "umart",
            "batch": "5522",
            "productid": 40310,
            "quantity": 11000.0,
            "createtime": 1562918934000,
            "updatetime": 1562924475000,
            "remander": null
        },
        {
            "id": 11420,
            "locationBarCode": "D8V223BD5S",
            "store": "umart",
            "batch": "5522",
            "productid": 40310,
            "quantity": 2.0,
            "createtime": 1562921436000,
            "updatetime": 1562921436000,
            "remander": null
        },
        {
            "id": 11421,
            "locationBarCode": "D8V219BE5S",
            "store": "umart",
            "batch": "5522",
            "productid": 40310,
            "quantity": 2.0,
            "createtime": 1562924242000,
            "updatetime": 1562924242000,
            "remander": null
        },
        {
            "id": 11422,
            "locationBarCode": "D8V210AB2S",
            "store": "umart",
            "batch": "5522",
            "productid": 40310,
            "quantity": 2.0,
            "createtime": 1563007079000,
            "updatetime": 1563007079000,
            "remander": null
        }
    ]
   
```

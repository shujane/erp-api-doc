# Model - Account

|     Name       | Data Type     | Description |
| ------------   | ------------- | ------------ |
| `appId`        | number        | Customer Id, ** please contact Raffles ** |
| `userId`       | number        | Unique number of the account ** accountNo Must be unique.** |
| `userNumber`   | string        | The name/alias/userName of the account |
| `nickName`     | string        | The nickName of the account |
| `password`     | string        | The password of the account  |
| `userCard`     | string        | Similar to username and password combination, can be used directly for login |
| `stat`         | boolean       | 1:Available 0: Unavailable |
| `createTime`   | long          | Timestamp demo:1581412741598 |
| `updateTime`   | long          | Timestamp |

# Model - Product

|     Name       | Data Type     | Description |
| ------------   | ------------- | ------------ |
| `productId `   | number        | Product Unique Id for a given accountNo ** (accountNo,productId) Must be unique.** |
| `appId`        | number        | Customer Id, ** please contact Raffles ** |
| `wareHouseId   | number        | In which warehouse is the current item used |
| `sku`          | string        | Stock keeping Unit. A user-defined value for a product to help identify the product. It is suggested that each product should contain a unique SKU. |
| `name`         | string        | Product name |
| `barcode`      | string        | Unique barcode to identify the product |
| `length`       | number        | **Optional** |
| `width`        | number        | **Optional** |
| `height`       | number        | **Optional** |
| `weight`       | number        | **Optional** |
| `unitVolume`   | number        | unit that can fit inside the box |
| `active`       | boolean       | Specifies whether or not the product is an active record. |
| `productImgUrl`| string        | Product image URL |
| `packageImgUrl`| string        | Package image URL |
| `createDate`   | string        |  |
| `modifyDate`   | string        |  |

# Model - Delivery

|     Name       | Data Type     | Description |
| ------------   | ------------- | ------------ |
| `appId`        | number        | Customer Id, ** please contact Raffles **  |
| `orderNo`      | string        | Specifies the order. ** (accountNo,orderNo) Must be unique.** |
| `wareHouseId   | number        | In which warehouse is the current item used |
| `orderStatus`  | string        | The order's status.   -1 = CANCEL, 0=UN_ASSIGN, 1=ASSIGN |
| `priority`     | number        | Specifies the priority of the order. Options: 1 to 10. **The larger the number the higher priority it has. i.e. 10 is the highest, 1 is the lowest** |
| `orderDate`    | string        |  |
| `createDate`   | string        |  |
| `modifyDate`   | string        |  |
| `items`        | OrderItem     | Array of purchased items. |

# Model - DeliveryItem

|     Name       | Data Type     | Description |
| ------------   | ------------- | ------------ |
| `lineItemKey`  | string        | Each line item should have an unique key.  i.e. productId |
| `sku`          | string        | product SKU. **Must be unique** |
| `name`         | string        | Product name |
| `quantity`     | number        | Quantity of packages in the order  |
| `unitNum`      | number        | Quantity of item per package |
**The following key are only for return data**
| `processStatus`| string        |  The process's status. Possible values: `Not processed`, `Finished`, `Waiting to process`, `Being processed`, `Cancel`.|
| `pickedQty`    | number        | Specifies the quantity of item being picked. If the status is `Finished` but the `pickedQty` is less than `quantity` |


# Model - BinInfo

|     Name       | Data Type     | Description |
| ------------   | ------------- | ------------ |
| `binBarcode`   | string        | Each bin has it's own unique ID |
| `binTypeId`    | number        | Specifies bin type with an ID |
| `binTypeName`  | string        | Bin type name |
| `size`         | string        | size dimentions of the bin |
| `colorName`    | string        | Specifies the color of the bin |
| `hexCode`      | number        | Hex code of the bin's color |

# Model - Replenishment

|     Name       | Data Type     | Description |
| ------------   | ------------- | ------------ |
| `accountNo`    | number        | Specifies which account this order belongs |
| `requestNo`    | string        | Specifies the requeset. **(accountNo,requestNo) Must be unique.** |
| `priority`     | number        | Specifies the priority of the replenishment. Options: 1 to 10. **The larger the number the higher priority it has. i.e. 10 is the highest, 1 is the lowest** |
| `createDate`   | string        |  |
| `modifyDate`   | string        |  |
| `items`        | ReplenishItem     | Array of replenishment items. |

# Model - ReplenishItem

|     Name       | Data Type     | Description |
| ------------   | ------------- | ------------ |
| `itemId`       | string        | Specifies the item with unique ID  i.e. productId |
| `sku`          | string        | Specifies the product. |
| `name`         | string        | Name of item |
| `lotNo`        | string        | The lot number of the item |
| `expiredDate`  | string        | i.e. "20201230". |
| `unitNum`      | number        | The unit of each item. Normally should be 1 for ecommerce |
| `quantity`     | number        | Quantity of item to be replenished. |
| `caseNbr`      | string        | Barcode or SerialNumber of item |

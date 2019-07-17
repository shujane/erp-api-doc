# Umart-Liftians data mapping

## Product

| Umart | Liftians | Note |
|-------|----------|-------|
|product_id | productId |Update and Select based on this value of this key|
|model|sku||
|upc|barcode||

 

## Orders

| Umart | Liftians | Note |
|-------|----------|-------|
|orderNo | orderNo |This is a uniqueId for a order request|
|product_id|lineItemKey||


## Replenishments
| Umart | Liftians | Note |
|-------|----------|-------|
|replenishmentID | requestNo |This is a uniqueId for a replenishment request|
|product_id|lineItemKey||
|serial number|caseNbr|

 

 



 
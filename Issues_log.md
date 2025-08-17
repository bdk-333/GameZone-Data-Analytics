# List of issues, their magnitude, solvablility

| issue                                     | feature                 | magnitude | solvalbe | resolution                                                                   |
| ----------------------------------------- | ----------------------- | --------- | -------- | ---------------------------------------------------------------------------- |
| Missing purchase dates                    | PURCHASE_TS             | 5         | N        | kept it as it is                                                             |
| duplicate orders                          | ORDER_ID                | 145       | Y        | removed duplicate 145 rows                                                   |
| spelling inconsistency (27in vs 27inches) | PROCUCT_NAME            | 61        | Y        | Replaced 27inches with 27in                                                  |
| missing prices                            | USD_PRICE               | 5         | Y        | Filled with the average price of the order product from the date or purchase |
| $0 price                                  | USD_PRICE               | 29        | Y        | Filled with the average price of the order product from the date or purchase |
| missing marketing channels                | MARKETING_CHANNEL       | 83        | Y        | Filled with 'unknown'                                                        |
| missing account creation methods          | ACCOUNT_CREATION_METHOD | 83        | Y        | Filled with 'unknown'                                                        |
| missing country code                      | COUNTRY_CODE            | 38        | N        | Kept it as it is                                                             |
| shipping data even before purchase data   | PURCHASE_TS and SHIP_TS | 2000      | N        | Kept it as it is, created a new df without these orders                      |
|                                           |                         |           |          |                                                                              |

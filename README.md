

https://github.com/Leangonplu/Ecommerce_Customer_Churn_Analysis_and_Prediction

### Features

CustomerID - Unique customer ID.
Desprezar

Churn - Churn flag (indicator of whether a customer has churned).
Target

Tenure - Duration of a customer's relationship with the organization.

PreferredLoginDevice - The device that a customer most often uses to log in.

CityTier - The tier of the city in which the customer lives.

WarehouseToHome - The distance from the warehouse to the customer's home.

PreferredPaymentMode - The customer's preferred payment method.

Gender - The gender of the customer.

HourSpendOnApp - The number of hours the customer spends on the mobile application or website.

NumberOfDeviceRegistered - The total number of devices registered for a particular customer.

PreferedOrderCat - The category of items that a customer most often ordered last month.

SatisfactionScore - The customer's satisfaction score for the service.

MaritalStatus - The marital status of the customer.

NumberOfAddress - The total number of addresses registered for a particular customer.


Complain - An indicator of whether the customer raised any complaints last month.

OrderAmountHikeFromlastYear - The percentage increase in the order amount from last year.

CouponUsed - The total number of coupons used by a customer last month.

OrderCount - The total number of orders placed by a customer last month.

DaySinceLastOrder - The number of days since the customer's last order.

CashbackAmount - The average cashback amount the customer received last month.


#### Colunas categóricas

- CityTier
- PreferedLoginDevice
- PreferredPaymentMode
- Gender
- PreferedOrderCat
- MaritalStatus
- Complain


#### Colunas numéricas

- Tenure

    - Missing = mediana

    - Outlier = remover

- WarehouseToHome

    - Missing = Mediana

    - Outliers = Remover (2)

- HourSpendOnApp

    - Missing = Mediana

    - Outliers = Nada

- NumberOfDeviceRegistered

    - Missing = n tem

    - Outliers = Nada

- SatisfactionScore

    - Tudo OK

- NumberOfAddress

    - Outliers = Percentil 95

- OrderAmountHikeFromlastYear

    - Missing = Mediana

    - Outliers = Percentil 95

- CouponUsed

    - Missing = Mediana

    - Outliers = Percentil 95

- OrderCount

    - Missing = Mediana

    - Outliers = Percentil 95

- DaySinceLastOrder

    - Outliers = Percentil 95

- CashbackAmount

    - Missing = Mediana

    - Outlier = Percentil 5 e 95




PreferredLoginDevice - The device that a customer most often uses to log in.

CityTier - The tier of the city in which the customer lives.

PreferredPaymentMode - The customer's preferred payment method.

Gender - The gender of the customer.

PreferedOrderCat - The category of items that a customer most often ordered last month.

SatisfactionScore - The customer's satisfaction score for the service.

MaritalStatus - The marital status of the customer.

NumberOfAddress - The total number of addresses registered for a particular customer.

Complain - An indicator of whether the customer raised any complaints last month.

CouponUsed - The total number of coupons used by a customer last month.

OrderCount - The total number of orders placed by a customer last month.

DaySinceLastOrder - The number of days since the customer's last order.
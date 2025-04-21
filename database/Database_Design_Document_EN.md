## Database Design Document

| No. | Table Name      | Chinese Name       |
| ---- | ------------- | -------------- |
| 1    | employee      | Employee Table         |
| 2    | category      | Category Table         |
| 3    | dish          | Dish Table         |
| 4    | dish_flavor   | Dish Flavor Table     |
| 5    | setmeal       | Set Meal Table         |
| 6    | setmeal_dish  | Set Meal-Dish Relation Table |
| 7    | user          | User Table         |
| 8    | address_book  | Address Table         |
| 9    | shopping_cart | Shopping Cart Table       |
| 10   | orders        | Orders Table         |
| 11   | order_detail  | Order Detail Table     |

### 1. employee

The employee table is an Employee Table used to store employee information within the merchant. The specific table structure is as follows:

| Field Name      | Data Type    | Description         | Remarks        |
| ----------- | ----------- | ------------ | ----------- |
| id          | bigint      | Primary Key         | Auto Increment        |
| name        | varchar(32) | Name         |             |
| username    | varchar(32) | Username       | Unique        |
| password    | varchar(64) | Password         |             |
| phone       | varchar(11) | Phone Number       |             |
| sex         | varchar(2)  | Gender         |             |
| id_number   | varchar(18) | ID Number     |             |
| status      | int         | Account Status     | 1normal 0locked |
| create_time | datetime    | Created Time     |             |
| update_time | datetime    | Last Modified Time |             |
| create_user | bigint      | Created By     |             |
| update_user | bigint      | Updated By |             |

### 2. category

The category table is a Category Table, which is used to store the classification information of commodities. The specific table structure is as follows:

| Field Name      | Data Type    | Description         | Remarks                 |
| ----------- | ----------- | ------------ | -------------------- |
| id          | bigint      | Primary Key         | Auto Increment                 |
| name        | varchar(32) | Category Name     | Unique                 |
| type        | int         | Category Type     | 1 Dish Classification  2Combo Classification |
| sort        | int         | Sort Field     | Sorting for categorical data   |
| status      | int         | Status         | 1able 0unable          |
| create_time | datetime    | Created Time     |                      |
| update_time | datetime    | Last Modified Time |                      |
| create_user | bigint      | Created By     |                      |
| update_user | bigint      | Updated By |                      |

### 3. dish

The dish table is a Dish Table, which is used to store information about dishes. The specific table structure is as follows:

| Field Name      | Data Type      | Description         | Remarks        |
| ----------- | ------------- | ------------ | ----------- |
| id          | bigint        | Primary Key         | Auto Increment        |
| name        | varchar(32)   | Dish Name     | Unique        |
| category_id | bigint        | Category ID       | Logical foreign keys    |
| price       | decimal(10,2) | Dish Price     |             |
| image       | varchar(255)  | Image Path     |             |
| description | varchar(255)  | Dish Description     |             |
| status      | int           | selling Status     | 1selling 0not selling |
| create_time | datetime      | Created Time     |             |
| update_time | datetime      | Last Modified Time |             |
| create_user | bigint        | Created By     |             |
| update_user | bigint        | Updated By |             |

### 4. dish_flavor

The dish_flavor table is a Dish Flavor Table, which is used to store the flavor information of dishes. The specific table structure is as follows:

| Field Name  | Data Type     | Description     | Remarks     |
| ------- | ------------ | -------- | -------- |
| id      | bigint       | Primary Key     | Auto Increment     |
| dish_id | bigint       | Dish ID   | Logical foreign keys  |
| name    | varchar(32)  | Flavor Name |          |
| value   | varchar(255) | Flavor Value   |          |

### 5. setmeal

The setmeal table is the Set Meal Table, which is used to store meal information. The specific table structure is as follows:

| Field Name      | Data Type      | Description         | Remarks        |
| ----------- | ------------- | ------------ | ----------- |
| id          | bigint        | Primary Key         | Auto Increment        |
| name        | varchar(32)   | Set Meal Name     | Unique        |
| category_id | bigint        | Category ID       | Logical foreign keys    |
| price       | decimal(10,2) | Set Meal Price     |             |
| image       | varchar(255)  | Image Path     |             |
| description | varchar(255)  | Set Meal Description     |             |
| status      | int           | selling Status     | 1selling 0not selling |
| create_time | datetime      | Created Time     |             |
| update_time | datetime      | Last Modified Time |             |
| create_user | bigint        | Created By     |             |
| update_user | bigint        | Updated By |             |

### 6. setmeal_dish

The setmeal_dish table is a Set Meal-Dish Relation Table, which is used to store the relationship between meal sets and dishes. The specific table structure is as follows:

| Field Name     | Data Type      | Description     | Remarks     |
| ---------- | ------------- | -------- | -------- |
| id         | bigint        | Primary Key     | Auto Increment     |
| setmeal_id | bigint        | Set Meal ID   | Logical foreign keys |
| dish_id    | bigint        | Dish ID   | Logical foreign keys |
| name       | varchar(32)   | Dish Name | Redundant fields |
| price      | decimal(10,2) | Dish Price | Redundant fields |
| copies     | int           | Dish Copies |          |

### 7. user

The user table is a User Table, which is used to store the information of C-end users. The specific table structure is as follows:

| Field Name      | Data Type     | Description               | Remarks |
| ----------- | ------------ | ------------------ | ---- |
| id          | bigint       | Primary Key               | Auto Increment |
| openid      | varchar(45)  | Unique ID of WeChat users |      |
| name        | varchar(32)  | User's Name           |      |
| phone       | varchar(11)  | Phone Number             |      |
| sex         | varchar(2)   | Gender               |      |
| id_number   | varchar(18)  | ID Number           |      |
| avatar      | varchar(500) | WeChat Avatar Path   |      |
| create_time | datetime     | Registration Time           |      |

### 8. address_book

The address_book table is an Address Table, which is used to store the delivery address information of C-end users. The specific table structure is as follows:

| Field Name        | Data Type     | Description         | Remarks           |
| ------------- | ------------ | ------------ | -------------- |
| id            | bigint       | Primary Key         | Auto Increment           |
| user_id       | bigint       | User ID       | Logical foreign keys       |
| consignee     | varchar(50)  | Consignee       |                |
| sex           | varchar(2)   | Gender         |                |
| phone         | varchar(11)  | Phone Number       |                |
| province_code | varchar(12)  | Province Code     |                |
| province_name | varchar(32)  | Province Name     |                |
| city_code     | varchar(12)  | City Code     |                |
| city_name     | varchar(32)  | City Name     |                |
| district_code | varchar(12)  | District Code     |                |
| district_name | varchar(32)  | District Name     |                |
| detail        | varchar(200) | Detailed Address | Specific to the house number   |
| label         | varchar(100) | Label         | Work, Home, School |
| is_default    | tinyint(1)   | Is Default Address | 1true 0false        |

### 9. shopping_cart

The shopping_cart table is a Shopping Cart Table, which is used to store the shopping cart information of C-end users. The specific table structure is as follows:

| Field Name      | Data Type      | Description         | Remarks     |
| ----------- | ------------- | ------------ | -------- |
| id          | bigint        | Primary Key         | Auto Increment     |
| name        | varchar(32)   | Product Name     |          |
| image       | varchar(255)  | Product Image Path |          |
| user_id     | bigint        | User ID       | Logical foreign keys |
| dish_id     | bigint        | Dish ID       | Logical foreign keys |
| setmeal_id  | bigint        | Set Meal ID       | Logical foreign keys |
| dish_flavor | varchar(50)   | Dish Flavor     |          |
| number      | int           | Product Quantity     |          |
| amount      | decimal(10,2) | Product Price     |          |
| create_time | datetime      | Created Time     |          |

### 10. orders

The orders table is an Orders Table, which is used to store the order data of C-end users. The specific table structure is as follows:

### 10. orders

The `orders` table stores order data for end-users. Table structure is as follows:

| Field Name              | Data Type      | Description                 | Remarks                                     |
|-------------------------|----------------|-----------------------------|---------------------------------------------|
| id                      | bigint         | Primary Key                 | Auto Increment                              |
| number                  | varchar(50)    | Order Number                |                                             |
| status                  | int            | Order Status                | 1 = Pending Payment, 2 = Pending Order, 3 = Accepted, 4 = Delivering, 5 = Completed, 6 = Canceled |
| user_id                 | bigint         | User ID                     | Logical Foreign Key                         |
| address_book_id         | bigint         | Address ID                  | Logical Foreign Key                         |
| order_time              | datetime       | Order Time                  |                                             |
| checkout_time           | datetime       | Checkout Time               |                                             |
| pay_method              | int            | Payment Method              | 1 = WeChat Pay, 2 = Alipay                  |
| pay_status              | tinyint        | Payment Status              | 0 = Unpaid, 1 = Paid, 2 = Refunded          |
| amount                  | decimal(10,2)  | Order Amount                |                                             |
| remark                  | varchar(100)   | Remarks                     |                                             |
| phone                   | varchar(11)    | Phone Number                |                                             |
| address                 | varchar(255)   | Detailed Address            |                                             |
| user_name               | varchar(32)    | User Name                   |                                             |
| consignee               | varchar(32)    | Consignee                   |                                             |
| cancel_reason           | varchar(255)   | Cancel Reason               |                                             |
| rejection_reason        | varchar(255)   | Rejection Reason            |                                             |
| cancel_time             | datetime       | Cancel Time                 |                                             |
| estimated_delivery_time | datetime       | Estimated Delivery Time     |                                             |
| delivery_status         | tinyint        | Delivery Status             | 1 = Immediate Delivery, 0 = Scheduled Time  |
| delivery_time           | datetime       | Delivery Time               |                                             |
| pack_amount             | int            | Packaging Fee               |                                             |
| tableware_number        | int            | Tableware Quantity          |                                             |
| tableware_status        | tinyint        | Tableware Quantity Status   | 1 = By Meal Count, 0 = Custom Quantity      |

### 11. order_detail

The order_detail table is an Order Detail Table, which is used to store the order details of C-end users. The specific table structure is as follows:

| Field Name      | Data Type      | Description         | Remarks     |
| ----------- | ------------- | ------------ | -------- |
| id          | bigint        | Primary Key         | Auto Increment     |
| name        | varchar(32)   | Product Name     |          |
| image       | varchar(255)  | Product Image Path |          |
| order_id    | bigint        | Order ID       | Logical foreign keys |
| dish_id     | bigint        | Dish ID       | Logical foreign keys |
| setmeal_id  | bigint        | Set Meal ID       | Logical foreign keys |
| dish_flavor | varchar(50)   | Dish Flavor     |          |
| number      | int           | Product Quantity     |          |
| amount      | decimal(10,2) | Product Price     |          |


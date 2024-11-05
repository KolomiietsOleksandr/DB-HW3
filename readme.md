# Practical assignment 3

## Beer Shop Database Schema

This is the database schema for the Beer Shop:

```mermaid
erDiagram
    CUSTOMERS {
        VARCHAR(36) ID PK
        VARCHAR(200) First_Name
        VARCHAR(200) Last_Name
        VARCHAR(200) Email
        VARCHAR(20) Phone
        VARCHAR(500) Address
        BOOLEAN Active
    }

    PRODUCTS {
        VARCHAR(36) ID PK
        VARCHAR(200) Name
        VARCHAR(500) Description
        VARCHAR(36) Category_ID FK
        VARCHAR(36) Supplier_ID FK
        DECIMAL(10, 2) Price
        DECIMAL(5, 2) Alcohol_Content
        VARCHAR(10) Volume
        INT Stock_Quantity
        BOOLEAN Active
    }

    CATEGORIES {
        VARCHAR(36) ID PK
        VARCHAR(200) Name
        VARCHAR(500) Description
    }

    SUPPLIERS {
        VARCHAR(36) ID PK
        VARCHAR(200) Name
        VARCHAR(200) Contact_Person
        VARCHAR(20) Phone
        VARCHAR(200) Email
        VARCHAR(500) Address
        BOOLEAN Active
    }

    ORDERS {
        VARCHAR(36) ID PK
        VARCHAR(36) Customer_ID FK
        DATE Order_Date
        VARCHAR(20) Status
        DECIMAL(10, 2) Total_Amount
    }

    ORDER_ITEMS {
        VARCHAR(36) ID PK
        VARCHAR(36) Order_ID FK
        VARCHAR(36) Product_ID FK
        INT Quantity
        DECIMAL(10, 2) Price
    }

    INVENTORY {
        VARCHAR(36) ID PK
        VARCHAR(36) Product_ID FK
        VARCHAR(36) Supplier_ID FK
        INT Quantity
        DATE Date_Added
    }

    CUSTOMERS ||--o{ ORDERS : "places"
    ORDERS ||--o{ ORDER_ITEMS : "contains"
    PRODUCTS ||--o{ ORDER_ITEMS : "included in"
    PRODUCTS }o--o{ SUPPLIERS : "provided by"
    PRODUCTS }o--|| CATEGORIES : "belongs to"
    PRODUCTS ||--o{ INVENTORY : "recorded in"
    SUPPLIERS ||--o{ INVENTORY : "supplies"
```

# Snow_Retail_Analytics_DWBI_Suite
A Retail Analytics Project based on a Snowflake Schema design. It transforms raw retail data into meaningful insights by integrating multiple dimensions like customers, products, orders, time, and store details. The project covers data cleaning, transformation, modeling, and visualization to support better business decisions.

## 🧱 Data Model Overview

This project uses a normalized dimensional model where some dimension tables (like `DIM_CUSTOMER`) reference additional dimension tables (like `DIM_LOYALTY_INFO`) for better organization, flexibility, and data integrity.

At the center of the model is the `FACT_ORDERS` table, which captures transactional sales data and is connected to multiple dimension tables.


### 📊 Tables and Their Roles

#### 🔹 FACT_ORDERS
The core fact table that holds transactional sales data.

**Key Fields:**
- `Order_ID` (Primary Key)
- `Customer_ID`, `Store_ID`, `Order_Date_ID`, `Product_ID` (Foreign Keys)
- `Quantity_Ordered`
- `Order_Amount`
- `Discount_Amount`
- `Shipping_Cost`
- `Total_Amount`

---

#### 🔹 DIM_CUSTOMER
Holds detailed customer information.

**Key Fields:**
- `Customer_ID` (Primary Key)
- `First_Name`, `Last_Name`, `Gender`, `DOB`, `Email`
- `Phone_Number`, `Address`, `City`, `State`, `Zip_Code`, `Country`
- `Loyalty_Program_ID` (Foreign Key)

---

#### 🔹 DIM_DATE
Provides temporal context for orders.

**Key Fields:**
- `Date_ID` (Primary Key)
- `Date`, `Day_Of_Week`, `Month`, `Quarter`, `Year`, `IsWeekend`

---

#### 🔹 DIM_PRODUCT
Contains product-related metadata.

**Key Fields:**
- `Product_ID` (Primary Key)
- `Product_Name`, `Category`, `Brand`, `Unit_Price`

---

#### 🔹 DIM_STORE
Stores store-specific details where the sales occur.

**Key Fields:**
- `Store_ID` (Primary Key)
- `Store_Name`, `Store_Type`, `Store_Opening_Date`
- `Address`, `City`, `State`, `Country`, `Region`, `Manager_Name`

---

#### 🔹 DIM_LOYALTY_INFO
Details of customer loyalty program participation.

**Key Fields:**
- `Loyalty_Program_ID` (Primary Key)
- `Program_Name`, `Program_Tier`, `Points_Accrued`

---

### 🔗 Relationships

- `FACT_ORDERS` references:
  - `DIM_CUSTOMER` via `Customer_ID`
  - `DIM_DATE` via `Order_Date_ID`
  - `DIM_PRODUCT` via `Product_ID`
  - `DIM_STORE` via `Store_ID`

- `DIM_CUSTOMER` references:
  - `DIM_LOYALTY_INFO` via `Loyalty_Program_ID`

This design ensures efficient slicing and dicing of sales data across different business perspectives like customer demographics, product hierarchy, store performance, and loyalty programs.

---

## 📐 Entity Relationship Diagram

Below is the ER diagram that illustrates the logical data model for the retail analytics project:

![image](https://github.com/user-attachments/assets/a4c4c9e5-a923-4946-afaf-d3e94a0fcad4)

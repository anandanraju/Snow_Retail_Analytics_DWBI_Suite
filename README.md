# Snow_Retail_Analytics_DWBI_Suite

Developed a Retail Analytics project utilizing a Snowflake Schema design to convert raw retail data into actionable insights. The project integrates key dimensions such as customers, products, orders, time, and store information. It involves end-to-end processes including data cleaning, transformation, modeling, and visualization to support strategic business decisions. 

The data model was built using a combination of sample datasets generated through Python libraries and tables sourced from Oracle Database, with well-defined relationships established between entities for effective analysis.

<img width="1660" height="1001" alt="Data Flow Diagram drawio (5)" src="https://github.com/user-attachments/assets/f50c9f92-b8fc-4eb7-b5fe-07d42abd0b77" />


## 🧱 Data Model Overview

This project uses a normalized dimensional model where some dimension tables reference additional dimension tables for better organization, flexibility, and data integrity.

At the center of the model is the `FACT_ORDERS` table, which captures transactional sales data and is connected to multiple dimension tables.


## ⚙  Languages and Tools involved: 

**Language**: **`Python`, `SQL`**

**Tools**: **`Oracle`, `Jupyter_Notebook`, `Excel`, `Snowflake_DB` ❄, `Power_BI`**  

## 📊 Tables and Their Roles

#### 🔹 FACT_ORDERS 
The core fact table that holds transactional sales data.

**`Order_ID`, `Customer_ID`, `Store_ID`, `Order_Date_ID`, `Product_ID`**, `Quantity_Ordered`, `Order_Amount`, `Discount_Amount`, `Shipping_Cost`, `Total_Amount`

#### 🔹 DIM_CUSTOMER 
Holds detailed customer information.

**`Customer_ID`**, `First_Name`, `Last_Name`, `Gender`, `DOB`, `Email`, `Phone_Number`, `Address`, `City`, `State`, `Zip_Code`, `Country`,**`Loyalty_Program_ID`**

#### 🔹 DIM_DATE 
Provides temporal context for orders.

**`Date_ID`**, `Date`, `Day_Of_Week`, `Month`, `Quarter`, `Year`, `IsWeekend`

#### 🔹 DIM_PRODUCT 
Contains product-related metadata.

**`Product_ID`**, `Product_Name`, `Category`, `Brand`, `Unit_Price`

#### 🔹 DIM_STORE 
Stores store-specific details where the sales occur.

**`Store_ID`**, `Store_Name`, `Store_Type`, `Store_Opening_Date`, `Address`, `City`, `State`, `Country`, `Region`, `Manager_Name`

#### 🔹 DIM_LOYALTY_INFO 
Details of customer loyalty program participation.

**Key Fields:**
- `Loyalty_Program_ID` (Primary Key)
- `Program_Name`, `Program_Tier`, `Points_Accrued`


## 🔗 Relationships

- `FACT_ORDERS` references:
  - `DIM_CUSTOMER` via `Customer_ID`
  - `DIM_DATE` via `Order_Date_ID`
  - `DIM_PRODUCT` via `Product_ID`
  - `DIM_STORE` via `Store_ID`

- `DIM_CUSTOMER` references:
  - `DIM_LOYALTY_INFO` via `Loyalty_Program_ID`

This design ensures efficient slicing and dicing of sales data across different business perspectives like customer demographics, product hierarchy, store performance, and loyalty programs.

## 📐 Entity Relationship Diagram

Below is the ER diagram that illustrates the logical data model for the retail analytics project:

<img width="1501" height="830" alt="Final_Data_Model drawio (2)" src="https://github.com/user-attachments/assets/508b687c-c3ad-4e85-9532-cd1779b2dbe4" />



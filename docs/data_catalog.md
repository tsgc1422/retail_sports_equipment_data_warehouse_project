# Data Catalog for Gold Layer

## Overview
The Gold Layer is the business-level data representation, structured to support analytical and reporting use cases. It consists of **dimension tables** and **fact tables** for specific business metrics.

---

### 1. **gold.dim_customers**
- **Purpose:** Stores customer details with demographic and geographic data.
- **Columns:**

| Column Name      | Data Type     | Description                                                                                   |
|------------------|---------------|-----------------------------------------------------------------------------------------------|
| customer_key     | INT           | Surrogate key uniquely identifying each customer record in the dimension table.               |
| customer_id      | INT           | Unique numerical identifier assigned to each customer.                                        |
| customer_number  | NVARCHAR(50)  | Alphanumeric identifier, used for tracking and referencing.         |
| first_name       | NVARCHAR(50)  | Customer's first name.                                         |
| last_name        | NVARCHAR(50)  | Customer's last name.                                                     |
| country          | NVARCHAR(50)  | Customer's origin country (e.g., 'Australia').                               |
| marital_status   | NVARCHAR(50)  | Customer's marital status (e.g., 'Married', 'Single').                              |
| gender           | NVARCHAR(50)  | Customer's gender (e.g., 'Male', 'Female', 'n/a').                                  |
| birthdate        | DATE          | Customer's date of birth, YYYY-MM-DD (e.g., 1971-10-06).               |
| create_date      | DATE          | Date and time when record was created. |

---

### 2. **gold.dim_products**
- **Purpose:** Provides information about the products and their attributes.
- **Columns:**

| Column Name         | Data Type     | Description                                                                                   |
|---------------------|---------------|-----------------------------------------------------------------------------------------------|
| product_key         | INT           | Surrogate key uniquely identifying each product record in the product dimension table.         |
| product_id          | INT           | A unique identifier assigned to the product for internal tracking and referencing.            |
| product_number      | NVARCHAR(50)  | A structured alphanumeric code, often used for categorization or inventory. |
| product_name        | NVARCHAR(50)  | Product's name, including key details such as type, color, and size.         |
| category_id         | NVARCHAR(50)  | Product unique category identifier.     |
| category            | NVARCHAR(50)  | Product classification (e.g., Bikes, Components) to group related items.  |
| subcategory         | NVARCHAR(50)  | More detailed product classification within the category.      |
| maintenance_required| NVARCHAR(50)  | Indicates whether the product requires maintenance (e.g., 'Yes', 'No').                       |
| cost                | INT           | Product price.                            |
| product_line        | NVARCHAR(50)  | Specific product line or series (e.g., Road, Mountain).      |
| start_date          | DATE          | When the product became available for sale or use. |

---

### 3. **gold.fact_sales**
- **Purpose:** Stores transactional sales data for analytical purposes.
- **Columns:**

| Column Name     | Data Type     | Description                                                                                   |
|-----------------|---------------|-----------------------------------------------------------------------------------------------|
| order_number    | NVARCHAR(50)  | A unique alphanumeric identifier for each sales order (e.g., 'SO54496').                      |
| product_key     | INT           | Surrogate key linking the order to the product dimension table.                               |
| customer_key    | INT           | Surrogate key linking the order to the customer dimension table.                              |
| order_date      | DATE          | Order placed date.                                                           |
| shipping_date   | DATE          | Order shipped date.                                          |
| due_date        | DATE          | Payment due date.                                                     |
| sales_amount    | INT           | Total monetary value of the sale (e.g., 25).   |
| quantity        | INT           | Number of units of the product ordered (e.g., 1).                       |
| price           | INT           | Price per product unit (e.g., 25).      |

# 📘 Data Dictionary for Gold Layer
 
**Layer:** Gold (Business-Level)  
**Purpose:** The Gold Layer is the business-level data representation, structured to support analytical and reporting use cases. It consists of **dimension tables** and **fact tables** used to model specific business metrics.

---

## 📁 Table: `gold.dim_customers`

**Purpose:** Stores customer details enriched with demographic and geographic data.

| Column Name      | Data Type     | Description                                                                 |
|------------------|---------------|-----------------------------------------------------------------------------|
| customer_key      | INT           | Surrogate key uniquely identifying each customer record.                   |
| customer_id       | INT           | Unique numerical identifier assigned to each customer.                     |
| customer_number   | NVARCHAR(50)  | Alphanumeric identifier used for tracking and referencing.                 |
| first_name        | NVARCHAR(50)  | Customer’s first name.                                                     |
| last_name         | NVARCHAR(50)  | Customer’s last/family name.                                               |
| country           | NVARCHAR(50)  | Country of residence (e.g., ‘Australia’).                                  |
| marital_status    | NVARCHAR(50)  | Marital status (e.g., ‘Married’, ‘Single’).                                |
| gender            | NVARCHAR(50)  | Gender (e.g., ‘Male’, ‘Female’, ‘n/a’).                                    |
| birthdate         | DATE          | Date of birth, formatted as YYYY-MM-DD (e.g., 1971-10-06).                  |
| create_date       | DATE          | Date and time when the customer record was created.                        |

---

## 📁 Table: `gold.dim_products`

**Purpose:** Provides information about the products and their attributes.

| Column Name      | Data Type     | Description                                                                 |
|------------------|---------------|-----------------------------------------------------------------------------|
| product_key       | INT           | Surrogate key uniquely identifying each product.                           |
| product_id        | INT           | Unique product identifier for internal use.                                |
| product_number    | NVARCHAR(50)  | Alphanumeric code used for categorization or inventory.                    |
| product_name      | NVARCHAR(50)  | Descriptive product name including key features (type, color, size).       |
| category_id       | NVARCHAR(50)  | Identifier linking to the product’s high-level category.                   |
| category          | NVARCHAR(50)  | Broad classification of the product (e.g., Bikes, Components).            |
| subcategory       | NVARCHAR(50)  | More specific classification within a category.                            |
| maintenance       | NVARCHAR(50)  | Indicates if the product requires maintenance (e.g., ‘Yes’, ‘No’).         |
| cost              | INT           | Base price of the product in whole currency units.                         |
| product_line      | NVARCHAR(50)  | Product line or series (e.g., Road, Mountain).                             |
| start_date        | INT           | Date the product became available (format not specified).                  |

---

## 📁 Table: `gold.fact_sales`

**Purpose:** Stores transactional sales data for analytical purposes.

| Column Name      | Data Type     | Description                                                                 |
|------------------|---------------|-----------------------------------------------------------------------------|
| order_number      | NVARCHAR(50)  | Unique alphanumeric sales order ID (e.g., ‘SO54496’).                       |
| product_key       | INT           | Surrogate key linking to the product dimension.                             |
| customer_key      | INT           | Surrogate key linking to the customer dimension.                            |
| order_date        | DATE          | Date the order was placed.                                                  |
| shipping_date     | DATE          | Date the order was shipped.                                                 |
| due_date          | DATE          | Payment due date for the order.                                             |
| sales_amount      | INT           | Total value of the sale per line item, in whole currency units.            |
| quantity          | INT           | Number of units ordered.                                                    |
| price             | INT           | Price per unit of product ordered.                                          |

---

> ℹ️ **Note:** All surrogate keys are used to maintain referential integrity between fact and dimension tables. Dates should follow the `YYYY-MM-DD` format where applicable.



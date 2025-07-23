## 🧾 Naming Standards for the Data Warehouse

This section describes how names are structured for different objects such as schemas, tables, views, columns, and procedures within this data warehouse project.

### 🔹 Structure Overview

* **Style**: All names follow `snake_case` lowercase with underscores between words.
* **Language**: English is used universally.
* **Clarity**: Avoid SQL reserved keywords to prevent conflicts.
_______________________________________________________________________________________________________________________________________
## 📘 Table Naming Guidelines

#### 🥉 Bronze Layer

* **Format**: `source_system_table_name`
* **Rule**: The table name mirrors the original name from the source system.
* **Example**: `crm_customer_info` → Refers to customer data from the CRM system.

#### 🥈 Silver Layer

* **Format**: Same as Bronze → `source_system_table_name`
* **Example**: `erp_invoice_data` → Cleaned and processed invoice data from the ERP system.

#### 🥇 Gold Layer

* **Format**: `category_entity`
* **Details**:

  * `category`: Functional role of the table (e.g., `dim`, `fact`, `report`)
  * `entity`: Business-relevant data description
* **Examples**:

  * `dim_products`: Contains product details
  * `fact_sales`: Holds transactional sales data
  * `report_sales_monthly`: Reporting table for monthly sales
________________________________________________________________________________________________________________________________________________________
## 🏷️ Column Naming Patterns

#### 🔑 Surrogate Keys

* **Format**: `entity_key`
* **Usage**: Primary keys in dimension tables
* **Example**: `customer_key` in `dim_customers`

#### ⚙️ Technical Metadata Columns

* **Format**: `dwh_columnname`
* **Prefix**: `dwh_` indicates system-managed fields
* **Example**: `dwh_load_date` → Timestamp of when the record was inserted
_______________________________________________________________________________________________________________________________________________________
## 🛠️ Stored Procedure Naming

* **Format**: `load_layer`
* **Layer** can be `bronze`, `silver`, or `gold`
* **Purpose**: Easily identify procedures based on which layer of the pipeline they support
* **Examples**:

  * `load_bronze`
  * `load_silver`

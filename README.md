# Snowflake Assignment

This repository contains the solution to the Snowflake assignment, including SQL scripts, steps, and instructions for completing the tasks as described in the assignment document.

---

## **Pre-requisites**
Before running the queries or following the steps, ensure you have the following set up:
1. A Snowflake trial account.
2. SnowSQL installed and configured.
3. Access to a functional cloud account (e.g., AWS, Azure, or GCP).
4. A public GitHub repository to store the backup of the worksheet.

---

## **General Instructions**
1. Create a Snowflake worksheet containing all queries required for this assignment.
2. Keep a backup of this worksheet in this public GitHub repository, as it cannot be recovered if your Snowflake trial account expires.
3. Use the provided steps as guidelines while working on the assignment.
4. Be aware of hidden Snowflake concepts that may be required to complete this assignment.
5. Add the following audit columns to all tables:
   - `elt_ts` (timestamp): The timestamp when the record was inserted into Snowflake.
   - `elt_by` (varchar): The name of the application inserting the record (can be hardcoded).
   - `file_name` (varchar): The name of the file used to insert data into the table.

---

## **Assignment Tasks**
### 1. **Role Hierarchy**
   Create roles as per the hierarchy below (assuming `Accountadmin` already exists):
   - **Accountadmin**
     - **Admin**
       - **Developer**
     - **PII**

### 2. **Warehouse Creation**
   - Create an M-sized warehouse named `assignment_wh` and use it for all queries.

### 3. **Switch Roles**
   - Switch to the `Admin` role.

### 4. **Database Creation**
   - Create a database named `assignment_db`.

### 5. **Schema Creation**
   - Create a schema named `my_schema`.

### 6. **Table Creation**
   - Create a table using a sample CSV dataset. Preferably, use a sample employee dataset to include PII-related columns (e.g., email, phone number). If no such dataset is available, treat any column as PII.

### 7. **Variant Table**
   - Create a variant version of the dataset for semi-structured data.

### 8. **Data Loading**
   - Load the dataset into:
     - An **internal stage**.
     - An **external stage** (e.g., an S3 bucket).

### 9. **Copy Data**
   - Use `COPY INTO` statements to load data:
     - Into one table from the internal stage.
     - Into another table from the external stage.

### 10. **Parquet File**
   - Upload an unrelated Parquet file to a stage and infer its schema.

### 11. **Query Staged Data**
   - Run a `SELECT` query on the staged Parquet file without loading it into a Snowflake table.

### 12. **Add Masking Policy**
   - Add masking policies to PII columns (e.g., email, phone number):
     - For users with the `Developer` role, these fields should display as `**masked**`.
     - For users with the `PII` role, the actual values should be visible.

**ACID-Compliant Database Management Using PostgreSQL**

**Project Overview**

This project explores the implementation of a database system that adheres to the four ACID properties—Atomicity, Consistency, Isolation, and Durability—using PostgreSQL. We designed and executed transactions that manage products, depots, and inventory stocks. The goal was to ensure that the database maintains data integrity and consistency during complex operations, such as insertions, updates, and deletions.

**Objective**

To create a robust relational database system that:

Handles complex operations across multiple tables.
Maintains consistency and integrity through cascading constraints.
Demonstrates real-world use cases for ACID properties.

**Database Schema**

The database consists of three tables:

1)Product: Stores product details.

Columns: prod_id (Primary Key), Pname, price.

2)Depot: Represents storage locations.

Columns: dep_id (Primary Key), addr, volume.

3)Stock: Links products and depots, managing inventory levels.

Columns: prod_id (Foreign Key), dep_id (Foreign Key), quantity.

**Cascading rules:**

ON UPDATE CASCADE: Updates propagate automatically.
ON DELETE CASCADE: Deletes remove dependent records.

**Key Features**

**ACID-Compliant Transactions:**

Atomic operations to ensure no partial changes occur.
Cascading rules for automatic updates and deletions.

**Transaction Management:**

**Isolation Level:**

Set to SERIALIZABLE to prevent concurrency issues.
Explicit BEGIN and COMMIT commands for grouped operations.

**Python Integration:**

Used psycopg2 to manage database transactions.
Included robust error handling and dynamic schema verification.

**Implemented Operations**

1. Insert Operations

**Added a new product (p100) and linked it to a depot (d2):**

INSERT INTO product VALUES ('p100', 'cd', 5);
INSERT INTO stock VALUES ('p100', 'd2', 50);

2. Update Operations
   
**Updated a product ID (p1 to pp1):**
**Updated a depot ID (d1 to dd1):**

UPDATE product SET prod_id = 'pp1' WHERE prod_id = 'p1';
UPDATE depot SET dep_id = 'dd1' WHERE dep_id = 'd1';

3. Delete Operations

**Deleted a product (pp1) and its associated inventory:**
**Deleted a depot (dd1) and its linked inventory:**

DELETE FROM product WHERE prod_id = 'pp1';
DELETE FROM depot WHERE dep_id = 'dd1';

**Challenges and Solutions**

**Foreign Key Constraints:**

**Problem:** Missing unique constraints on referenced columns.
**Solution:** Added primary keys to prod_id and dep_id.

**Cascading Conflicts:**

**Problem:** Manual updates to linked tables caused redundancy.
**Solution:** Introduced ON UPDATE CASCADE and ON DELETE CASCADE to handle these automatically.

**Error Handling:**

**Problem:** Transaction rollback on errors disrupted operations.
**Solution:** Implemented comprehensive error handling and schema validation.

**Real-World Applications**

This project demonstrates the practical implementation of ACID principles, which are critical in industries such as:

**E-commerce:** Ensuring inventory systems reflect product updates or deletions.
**Logistics:** Managing warehouse operations and stock levels.
**Banking:** Handling transactional data to prevent inconsistencies.

**How to Run**

1) Set Up the Database:

Install PostgreSQL.
Create the schema using the provided SQL commands.

2) Run Python Code:

Install the required Python libraries:

**pip install psycopg2 tabulate**

3) Verify Results:

Query the Stock table to see the final output:

**SELECT * FROM stock;**

**Key Takeaways**

Designing a database with cascading rules simplifies data management.

ACID principles ensure reliable and consistent data handling.

Proper schema design and error handling are crucial for real-world systems.

**Thank you for exploring our project!**

# PostgreSQL Transaction Management and ACID Properties

## 🚀 Portfolio Project: Database Management System

This project demonstrates the practical implementation of **ACID properties** (Atomicity, Consistency, Isolation, Durability) using PostgreSQL with Python. It showcases professional database transaction management for an inventory management system with products, depots, and stock levels.

**Author:** Harini Balaji | **Course:** CS623 Database Systems | **Date:** Spring 2026

---

## 📋 Overview

This project implements a robust relational database system that:

- ✅ Handles complex operations across multiple tables with referential integrity
- ✅ Maintains consistency through cascading constraints (ON UPDATE/DELETE CASCADE)
- ✅ Demonstrates real-world ACID transaction scenarios
- ✅ Includes performance benchmarking and transaction rollback demonstrations
- ✅ Shows professional error handling and code organization

## 🎯 Objectives

### Primary Goals

1. Design and implement a relational database schema with foreign key relationships
2. Demonstrate **Atomicity** through transaction rollback scenarios
3. Ensure **Consistency** with cascading constraints
4. Configure **Isolation** levels (SERIALIZABLE) for data integrity
5. Validate **Durability** by persisting committed transactions
6. Implement robust error handling and transaction management
7. Benchmark performance of commit vs rollback operations

### Real-World Applications

This implementation showcases critical database principles used in:
- 🛒 **E-commerce platforms:** Inventory and product management
- 🏦 **Banking:** Financial transactions and account balance
- 🚚 **Logistics:** Warehouse and supply chain operations
- 💻 **Distributed Systems:** Multi-database transaction coordination

---

## 🗂️ Database Schema

The database consists of three interconnected tables:

### 1. Product Table
- `prod_id` (Primary Key): Unique product identifier
- `Pname`: Product name
- `price`: Product price

### 2. Depot Table
- `dep_id` (Primary Key): Unique depot identifier
- `addr`: Depot address
- `volume`: Storage volume capacity

### 3. Stock Table
- `prod_id` (Foreign Key → Product)
- `dep_id` (Foreign Key → Depot)
- `quantity`: Stock quantity

### Entity-Relationship Diagram

```
┌──────────────┐         ┌──────────────┐
│   Product    │         │    Depot     │
│──────────────│         │──────────────│
│ prod_id (PK) │         │ dep_id (PK)  │
│ Pname        │         │ addr         │
│ price        │         │ volume       │
└──────┬───────┘         └──────┬───────┘
       │                        │
       │    ┌──────────────┐    │
       └───►│     Stock    │◄───┘
            │──────────────│
            │ prod_id (FK) │
            │ dep_id (FK)  │
            │ quantity     │
            └──────────────┘
```

**Cascading Rules:**
- `ON UPDATE CASCADE`: Changes to product/depot IDs automatically update Stock table
- `ON DELETE CASCADE`: Deletions automatically remove associated Stock entries

---

## 🛠️ Technology Stack

| Component | Version/Details |
|-----------|----------------|
| **Python** | 3.11+ |
| **PostgreSQL** | 15.x |
| **Database Adapter** | psycopg2 2.9.10 |
| **Data Visualization** | pandas, matplotlib |
| **Output Formatting** | tabulate |

## 🔑 Key Features

### ACID-Compliant Transactions
- **Atomic operations:** All-or-nothing execution with rollback capability
- **Cascading rules:** Automatic updates and deletions via foreign keys
- **Isolation Level:** SERIALIZABLE prevents concurrency issues
- **Durability:** Explicit COMMIT ensures data persistence

### Transaction Management
- Context managers for safe database connections
- Helper functions for query execution and display
- Performance benchmarking of commit vs rollback operations
- Robust error handling with automatic rollback

### Code Quality
- Modular, reusable functions
- Clean separation of concerns
- Professional documentation
- Performance analysis with visualizations

## 📝 Implemented Operations

The notebook demonstrates a complete transaction including:

### 1. Insert Operations
```sql
INSERT INTO product VALUES ('p100', 'cd', 5);
INSERT INTO stock VALUES ('p100', 'd2', 50);
INSERT INTO depot VALUES ('d100', 'Chicago', 100);
INSERT INTO stock VALUES ('p1', 'd100', 100);
```

### 2. Update Operations (with CASCADE)
```sql
UPDATE product SET prod_id = 'pp1' WHERE prod_id = 'p1';
-- Stock table automatically updated via CASCADE
UPDATE depot SET dep_id = 'dd1' WHERE dep_id = 'd1';
-- Stock table automatically updated via CASCADE
```

### 3. Delete Operations (with CASCADE)
```sql
DELETE FROM product WHERE prod_id = 'pp1';
-- Associated Stock entries automatically deleted
DELETE FROM depot WHERE dep_id = 'dd1';
-- Associated Stock entries automatically deleted
```

## 🎓 Key Takeaways

### Learning Outcomes

1. **Cascading Constraints** simplify data management
   - Automatic propagation eliminates manual synchronization
   - Reduces code complexity and potential bugs

2. **Transaction Management** ensures data integrity
   - Explicit COMMIT/ROLLBACK control provides flexibility
   - Atomicity prevents inconsistent states

3. **ACID Properties** are essential for production systems
   - Ensures reliable and consistent data handling
   - Critical for applications requiring data integrity

4. **Error Handling** enables graceful degradation
   - Proper exception catching and rollback
   - Maintains database state even on failures

---

## 🚀 How to Run

### Prerequisites

1. Install PostgreSQL 15+ from [postgresql.org](https://www.postgresql.org/download/)
2. Create the database schema using your preferred method
3. Ensure Python 3.11+ is installed

### Installation

```bash
# Install required Python packages
pip install psycopg2 pandas tabulate matplotlib
```

### Configuration

Update the database credentials in the notebook:

```python
DB_CONFIG = {
    "host": "localhost",
    "database": "postgres",
    "user": "your_username",
    "password": "your_password"
}
```

### Running the Notebook

1. Open `CS623 Project (2).ipynb` in Jupyter Notebook or JupyterLab
2. Run all cells sequentially
3. Review the output for ACID compliance verification

### Verify Results

Query the Stock table to see the final output:

```sql
SELECT * FROM stock;
```

---

## 📊 Portfolio Value

This project demonstrates:

- ✅ **Solid understanding** of database fundamentals
- ✅ **Practical experience** with PostgreSQL and Python
- ✅ **Professional code quality** with error handling and documentation
- ✅ **Analytical thinking** with performance benchmarking
- ✅ **Real-world application** of CS theory to business problems

---

## 📚 Related Concepts

- Database normalization
- Referential integrity
- Transaction isolation levels
- Concurrent transaction handling
- Database recovery

---

## 👤 About

**Harini Balaji**  
Master's in Data Science | Spring 2026

**Technologies:** PostgreSQL, Python, psycopg2, pandas, matplotlib

---

## 🙏 Acknowledgments

This project was developed as part of CS623 Database Systems coursework at [Your University], demonstrating practical understanding of ACID properties and transaction management.

---

**⭐ If you find this project useful, please consider giving it a star!**

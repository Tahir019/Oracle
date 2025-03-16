# Oracle SQL Notes

## Introduction to SQL (Structured Query Language)
SQL is a database language introduced by **IBM** to communicate with databases. Initially named **SEQUEL**, it was later renamed to **SQL**.

### Key Features:
- **Case Insensitive:** SQL queries can be written in uppercase, lowercase, or a mix of both.
- **Statements End with `;`**: Every SQL query should terminate with a semicolon (`;`).

#### Example Queries:
```sql
SELECT * FROM EMPLOYEE; -- Executed
select * from emp; -- Executed
SeLecT * From Emp; -- Executed
```

---

## Sub-languages of SQL
SQL is divided into several sub-languages based on their functionality:

### 1. Data Definition Language (DDL)
Used for defining and modifying database schema.

**Commands:**
- `CREATE`
- `ALTER`
  - MODIFY
  - ADD
  - RENAME
  - DROP
- `RENAME`
- `TRUNCATE`
- `DROP`

**New Features in DDL:**
- **Recycle Bin**
- **Flashback**
- **Purge**

### 2. Data Manipulation Language (DML)
Used for managing data within tables.

**Commands:**
- `INSERT`
- `UPDATE`
- `DELETE`

**New Features in DML:**
- **INSERT ALL**
- **MERGE**

### 3. Data Query Language (DQL) / Data Retrieval Language (DRL)
Used for retrieving data from the database.

**Command:**
- `SELECT`

### 4. Transaction Control Language (TCL)
Used for managing transactions.

**Commands:**
- `COMMIT`
- `ROLLBACK`
- `SAVEPOINT`

### 5. Data Control Language (DCL)
Used for access control.

**Commands:**
- `GRANT`
- `REVOKE`

---

## Data Definition Language (DDL) in Detail
### `CREATE` Statement
Used to create database objects like tables, views, synonyms, sequences, procedures, and functions.

#### Syntax:
```sql
CREATE TABLE <table_name> (
  <column_name1> <datatype> [size],
  <column_name2> <datatype> [size],
  ...
);
```

> **Note:** A single table can have up to **1000 columns** in Oracle.

#### Example:
```sql
CREATE TABLE students (
  student_id NUMBER(10),
  name VARCHAR2(50),
  age NUMBER(3)
);
```

**SQL Server vs Oracle Differences:**
| Feature     | SQL Server  | Oracle      |
|------------|------------|------------|
| `VARCHAR(MAX)` | Supported  | Error |
| `MONEY` | Supported  | Error |
| `VARCHAR2` | Error | Supported |
| `LONG` | Error | Supported |

---

## Data Types in Oracle
A data type specifies the type of data a column can store.

### 1. Numeric Data Types
| Data Type | Description |
|-----------|-------------|
| `INT` | Stores integer values. |
| `NUMBER(p, s)` | Stores both integer and floating-point values. |

#### Explanation:
- `p` (Precision) - Total number of digits (left + right of decimal).
- `s` (Scale) - Number of digits after the decimal point.

##### Example:
```sql
PRICE NUMBER(6,2)
```
- Stores values between **0.00** and **9999.99**
- `10000.00` → Error (Exceeds limit)

### 2. Character/String Data Types
Used for storing textual data.

| Data Type | Description |
|-----------|-------------|
| `CHAR(size)` | Fixed-length string (Max: 2000 bytes). |
| `VARCHAR2(size)` | Variable-length string (Max: 4000 bytes). |

#### String Representation Example:
```sql
-- Correct
INSERT INTO students (name) VALUES ('Smith');

-- Incorrect
INSERT INTO students (name) VALUES (Smith); -- Error
```

### Unicode vs Non-Unicode Data Types
| Type | Description |
|------|-------------|
| **Non-Unicode Data Types** | Stores English (localized) characters. (`CHAR`, `VARCHAR2`) |
| **Unicode Data Types** | Stores all national languages. (`NCHAR`, `NVARCHAR2`) |

> **Note:** `N` in `NVARCHAR2` represents **National Language Support (NLS)**.

---



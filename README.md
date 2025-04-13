 # Bookstore Database Project

## Overview

This project involved designing and implementing a MySQL database for a bookstore. The database is designed to store and manage information about books, authors, customers, orders, and related data. The visual representation of the database model is provided in the drawio document

## Team Members and Roles

* **Brian:** Scheme/Model Designer
* **Macharia:** Developer
* **Lissa:** Tester

## Project Objectives

The primary goal was to create a relational database that efficiently stores all necessary data for a bookstore's operations. This included designing tables, establishing relationships between them, and ensuring data integrity. The database should allow for quick retrieval and analysis of data.

## Tools and Technologies

* **MySQL:** For building and managing the database.
* **Draw.io:** For visualizing the database schema and relationships (The model is presented in `image.png`).

## Database Schema

The database includes the following tables with their respective columns and relationships:

* **book**:
    * book\_id (INT, PRIMARY KEY)
    * isbn (VARCHAR(20), UNIQUE)
    * title (VARCHAR(255), NOT NULL)
    * publication\_date (DATE)
    * language\_id (INT, FOREIGN KEY referencing `book_language`)
    * publisher\_id (INT, FOREIGN KEY referencing `publisher`)
    * pages (INT)
* **book\_author**:
    * book\_author\_id (INT, PRIMARY KEY)
    * book\_id (INT, FOREIGN KEY referencing `book`)
    * author\_id (INT, FOREIGN KEY referencing `author`)
* **author**:
    * author\_id (INT, PRIMARY KEY)
    * first\_name (VARCHAR(50), NOT NULL)
    * last\_name (VARCHAR(50), NOT NULL)
* **book\_language**:
    * language\_id (INT, PRIMARY KEY)
    * language\_name (VARCHAR(50), NOT NULL)
    * language\_code (VARCHAR(3), NOT NULL)
* **publisher**:
    * publisher\_id (INT, PRIMARY KEY)
    * publisher\_name (VARCHAR(100), NOT NULL)
* **customer**:
    * customer\_id (INT, PRIMARY KEY)
    * first\_name (VARCHAR(50), NOT NULL)
    * last\_name (VARCHAR(50), NOT NULL)
    * email (VARCHAR(100), UNIQUE)
    * phone\_number (VARCHAR(20))
    * address\_id (INT, FOREIGN KEY referencing `address`)
* **customer\_address**:
    * customer\_address\_id (INT, PRIMARY KEY)
    * customer\_id (INT, FOREIGN KEY referencing `customer`)
    * address\_id (INT, FOREIGN KEY referencing `address`)
    * address\_status\_id (INT, FOREIGN KEY referencing `address_status`)
* **address\_status**:
    * address\_status\_id (INT, PRIMARY KEY)
    * status\_name (VARCHAR(50), NOT NULL)
* **address**:
    * address\_id (INT, PRIMARY KEY)
    * street (VARCHAR(255), NOT NULL)
    * city (VARCHAR(100), NOT NULL)
    * state (VARCHAR(100))
    * zip\_code (VARCHAR(20))
    * county\_id (INT, FOREIGN KEY referencing `county`)
* **county**:
    * county\_id (INT, PRIMARY KEY)
    * county\_name (VARCHAR(100), NOT NULL)
* **order\_item**:
    * order\_item\_id (INT, PRIMARY KEY)
    * order\_id (INT, FOREIGN KEY referencing `order_header`)
    * book\_id (INT, FOREIGN KEY referencing `book`)
    * quantity (INT, NOT NULL)
    * price (DECIMAL(10, 2), NOT NULL)
* **order\_header**:
    * order\_id (INT, PRIMARY KEY)
    * customer\_id (INT, FOREIGN KEY referencing `customer`)
    * order\_date (DATE, NOT NULL)
    * shipping\_address\_id (INT, FOREIGN KEY referencing `address`)
    * billing\_address\_id (INT, FOREIGN KEY referencing `address`)
    * shipping\_method\_id (INT, FOREIGN KEY referencing `shipping_method`)
    * order\_status\_id (INT, FOREIGN KEY referencing `order_status`)
* **shipping\_method**:
    * shipping\_method\_id (INT, PRIMARY KEY)
    * method\_name (VARCHAR(100), NOT NULL)
    * shipping\_cost (DECIMAL(10, 2), NOT NULL)
* **order\_history**:
    * history\_id (INT, PRIMARY KEY)
    * order\_id (INT, FOREIGN KEY referencing `order_header`)
    * order\_status\_id (INT, FOREIGN KEY referencing `order_status`)
    * change\_date (TIMESTAMP, DEFAULT CURRENT\_TIMESTAMP)
* **order\_status**:
    * order\_status\_id (INT, PRIMARY KEY)
    * status\_name (VARCHAR(50), NOT NULL)
* **cart\_item**:
    * cart\_item\_id (INT, PRIMARY KEY)
    * customer\_id (INT, FOREIGN KEY referencing `customer`)
    * book\_id (INT, FOREIGN KEY referencing `book`)
    * quantity (INT, NOT NULL)
    * added\_date (TIMESTAMP, DEFAULT CURRENT\_TIMESTAMP)

## SQL Code

The SQL code for creating the database and tables is provided in the sql file. It includes the following operations:

* Creating the database `Tech_Pack_Bookstore`.
* Creating tables with appropriate data types and constraints as defined in the schema.
* Defining primary and foreign keys to establish relationships between tables.
* Inserting sample data into the tables for testing purposes.

## Submission

The project is submitted as a GitHub repository.

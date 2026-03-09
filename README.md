# Warehouse Inventory & Orders Management

**Warehouse Inventory & Orders Management** is a Java-based enterprise application designed to automate the processing of client orders within a warehouse environment. The system manages products, clients, and transactions using a **Layered Architecture** and advanced **Java Reflection** techniques to interact dynamically with a relational database.

## Features

### N-Tier Layered Architecture
* **Decoupled Structure:** Designed with four distinct layers—Presentation, Business Logic, Data Access, and Model—to ensure modularity and ease of maintenance.
* **Object-Oriented Design:** Adheres to SOLID principles, ensuring that each class has a single responsibility and methods are concise (max 30 lines).

### Dynamic Data Access (Reflection API)
* **Generic DAO Engine:** Utilizes **Java Reflection** to create a universal Data Access Object. It dynamically generates SQL queries (`SELECT`, `INSERT`, `UPDATE`, `DELETE`) at runtime based on the object's class.
* **Automated UI Tables:** A reflection-based method automatically extracts object properties to generate `JTable` headers and rows, decoupling the GUI from specific data models.

### Order Processing & Inventory Control
* **Stock Validation:** Automatically checks product availability before finalizing an order. If a product is under-stocked, an error message is displayed to the user.
* **Automated Updates:** Decrements product quantities in real-time upon successful order placement.
* **Transaction Auditing:** Uses **Java Records** to create immutable **Bill** objects for each order, which are stored in a dedicated Log table for legal and audit compliance.

### Management Interfaces (GUI)
* **Client Management:** Dedicated window for CRUD operations (Create, Read, Update, Delete) on client data.
* **Product Management:** Interface for maintaining the product catalog, including price and stock levels.
* **Order Placement:** A specialized module where users can select clients and products to generate valid transactions.

## Technologies Used

### Backend – Java
* **Reflection API:** Used for dynamic SQL generation and automated UI populating, mimicking ORM (Object-Relational Mapping) functionality.
* **JDBC:** Manages the low-level connection and communication with the MySQL database.
* **Lambda & Streams:** Utilized for efficient list processing and data filtering within the business layer.
* **Java Records:** Ensures data immutability for billing and logging purposes.

### Database – MySQL
* **Relational Storage:** Uses a structured database with minimum three core tables: `Client`, `Product`, and `Order`, along with a `Log` table for bills.
* **SQL Dump:** Includes a complete schema script for database creation and initial population.

### Frontend – Java Swing
* **Interactive Interface:** Built using Java Swing to provide a responsive desktop experience.
* **Data Visualization:** Uses `JTable` components that are dynamically updated to reflect the current state of the database.

## System Architecture
The application is organized into the following mandatory packages:
* `org.example.dataAccessLayer`: Contains the generic DAO and DB connection logic.
* `org.example.businessLayer`: Implements validators and the core order processing logic.
* `org.example.model`: Defines the data structures and Java Records.
* `org.example.presentation`: Manages the GUI components and user interactions.

## How to Run
1. **Database Setup:** Execute the provided `.sql` dump file in your MySQL environment to create the schema.
2. **Configuration:** Ensure the JDBC connection string in the `dataAccessLayer` matches your local MySQL credentials.
3. **Compile & Run:** Use any Java IDE (IntelliJ/Eclipse) to run the main application class.

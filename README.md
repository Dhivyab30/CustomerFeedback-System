# CustomerFeedback-System

The Customer Feedback System is a Java-based application developed using Hibernate ORM to demonstrate how customer feedback can be efficiently stored, managed, and retrieved from a relational database.
This project models a one-to-many relationship between customers and their feedbacks — where each customer can provide multiple feedback entries. It follows the DAO (Data Access Object) design pattern for clean separation between business logic and database operations.

✓ Create and store customer information (name, email).

✓ Record multiple feedback messages and ratings for each customer.

✓ Automatically manage relationships using Hibernate cascading.

✓ Retrieve and display all stored customers and feedback data.

The project is ideal for learning Hibernate configuration, entity mapping (One-to-Many / Many-to-One), and CRUD operations using annotations or XML mapping.
It can serve as a foundation for more advanced systems such as customer relationship management (CRM), review management platforms, or e-commerce feedback modules.

🚀 Getting Started:
--------------------
The Customer Feedback System is a Hibernate-based Java application that allows customers to submit feedback and ratings.
It demonstrates a One-to-Many relationship between Customer and Feedback entities using Hibernate ORM for database interaction.

⚙️ Prerequisites:
------------------

✓ Java Development Kit (JDK) – Version 8 or higher.

✓ Apache Maven – For building and managing dependencies.

✓ MySQL Database Server – For data persistence.

✓ Hibernate ORM – Integrated through Maven dependencies.

✓ IDE (Recommended) – Eclipse / IntelliJ IDEA / VS Code.

🧰 Requirement Versions / Tools:
---------------------------------

Tool / Technology	Version	Purpose
Java	8+	Core programming language
Maven	3.6+	Build automation and dependency management
Hibernate	5.6+	ORM framework
MySQL	8.0+	Relational database
MySQL Connector/J	8.0+	JDBC driver for MySQL
IDE	Any	Development environment.

🗄️ Database Table Required:
----------------------------
Database Name: customer_feedback_db
Table 1: Customer
Column	Type	Constraints
id	INT	Primary Key, Auto Increment
name	VARCHAR(100)	NOT NULL
email	VARCHAR(100)	UNIQUE, NOT NULL
Table 2: Feedback
Column	Type	Constraints
id	INT	Primary Key, Auto Increment
message	VARCHAR(255)	NOT NULL
rating	INT	CHECK (rating BETWEEN 1 AND 5)
customer_id	INT	Foreign Key → Customer(id)

⚙️ Installation Steps:
-----------------------

Create MySQL database

CREATE DATABASE customer_feedback_db;


Update Hibernate configuration
In src/main/resources/hibernate.cfg.xml, set:

<property name="hibernate.connection.url">jdbc:mysql://localhost:3306/customer_feedback_db</property>
<property name="hibernate.connection.username">root</property>
<property name="hibernate.connection.password">yourpassword</property>


Build the project using Maven

mvn clean install

🧩 Example Maven Dependencies:
-------------------------------

<dependencies>
    <!-- Hibernate Core -->
    <dependency>
        <groupId>org.hibernate</groupId>
        <artifactId>hibernate-core</artifactId>
        <version>5.6.15.Final</version>
    </dependency>

    <!-- MySQL Connector -->
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-j</artifactId>
        <version>8.0.33</version>
    </dependency>

    <!-- JPA API -->
    <dependency>
        <groupId>javax.persistence</groupId>
        <artifactId>javax.persistence-api</artifactId>
        <version>2.2</version>
    </dependency>

    <!-- Logging (Optional) -->
    <dependency>
        <groupId>org.slf4j</groupId>
        <artifactId>slf4j-simple</artifactId>
        <version>1.7.36</version>
    </dependency>
</dependencies>

▶️ Usage / Running the Application:
------------------------------------
Run the MainApp.java file.

Hibernate will:

Create tables automatically (if hibernate.hbm2ddl.auto is set to update)

Insert the customer and feedback records

Retrieve and display all stored data.

🔄 Example Flow:

1️⃣ Create a Customer
Customer("Dhivya", "dhivya@example.com")

2️⃣ Add Feedbacks

“Excellent service!” (Rating: 5)

“Good experience.” (Rating: 4)

3️⃣ Save via DAO

Saving customer automatically saves feedbacks (CascadeType.ALL)

4️⃣ Retrieve Data
Displays all customers and feedback entries.

Expected Console Output:

All Customers:
Customer{id=1, name='Dhivya', email='dhivya@example.com'}

All Feedbacks:
Feedback{id=1, message='Excellent service!', rating=5, customer=Dhivya}
Feedback{id=2, message='Good experience.', rating=4, customer=Dhivya}

🧪 Running Test:
-----------------
You can create JUnit tests to verify:

✓ Database connectivity

✓ Customer and feedback persistence

✓ One-to-many relationship mapping

Example (pseudo test):

@Test
public void testSaveCustomer() {
    Customer c = new Customer("TestUser", "test@example.com");
    dao.saveCustomer(c);
    assertNotNull(c.getId());
}

🚀 Deployment:
---------------
You can deploy the application as:

A standalone JAR file using Maven:

mvn package
java -jar target/CustomerFeedbackSystem.jar

🏗️ Build With:
---------------

✓ Java SE – Core logic.

✓ Hibernate ORM – Object-relational mapping.

✓ Maven – Build & dependency management.

✓ MySQL – Data storage.

✓ JPA annotations – Entity relationships.

🏁 Conclusion:
---------------

This project demonstrates how to:

✓ Map one-to-many relationships in Hibernate.

✓ Use DAO pattern for database operations.

✓ Configure Hibernate with MySQL.

✓ Perform CRUD operations with cascading.

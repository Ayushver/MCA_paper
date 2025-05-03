# DATABASE MANAGEMENT SYSTEM (MCA-201)
## Comprehensive Study Notes

## Table of Contents
1. [Introduction to DBMS](#introduction-to-dbms)
2. [Database Models](#database-models)
3. [Entity-Relationship Model](#entity-relationship-model)
4. [Relational Model](#relational-model)
5. [SQL: Structured Query Language](#sql-structured-query-language)
6. [Normalization](#normalization)
7. [Transaction Management](#transaction-management)
8. [Concurrency Control](#concurrency-control)
9. [Database Recovery](#database-recovery)
10. [Database Security](#database-security)
11. [Distributed Databases](#distributed-databases)
12. [Data Warehousing and Data Mining](#data-warehousing-and-data-mining)
13. [NoSQL Databases](#nosql-databases)
14. [Big Data and Emerging Technologies](#big-data-and-emerging-technologies)

---

## Introduction to DBMS

### What is a Database?
A database is simply an organized collection of information stored on a computer. Think of it as a digital filing cabinet where all your important data is kept in a structured way. For example, a library database might store books, members, and borrowing records.

Unlike storing data in regular files (like Excel spreadsheets), a database organizes everything so you can easily find what you need, even when you have millions of records.

**Real-world example:** When you shop online, the website uses a database to store product information, your account details, and your order history.

### What is a DBMS?
A Database Management System (DBMS) is special software that helps us work with databases. It's like a manager for your digital filing cabinet. Examples include MySQL, Oracle, SQL Server, and MongoDB.

The DBMS helps us:
- Create new databases and tables
- Store data in the right places
- Find information quickly
- Make changes to existing data
- Control who can see or change different parts of the data

**Real-world example:** When you use an ATM, the bank's DBMS manages your account information, processes your transactions, and ensures your balance is updated correctly.

### Why Do We Need DBMS? (Explained Simply)

- **Stops Data Duplication**: Without a DBMS, the same information might be saved many times in different places. For example, a customer's address might be stored in the shipping department, billing department, and marketing department files. With a DBMS, it's stored just once, saving space and avoiding inconsistencies.

- **Keeps Data Consistent**: When data changes, a DBMS makes sure it changes everywhere it's supposed to. For example, if a customer changes their phone number, the DBMS ensures all departments see the updated number.

- **Lets People Share Data**: Multiple people can use the same data at the same time. For example, several airline ticket agents can book seats on the same flight simultaneously without creating duplicate bookings.

- **Unifies Data**: Brings together information from different sources. For instance, a school DBMS can combine student records, class schedules, and grade reports into one unified system.

- **Protects Data**: Controls who can see or change different pieces of information. For example, in a hospital database, doctors can see medical records, but billing staff can only see insurance information.

- **Separates Data from Programs**: Applications don't need to know how data is physically stored. This means you can change how data is stored without changing the applications that use it.

### Advantages of DBMS (With Examples)

1. **Less Repeated Data**: Imagine a school where each teacher keeps their own list of student contact information. If a student changes their phone number, it might get updated in some lists but not others. A DBMS stores this information once, so there's only one place to update.

2. **Better Data Accuracy**: When a customer changes their address, a DBMS ensures that change appears everywhere in the system. Without a DBMS, some departments might still have the old address.

3. **Stronger Data Security**: A bank DBMS can ensure that tellers can process deposits and withdrawals but can't change interest rates, while managers have broader access.

4. **United View of Data**: A retail business can see how inventory, sales, customer preferences, and staffing all relate to each other in one system.

5. **Quicker Data Access**: Instead of searching through file cabinets or scrolling through spreadsheets, a DBMS can find a specific customer record instantly among millions.

6. **Higher Productivity**: Staff spend less time looking for information and more time using it. A salesperson can quickly look up a customer's purchase history while on the phone with them.

7. **Smarter Decisions**: Managers can easily get up-to-date information to make informed choices. For example, a store manager can quickly see which products are selling well and which aren't.

### Disadvantages of DBMS (Explained)

1. **Expensive**: Setting up a good database system costs money for software licenses, powerful computers, and expert help. A small business might spend thousands of dollars just to get started.

2. **Complicated to Use**: Using a DBMS requires special knowledge. Database administrators need training to design, set up, and maintain the system properly.

3. **Needs Powerful Computers**: Database systems, especially for large companies, need fast computers with lots of storage. A company database might require servers that cost tens of thousands of dollars.

4. **When It Breaks, Everything Stops**: If a file system breaks, maybe one department is affected. If the central database goes down, the whole company might grind to a halt. For example, if an airline's database crashes, no one can check in, book tickets, or board planes.

### Database Architecture (Made Simple)

#### Three-Schema Architecture
This splits the database into three levels (like floors in a building):

1. **External Level (What Users See)**: Different users see the database differently. For example, in a hospital database:
   - Doctors see patient medical histories and treatments
   - Billing staff see insurance and payment information
   - Nurses see medication schedules and care plans
   All are looking at the same database but seeing different parts.

2. **Conceptual Level (The Big Picture)**: This is the complete view of all data and how it connects. It includes all the tables and relationships, like how patients connect to treatments, doctors, rooms, and billing.

3. **Internal Level (How It's Actually Stored)**: This is the technical part about how data is physically stored on hard drives, how it's indexed, and how the computer actually finds it. Users don't need to understand this level.

#### Two-Tier Architecture
This is like a restaurant with just a dining room and kitchen:

- **Client (The Customer)**: The application that users interact with, like a banking app on your phone
- **Server (The Kitchen)**: The database system that stores and processes the data

For example, when you use an ATM, your interaction is with the client, which sends requests to the server to get your account balance or process withdrawals.

#### Three-Tier Architecture
This adds a middle layer, like adding waiters to our restaurant example:

1. **Presentation Tier (Dining Room)**: What users see and interact with, like a website or app interface
2. **Application Tier (Waiters)**: Processes user requests, applies business rules, and passes appropriate queries to the database
3. **Data Tier (Kitchen)**: The actual database that stores and retrieves the data

**Real-world example:** When you use a banking website, you interact with the presentation tier (the website). When you request your transactions, the application tier checks if you're logged in, determines what accounts you can access, then asks the data tier for the specific information. The data tier retrieves your transaction data, sends it back to the application tier which formats it, and then to the presentation tier which displays it on your screen.

---

## Database Models

### What is a Database Model?
A database model defines the logical structure of a database and determines how data can be stored, organized, and manipulated.

### Types of Database Models

#### 1. Hierarchical Model
- Data organized in a tree-like structure
- Parent-child relationship between records
- One-to-many relationships only
- **Example**: IBM's Information Management System (IMS)
- **Advantages**: Simple structure, efficient for certain queries
- **Disadvantages**: Inflexible, cannot represent many-to-many relationships

#### 2. Network Model
- Allows many-to-many relationships
- Records are organized as graphs
- **Example**: Integrated Data Store (IDS)
- **Advantages**: More flexible than hierarchical model
- **Disadvantages**: Complex implementation, difficult to modify

#### 3. Relational Model
- Based on relational algebra
- Data stored in tables (relations)
- Relationships established through foreign keys
- **Example**: MySQL, Oracle, SQL Server
- **Advantages**: Simple, flexible, widely used
- **Disadvantages**: Can be slow for very large databases

#### 4. Object-Oriented Model
- Based on object-oriented programming concepts
- Data stored as objects
- **Example**: ObjectDB, Db4o
- **Advantages**: Handles complex data types, integrates well with OOP languages
- **Disadvantages**: Lacks standardization, limited adoption

#### 5. Object-Relational Model
- Hybrid of relational and object-oriented models
- **Example**: PostgreSQL, Oracle
- **Advantages**: Combines benefits of both models
- **Disadvantages**: Added complexity

---

## Entity-Relationship Model

### What is the ER Model? (Simplified)
The Entity-Relationship (ER) Model is a way to draw a blueprint of your database before you build it. It's like sketching a house plan before construction begins. This model helps you visualize what information you'll store and how different pieces of information connect to each other.

The ER model lets you describe your database using everyday concepts rather than technical database terms. This makes it easier for non-technical people to understand and contribute to database design.

**Real-world example:** Before building a school database, you might create an ER model showing how students, courses, teachers, and classrooms all relate to each other.

### Components of ER Model (With Everyday Examples)

#### 1. Entity
An entity is a person, place, thing, or event that we want to store information about. In an ER diagram, we draw entities as rectangles.

**Think of entities as the nouns in your system:**
- STUDENT (a person we want information about)
- COURSE (a thing we want information about)
- DEPARTMENT (an organization we want information about)
- ENROLLMENT (an event we want information about)

For example, in a library database, entities might include BOOK, MEMBER, AUTHOR, and LOAN.

#### 2. Attribute
Attributes are the specific pieces of information we want to store about each entity. They're the characteristics or properties that describe an entity. In ER diagrams, attributes are shown as ovals connected to their entity.

**Using a STUDENT entity as an example:**
- Student_ID (a unique number for each student)
- Name (the student's name)
- Email (the student's email address)
- Date_of_Birth (when the student was born)
- Current_GPA (the student's grade point average)

**Types of Attributes (Explained Simply):**

- **Simple Attributes**: These can't be broken down further.
  Example: Student_ID is just one piece of information.

- **Composite Attributes**: These can be divided into smaller parts.
  Example: Address can be split into Street, City, State, and ZIP code.

- **Single-valued Attributes**: These have just one value for each entity.
  Example: A student has only one Student_ID.

- **Multi-valued Attributes**: These can have many values for one entity.
  Example: A student might have multiple Phone_Numbers or Skills.

- **Derived Attributes**: These can be calculated from other attributes.
  Example: Age can be calculated from Date_of_Birth and the current date.

- **Key Attributes**: These uniquely identify an entity instance.
  Example: Student_ID uniquely identifies each student.

#### 3. Relationship
A relationship shows how entities are connected to each other. They represent actions or associations between entities and are drawn as diamonds in ER diagrams.

**Examples of relationships:**
- A STUDENT "enrolls in" a COURSE
- A TEACHER "teaches" a COURSE
- A DEPARTMENT "offers" a COURSE

**Types of Relationships (With Clear Examples):**

- **One-to-One (1:1)**: Each entity on both sides of the relationship is associated with exactly one entity on the other side.
  Example: Each COUNTRY has exactly one PRESIDENT, and each PRESIDENT leads exactly one COUNTRY.
  
  ```
  COUNTRY ──────1:1────── PRESIDENT
  ```

- **One-to-Many (1:N)**: Each entity on one side can be associated with many entities on the other side, but each entity on the "many" side is associated with only one entity on the "one" side.
  Example: One DEPARTMENT employs many EMPLOYEEs, but each EMPLOYEE works for just one DEPARTMENT.
  
  ```
  DEPARTMENT ────1:N───── EMPLOYEE
  ```

- **Many-to-One (N:1)**: This is the same as One-to-Many but viewed from the opposite direction.
  Example: Many STUDENTs are born in one COUNTRY.
  
  ```
  STUDENT ─────N:1────── COUNTRY
  ```

- **Many-to-Many (M:N)**: Entities on both sides can be associated with many entities on the other side.
  Example: A STUDENT can enroll in many COURSEs, and each COURSE can have many STUDENTs enrolled.
  
  ```
  STUDENT ─────M:N────── COURSE
  ```

### Cardinality and Participation Constraints (Made Simple)

#### Cardinality
Cardinality tells us the maximum number of times an entity can participate in a relationship. Think of it as answering the question: "How many?"

**For example, in a relationship between TEACHER and COURSE:**
- One teacher can teach many courses (1:N)
- Or maybe there's a rule that one teacher can teach at most 3 courses (1:3)

#### Participation
Participation tells us whether all entities must be involved in the relationship or if participation is optional. It answers the question: "Is it required?"

- **Total Participation (Double Line)**: Every entity must participate in the relationship.
  Example: In a company database, every EMPLOYEE must work in a DEPARTMENT (an employee without a department doesn't make sense).

- **Partial Participation (Single Line)**: Some entities may not participate in the relationship.
  Example: Not every PROFESSOR may currently be teaching a COURSE (some might be on sabbatical or doing research only).

**Visual Example:**
```
EMPLOYEE ═══════ works_in ─────── DEPARTMENT
(double line)               (single line)
```
This shows every employee must work in a department, but a department might exist with no employees yet (like a newly created department).

### ER Diagram Notations (Simplified)

There are several ways to draw ER diagrams, similar to how there are different ways to write the alphabet (print vs. cursive):

- **Chen Notation**: The original notation with rectangles for entities, diamonds for relationships, and ovals for attributes.

- **Crow's Foot Notation**: Uses symbols that look like crow's feet to show "many" relationships. This is very common in professional tools.
  ```
  DEPARTMENT ──|─────○< EMPLOYEE
  (one)              (many)
  ```

- **UML Notation**: Uses class diagram style from Unified Modeling Language, where entities are classes and relationships are lines between them.

### Steps to Create an ER Diagram (With a Simple Example)

Let's create an ER diagram for a small library system:

1. **Identify entities**: What main things do we need to track?
   - BOOK
   - MEMBER
   - LOAN

2. **Determine relationships**: How do these entities connect?
   - MEMBER "borrows" BOOK (through a LOAN)
   - BOOK "is borrowed by" MEMBER (through a LOAN)

3. **Add attributes to entities**:
   - BOOK: ISBN (key), Title, Author, Published_Date, Genre
   - MEMBER: Member_ID (key), Name, Address, Phone, Join_Date
   - LOAN: Loan_ID (key), Loan_Date, Due_Date, Return_Date

4. **Determine primary keys**: Which attributes uniquely identify each entity?
   - BOOK: ISBN
   - MEMBER: Member_ID
   - LOAN: Loan_ID

5. **Add cardinality and participation constraints**:
   - A MEMBER can borrow many BOOKs (1:N)
   - A BOOK can only be borrowed by one MEMBER at a time (1:1)
   - A BOOK doesn't always have to be borrowed (partial participation)
   - A MEMBER doesn't always have to borrow books (partial participation)

6. **Refine the diagram**: Review and adjust as needed
   - Add a return status attribute to LOAN
   - Consider adding a RESERVATION entity

### Converting ER Diagram to Relational Schema (Simple Steps with Example)

After creating your ER diagram, you need to convert it to tables in a relational database. Here's how to do it:

1. **Strong Entity**: Create a table with all attributes. The primary key remains the same.
   
   Example: For the MEMBER entity:
   ```sql
   CREATE TABLE MEMBER (
       Member_ID INT PRIMARY KEY,
       Name VARCHAR(50),
       Address VARCHAR(100),
       Phone VARCHAR(15),
       Join_Date DATE
   );
   ```

2. **Weak Entity**: Create a table with all attributes. The primary key is the combination of its partial key and the primary key of its owner entity.
   
   Example: If DEPENDENT is a weak entity owned by EMPLOYEE:
   ```sql
   CREATE TABLE DEPENDENT (
       Emp_ID INT,
       Dependent_Name VARCHAR(50),
       Relationship VARCHAR(20),
       PRIMARY KEY (Emp_ID, Dependent_Name),
       FOREIGN KEY (Emp_ID) REFERENCES EMPLOYEE(Emp_ID)
   );
   ```

3. **One-to-One (1:1) Relationship**: Include the primary key of one entity as a foreign key in the other entity's table.
   
   Example: For PERSON and PASSPORT (each person has exactly one passport):
   ```sql
   CREATE TABLE PERSON (
       Person_ID INT PRIMARY KEY,
       Name VARCHAR(50),
       Birth_Date DATE
   );
   
   CREATE TABLE PASSPORT (
       Passport_Number VARCHAR(20) PRIMARY KEY,
       Issue_Date DATE,
       Expiry_Date DATE,
       Person_ID INT UNIQUE,
       FOREIGN KEY (Person_ID) REFERENCES PERSON(Person_ID)
   );
   ```

4. **One-to-Many (1:N) Relationship**: Include the primary key of the "one" side as a foreign key in the table on the "many" side.
   
   Example: For DEPARTMENT and EMPLOYEE (one department has many employees):
   ```sql
   CREATE TABLE DEPARTMENT (
       Dept_ID INT PRIMARY KEY,
       Dept_Name VARCHAR(50),
       Location VARCHAR(50)
   );
   
   CREATE TABLE EMPLOYEE (
       Emp_ID INT PRIMARY KEY,
       Name VARCHAR(50),
       Salary DECIMAL(10,2),
       Dept_ID INT,
       FOREIGN KEY (Dept_ID) REFERENCES DEPARTMENT(Dept_ID)
   );
   ```

5. **Many-to-Many (M:N) Relationship**: Create a new table (junction table) with the primary keys of both entities as foreign keys.
   
   Example: For STUDENT and COURSE (students take many courses, courses have many students):
   ```sql
   CREATE TABLE STUDENT (
       Student_ID INT PRIMARY KEY,
       Name VARCHAR(50),
       Major VARCHAR(50)
   );
   
   CREATE TABLE COURSE (
       Course_ID VARCHAR(10) PRIMARY KEY,
       Title VARCHAR(100),
       Credits INT
   );
   
   CREATE TABLE ENROLLMENT (
       Student_ID INT,
       Course_ID VARCHAR(10),
       Semester VARCHAR(20),
       Grade CHAR(1),
       PRIMARY KEY (Student_ID, Course_ID),
       FOREIGN KEY (Student_ID) REFERENCES STUDENT(Student_ID),
       FOREIGN KEY (Course_ID) REFERENCES COURSE(Course_ID)
   );
   ```

---

## Relational Model

### What is the Relational Model?
The relational model, proposed by E.F. Codd in 1970, represents data in the form of tables (relations) with rows (tuples) and columns (attributes).

### Key Concepts

#### 1. Relation (Table)
- A two-dimensional table containing rows and columns
- Each relation has a name and consists of attributes and tuples

#### 2. Tuple (Row)
- Each row in a relation represents a record
- Must be distinct from every other row

#### 3. Attribute (Column)
- Each column in a relation represents a property
- Has a domain (set of allowed values)

#### 4. Domain
- The set of allowable values for an attribute
- **Example**: Integer, Date, Character

#### 5. Degree
- The number of attributes in a relation

#### 6. Cardinality
- The number of tuples in a relation

### Relational Database Constraints

#### 1. Domain Constraints
- Values in a column must be within the specified domain

#### 2. Key Constraints
- **Super Key**: Set of attributes that uniquely identifies a tuple
- **Candidate Key**: Minimal super key (no subset can be a super key)
- **Primary Key**: Chosen candidate key used to identify tuples
- **Alternate Key**: Candidate keys not selected as primary key
- **Foreign Key**: Attribute that refers to a primary key in another relation

#### 3. Entity Integrity Constraint
- Primary key cannot contain NULL values

#### 4. Referential Integrity Constraint
- If a foreign key exists in a relation, either:
  - The foreign key value must match a primary key value in the referenced relation
  - The foreign key value must be NULL

#### 5. User-Defined Constraints
- Business rules specific to an organization

### Relational Algebra
A procedural query language that consists of operations on relations.

#### Basic Operations
1. **Selection (σ)**: Selects tuples that satisfy a condition
   - Syntax: σ<condition>(relation)
   - Example: σage>25(STUDENT)

2. **Projection (π)**: Selects specified attributes
   - Syntax: π<attributes>(relation)
   - Example: πname,age(STUDENT)

3. **Union (∪)**: Combines two compatible relations
   - Example: R ∪ S

4. **Set Difference (-)**: Returns tuples in first relation but not in second
   - Example: R - S

5. **Cartesian Product (×)**: Combines each tuple from first relation with every tuple from second
   - Example: R × S

6. **Rename (ρ)**: Renames relations or attributes
   - Example: ρnew_name(relation)

#### Derived Operations
1. **Intersection (∩)**: Returns tuples common to both relations
   - R ∩ S = R - (R - S)

2. **Join (⋈)**: Combines related tuples from two relations
   - **Natural Join**: Joins on common attributes
   - **Theta Join**: Joins based on a condition
   - **Equijoin**: Theta join with equality condition
   - **Outer Join**: Preserves unmatched tuples
     - Left Outer Join
     - Right Outer Join
     - Full Outer Join

3. **Division (÷)**: Returns values from first relation that are associated with all values in second relation

### Relational Calculus
A non-procedural query language based on mathematical logic.

#### 1. Tuple Relational Calculus
- Uses tuple variables that range over tuples
- Expression: {t | P(t)} where P is a condition

#### 2. Domain Relational Calculus
- Uses domain variables that range over attribute domains
- Expression: {⟨x1, x2, ..., xn⟩ | P(x1, x2, ..., xn)}

---

## SQL: Structured Query Language

### What is SQL? (Explained Simply)
SQL (Structured Query Language) is a special language that helps us talk to databases. Think of it as the language you use to ask questions about data or tell the database to make changes. It's like having a conversation with your database.

If databases were libraries, SQL would be how you ask the librarian to find books, add new books, update book information, or remove old books.

**Real-world example:** When you use a banking app and check your recent transactions, the app uses SQL to ask the database "Show me all transactions for account #12345 from the last 30 days."

### Types of SQL Commands (With Simple Explanations)

#### 1. Data Definition Language (DDL)
These commands create and change the structure of your database - like constructing and remodeling the building itself:

- **CREATE**: Makes new things in your database (like making a new filing cabinet)
  ```sql
  -- Creating a new table is like setting up a new filing cabinet
  CREATE TABLE Customers (
      id INT,
      name VARCHAR(100),
      email VARCHAR(100)
  );
  ```

- **ALTER**: Changes existing structures (like adding a new drawer to your cabinet)
  ```sql
  -- Adding a new column is like adding a new section to your files
  ALTER TABLE Customers ADD phone VARCHAR(15);
  ```

- **DROP**: Completely removes things (like throwing away an entire filing cabinet)
  ```sql
  -- This completely removes the Customers table and all its data!
  DROP TABLE Customers;
  ```

- **TRUNCATE**: Empties a table but keeps its structure (like emptying the filing cabinet but keeping it)
  ```sql
  -- Removes all customer records but keeps the empty table structure
  TRUNCATE TABLE Customers;
  ```

- **RENAME**: Changes names (like putting a new label on your filing cabinet)
  ```sql
  -- Changes the table name from Customers to ClientList
  RENAME TABLE Customers TO ClientList;
  ```

#### 2. Data Manipulation Language (DML)
These commands work with the actual data - like handling the papers inside your filing cabinets:

- **SELECT**: Gets data (like pulling files to read them)
  ```sql
  -- Get all information about all customers
  SELECT * FROM Customers;
  
  -- Get just names and emails of customers
  SELECT name, email FROM Customers;
  ```

- **INSERT**: Adds new data (like adding new papers to your files)
  ```sql
  -- Add a new customer record
  INSERT INTO Customers (id, name, email)
  VALUES (1, 'John Smith', 'john@example.com');
  ```

- **UPDATE**: Changes existing data (like correcting information on your papers)
  ```sql
  -- Update John's email address
  UPDATE Customers
  SET email = 'john.smith@example.com'
  WHERE id = 1;
  ```

- **DELETE**: Removes data (like removing papers from your files)
  ```sql
  -- Remove a specific customer
  DELETE FROM Customers WHERE id = 1;
  ```

#### 3. Data Control Language (DCL)
These commands control who can access and change data - like managing who has keys to your filing cabinets:

- **GRANT**: Gives permissions (like giving someone a key)
  ```sql
  -- Allow the user 'marketing_team' to view customer data
  GRANT SELECT ON Customers TO marketing_team;
  ```

- **REVOKE**: Takes away permissions (like taking back a key)
  ```sql
  -- Remove the marketing team's ability to modify customer data
  REVOKE INSERT, UPDATE, DELETE ON Customers FROM marketing_team;
  ```

#### 4. Transaction Control Language (TCL)
These commands manage changes as groups - like making sure a multi-step task is either completely done or not done at all:

- **COMMIT**: Saves all changes permanently (like officially filing all your paperwork)
  ```sql
  -- Save all the changes you've made
  COMMIT;
  ```

- **ROLLBACK**: Undoes changes that haven't been committed (like taking back papers before they're filed)
  ```sql
  -- Undo changes if something went wrong
  ROLLBACK;
  ```

- **SAVEPOINT**: Creates a point you can roll back to (like putting a bookmark in your work)
  ```sql
  -- Create a point we can return to if needed
  SAVEPOINT before_bulk_update;
  
  -- If something goes wrong, we can go back to that point
  ROLLBACK TO before_bulk_update;
  ```

### SQL Examples with Clear Explanations

#### Creating a Table (Setting up a Student Record System)
```sql
-- This creates a new table to store student information
CREATE TABLE STUDENTS (
    student_id INT PRIMARY KEY,  -- Unique ID number for each student
    name VARCHAR(50) NOT NULL,   -- Student name (must be provided)
    age INT CHECK (age > 0),     -- Age must be positive
    gender CHAR(1),              -- M, F, or O (one character only)
    department VARCHAR(30),      -- Which department they study in
    -- Make sure gender is one of the allowed values
    CONSTRAINT gender_check CHECK (gender IN ('M', 'F', 'O'))
);
```

This is like creating a new form template that has spaces for ID, name, age, gender, and department, with rules about what can be written in each space.

#### Inserting Data (Adding a New Student)
```sql
-- Add a new student to our records
INSERT INTO STUDENTS (student_id, name, age, gender, department)
VALUES (1, 'Maria Garcia', 19, 'F', 'Computer Science');
```

This is like filling out a form for Maria with all her information and adding it to our filing cabinet.

#### Querying Data (Finding Information)

**Simple SELECT (Get All Students)**
```sql
-- Show all information about all students
SELECT * FROM STUDENTS;
```
This gives you every piece of information about every student - like pulling out all student forms from the filing cabinet.

**Filtering with WHERE (Finding

---

## Normalization

### What is Normalization?
Normalization is the process of organizing data in a database to reduce redundancy and improve data integrity.

### Database Anomalies
Problems that can occur in unnormalized databases:

1. **Insertion Anomaly**: Unable to add data due to lack of other data
2. **Deletion Anomaly**: Unintended loss of data when deleting other data
3. **Update Anomaly**: Data inconsistency due to partial updates

### Functional Dependencies
A functional dependency (FD) X → Y means that values of X determine values of Y.

#### Types of FDs:
1. **Trivial FD**: Y is a subset of X
2. **Non-trivial FD**: Y is not a subset of X
3. **Fully Functional Dependency**: Removing any attribute from X breaks the dependency
4. **Partial Dependency**: Removing some attribute from X still preserves the dependency
5. **Transitive Dependency**: X → Y and Y → Z implies X → Z (where Y is not a subset of X)

### Normal Forms

#### 1. First Normal Form (1NF)
- All attributes are atomic (indivisible)
- No repeating groups or arrays

**Example**:
- Unnormalized: STUDENT(ID, Name, Courses)
- 1NF: STUDENT(ID, Name), ENROLLMENT(ID, Course)

#### 2. Second Normal Form (2NF)
- Must be in 1NF
- All non-key attributes are fully functionally dependent on the primary key

**Example**:
- 1NF: ENROLLMENT(StudentID, CourseID, CourseName, StudentName)
- 2NF: STUDENT(StudentID, StudentName), COURSE(CourseID, CourseName), ENROLLMENT(StudentID, CourseID)

#### 3. Third Normal Form (3NF)
- Must be in 2NF
- No transitive dependencies (non-key attributes dependent on other non-key attributes)

**Example**:
- 2NF: COURSE(CourseID, CourseName, DepartmentID, DepartmentName)
- 3NF: COURSE(CourseID, CourseName, DepartmentID), DEPARTMENT(DepartmentID, DepartmentName)

#### 4. Boyce-Codd Normal Form (BCNF)
- Must be in 3NF
- For every dependency X → Y, X must be a super key

#### 5. Fourth Normal Form (4NF)
- Must be in BCNF
- No multi-valued dependencies

#### 6. Fifth Normal Form (5NF)
- Must be in 4NF
- No join dependencies

### Denormalization
The process of intentionally adding redundancy to improve performance.

**When to Use**:
- Read-heavy workloads
- Complex queries requiring many joins
- Performance bottlenecks

---

## Transaction Management

### What is a Transaction?
A transaction is a unit of work that is performed against a database and is treated in a coherent and reliable way independent of other transactions.

### ACID Properties
1. **Atomicity**: A transaction is an atomic unit of work; either all its operations are performed or none.
2. **Consistency**: A transaction must transform the database from one consistent state to another.
3. **Isolation**: Transactions execute independently of one another.
4. **Durability**: Once a transaction is committed, its effects are permanent.

### Transaction States
1. **Active**: Transaction is executing
2. **Partially Committed**: After final operation
3. **Committed**: Successful completion
4. **Failed**: Normal execution can't continue
5. **Aborted**: Transaction rolled back, database restored
6. **Terminated**: End of transaction

### Transaction Control Commands
- **BEGIN TRANSACTION**: Starts a transaction
- **COMMIT**: Saves changes
- **ROLLBACK**: Undoes changes
- **SAVEPOINT**: Creates points within transactions
- **ROLLBACK TO SAVEPOINT**: Rolls back to a savepoint

### Transaction Implementation
- **Log-Based Recovery**: Maintains a log of operations
- **Shadow Paging**: Maintains two page tables during updates
- **Checkpoints**: Reduces recovery time by periodically saving state

---

## Concurrency Control

### What is Concurrency Control?
Concurrency control ensures that transactions execute in a correct manner and preserve the ACID properties when multiple transactions execute simultaneously.

### Concurrency Problems
1. **Lost Update**: Two transactions read and update the same data, one overwriting the other's changes
2. **Dirty Read**: Reading uncommitted changes from another transaction
3. **Non-Repeatable Read**: Reading same data twice and getting different results
4. **Phantom Read**: New rows appear in a repeated query

### Concurrency Control Techniques

#### 1. Locking
- **Shared Lock (S-lock)**: Multiple transactions can read
- **Exclusive Lock (X-lock)**: Only one transaction can write
- **Two-Phase Locking (2PL)**: Locks acquired in growing phase, released in shrinking phase
- **Strict 2PL**: Locks held until transaction commits
- **Conservative 2PL**: All locks acquired at beginning
- **Lock Compatibility Matrix**:
  | Lock Type | S-lock | X-lock |
  |-----------|--------|--------|
  | S-lock    | Yes    | No     |
  | X-lock    | No     | No     |

#### 2. Timestamp Ordering
- Assigns timestamps to transactions
- Ensures older transactions go first
- **Thomas Write Rule**: Ignores writes that would be overwritten anyway

#### 3. Multiversion Concurrency Control (MVCC)
- Maintains multiple versions of data
- Each transaction sees a snapshot of the database
- Used in PostgreSQL, Oracle, MySQL (InnoDB)

#### 4. Optimistic Concurrency Control
- Assumes conflicts are rare
- Validates transactions before commit
- **Phases**: Read, Validation, Write

### Deadlocks
A deadlock occurs when two or more transactions are waiting for each other to release locks.

#### Deadlock Handling
1. **Prevention**: Prevent deadlocks from occurring
   - **Wait-Die**: Older transactions wait, younger ones die
   - **Wound-Wait**: Older transactions wound (abort) younger ones, younger wait

2. **Detection**: Detect deadlocks when they occur
   - **Wait-For Graph**: Represents waiting relationships
   - **Timeout**: Abort transactions that wait too long

3. **Recovery**: Resolve deadlocks by aborting transactions

---

## Database Recovery

### What is Database Recovery?
Database recovery is the process of restoring the database to a correct state after a failure.

### Types of Failures
1. **Transaction Failure**:
   - Logical errors in transaction
   - System errors (deadlock)

2. **System Failure**:
   - Power failure
   - Hardware/software errors

3. **Media Failure**:
   - Disk crash
   - Physical damage to storage

### Recovery Techniques

#### 1. Log-Based Recovery
- Maintains a log of all database modifications
- **Undo Operation**: Restores old values (for rollback)
- **Redo Operation**: Reapplies new values (for recovery after commit)

#### 2. Shadow Paging
- Maintains two page tables during transaction
- Current page table and shadow page table
- On commit, current becomes shadow
- On abort, shadow is used to restore state

#### 3. ARIES Recovery Algorithm
- **Analysis Phase**: Identifies active transactions at failure
- **Redo Phase**: Repeats all actions from last checkpoint
- **Undo Phase**: Rolls back incomplete transactions

### Backup Strategies
1. **Full Backup**: Complete copy of database
2. **Incremental Backup**: Only changes since last backup
3. **Differential Backup**: All changes since last full backup
4. **Transaction Log Backup**: Copy of transaction logs

### Recovery Strategies
1. **Point-in-Time Recovery**: Restore to specific moment
2. **Point-of-Failure Recovery**: Restore to moment before failure
3. **Standby Recovery**: Use standby database

---

## Database Security

### What is Database Security?
Database security refers to the comprehensive range of tools, controls, and measures designed to establish and preserve database confidentiality, integrity, and availability. In modern business environments, databases often contain sensitive information that is critical to organizations and their customers, making security a fundamental concern.

Database security operates on three core principles:
- **Confidentiality**: Ensuring that data is accessible only to authorized users
- **Integrity**: Maintaining and assuring the accuracy and consistency of data
- **Availability**: Ensuring that authorized users have access to data when needed

### Database Security Threats
1. **Excessive Privileges**: When users are granted more access permissions than required for their roles, it creates unnecessary security risks. For example, if a clerk who only needs to view customer information is given permissions to modify financial data, this excess privilege could lead to accidental or intentional data corruption.

2. **SQL Injection**: This is a code injection technique where malicious SQL statements are inserted into entry fields for execution. For example:
   ```sql
   -- Original intended query
   SELECT * FROM users WHERE username = 'input' AND password = 'input'
   
   -- With SQL injection (input: admin' OR '1'='1)
   SELECT * FROM users WHERE username = 'admin' OR '1'='1' AND password = 'anything'
   -- This returns true regardless of password, granting unauthorized access
   ```

3. **Malware**: Various forms of malicious software (viruses, trojans, ransomware) can compromise database systems. For instance, ransomware might encrypt a database and demand payment for the decryption key, while keyloggers could steal database credentials.

4. **Weak Authentication**: Simple, easily guessed passwords or shared credentials make databases vulnerable. For example, using "password123" or default credentials like "admin/admin" can lead to easy unauthorized access.

5. **Backup Exposure**: Database backups often contain the same sensitive information as the live database but might have weaker security controls. Unencrypted backup files stored on publicly accessible servers could be easily downloaded and exploited.

6. **Denial of Service (DoS)**: These attacks aim to make databases unavailable by overwhelming them with requests. For example, an attacker might flood a database server with thousands of complex queries simultaneously, causing legitimate queries to time out.

7. **Inference Attacks**: Even when direct access to sensitive data is restricted, attackers might infer protected information by analyzing permitted data. For instance, if a database restricts access to exact salaries but allows queries on salary ranges, repeated queries with different ranges could reveal specific salaries.

8. **Social Engineering**: Attackers might manipulate database administrators or users into revealing credentials or providing access. For example, a phishing email pretending to be from IT support might trick a database administrator into resetting their password to one chosen by the attacker.

### Database Security Measures

#### 1. Authentication
Authentication verifies the identity of users attempting to access the database, serving as the first line of defense.

- **Username/Password**: Traditional login credentials where users provide their unique identifier and a secret passphrase. Best practices include enforcing strong password policies (minimum length, complexity requirements, regular changes).
  
  Example implementation in PostgreSQL:
  ```sql
  CREATE USER analyst WITH PASSWORD 'Str0ng&C0mpl3x!';
  ALTER USER analyst PASSWORD 'NewSecur3P@ssw0rd' VALID UNTIL '2023-12-31';
  ```

- **Multi-Factor Authentication (MFA)**: Requires users to provide two or more verification factors:
  - Something you know (password)
  - Something you have (security token, mobile device)
  - Something you are (biometric verification)
  
  For example, Oracle Database supports MFA through Oracle Advanced Security, requiring both a password and a token generated by a mobile app.

- **Biometric Authentication**: Uses unique physical characteristics like fingerprints, facial recognition, or iris scans. While less common for direct database access, it's increasingly used in applications that connect to databases.

- **Certificate-Based Authentication**: Uses digital certificates to verify identity. The client presents a certificate signed by a trusted Certificate Authority (CA) during connection.
  
  Example in MySQL:
  ```sql
  CREATE USER 'analyst'@'%' IDENTIFIED BY 'password' REQUIRE X509;
  ```

#### 2. Authorization
Once authenticated, authorization determines what actions users can perform on which data.

- **Discretionary Access Control (DAC)**: The object owner determines who can access objects and what privileges they have. Most relational databases implement DAC by default.
  
  In SQL Server:
  ```sql
  GRANT SELECT ON Customers TO SalesStaff;
  DENY SELECT ON Customers WHERE CreditLimit > 100000 TO SalesStaff;
  ```

- **Mandatory Access Control (MAC)**: System-enforced access based on classification levels and clearances. Data objects receive sensitivity labels, and users receive clearance levels.
  
  Oracle Label Security implements MAC:
  ```sql
  -- Create a policy
  EXEC SA_SYSDBA.CREATE_POLICY('access_policy', 'policy_schema');
  
  -- Apply labels to data
  UPDATE employee SET label = char_to_label('access_policy', 'SENSITIVE');
  ```

- **Role-Based Access Control (RBAC)**: Access rights are grouped by role, and users are assigned to appropriate roles based on their responsibilities.
  
  Example in PostgreSQL:
  ```sql
  CREATE ROLE data_analyst;
  GRANT SELECT ON analytics_data TO data_analyst;
  GRANT data_analyst TO alice, bob;
  ```

- **Attribute-Based Access Control (ABAC)**: Access decisions are based on attributes of the user, resource, action, and environment. This provides more dynamic and contextual access control.
  
  For example, a policy might specify that managers can view all employee records in their department, but only during business hours from company IP addresses.

#### 3. SQL Security
SQL security features control what operations users can perform on database objects.

- **GRANT Statement**: Assigns privileges to users or roles.
  ```sql
  -- Grant specific privileges
  GRANT SELECT, INSERT ON STUDENT TO user1;
  
  -- Grant all privileges
  GRANT ALL PRIVILEGES ON DATABASE university TO admin;
  
  -- Grant with grant option (user can further grant these privileges)
  GRANT SELECT ON COURSE TO professor WITH GRANT OPTION;
  ```

- **REVOKE Statement**: Removes previously granted permissions.
  ```sql
  -- Revoke specific privilege
  REVOKE INSERT ON STUDENT FROM user1;
  
  -- Revoke all privileges
  REVOKE ALL PRIVILEGES ON STUDENT FROM user1;
  
  -- Revoke cascading (also revokes grants made by this user)
  REVOKE SELECT ON COURSE FROM professor CASCADE;
  ```

- **Roles**: Groups of privileges that can be assigned to users, making permission management more efficient.
  ```sql
  -- Create role
  CREATE ROLE professor;
  
  -- Assign privileges to role
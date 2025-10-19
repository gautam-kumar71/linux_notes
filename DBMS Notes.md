## Data

### 🧩 Data
- Raw, unprocessed facts and figures.
- Has no specific meaning on its own.
- Unorganized and unstructured.
- Cannot be directly used for decision-making.  
**Example:** 85, 90, 78 — these can be either marks, age, or anything else.

### 💡 Information
- Processed and organized data.
- Carries meaning and context.
- Structured and useful for analysis.
- Helps in decision-making and understanding.  
**Example:**  
- Average marks = 84.3 (shows performance)  
- “Orange” could mean a color or a fruit. This term “orange” is **data**.  
- If we say “color orange” or “fruit orange,” it becomes **information**.  
- Similarly, “12” could mean age, pocket money, or roll number. Hence, this is **data**.  
- When we say “Roll number 12,” it becomes **information**.

---

## Database
A database is a structured collection of interrelated data organized in a way that is easy to store, retrieve, and manipulate information. It serves as a centralized repository for data.

**Key characteristics of databases:**
- It is a collection of interrelated data.
- It can be stored in the form of tables.
- It can be of any size.

**Examples:** Multimedia Database, college database, etc.

---

## File System
A file system is a structure that an operating system uses to manage and organize files on a storage device, such as a hard drive, SSDs, or USB flash drive.  
- It defines how data is organized, accessed, and stored on the storage device.  
- The file system acts as an interface between the user and the data.

---

## Database Management System (DBMS)
A Database Management System (DBMS) is software designed to manage, manipulate, and organize large volumes of data efficiently.  
- Acts as an interface between the database and the users or applications.  
- Provides tools for storing, retrieving, updating, and managing data securely.

**Real-life Applications of DBMS**
- **Banking:** Keeps all customer and transaction details safe and consistent.  
- **Airlines:** Handles flight schedules, seat bookings, and passenger details.  
- **Education:** Stores student data like marks, attendance, and personal details.

---

## DBMS vs RDBMS

| Feature               | DBMS                           | RDBMS                                  |
| --------------------- | ------------------------------ | -------------------------------------- |
| Relationships         | Doesn’t support relationships  | Maintains relations using keys         |
| Data Storage          | Stores data as files           | Stores data in tables (rows & columns) |
| Data Redundancy       | High                           | Reduced                                |
| Integrity Constraints | Limited                        | Supports primary & foreign keys        |
| Security & Efficiency | Less secure and less efficient | More secure and reliable               |

**Examples:**  
- DBMS: File System
- RDBMS: MySQL, Oracle, SQL Server

---

## Advantages of DBMS
1. **Data Security:** Only authorized users can access data.  
2. **Data Integrity:** Ensures accuracy and consistency of data.  
3. **Reduced Data Redundancy:** Avoids duplicate data through normalization.  
4. **Efficient Data Access:** Query languages like SQL make data retrieval fast.  
5. **Backup and Recovery:** Easy to back up data and restore in case of failure.  
6. **Multi-user Access:** Multiple users can access and modify data concurrently.  
7. **Data Independence:** Changes in data structure don’t affect applications.

---

## Disadvantages of DBMS
1. Costly: Expensive to install and maintain.  
2. Complexity: Requires trained personnel to manage and operate.  
3. Performance Overhead: Can be slower for simple applications due to overhead.  
4. Centralized Failure Risk: If the central DB fails, all users are affected.  
5. Security Risks: If not properly managed, sensitive data may be exposed.

---

## Disadvantages of File Systems
1. Data Redundancy: Same data may be stored in multiple files, wasting space.  
2. Data Inconsistency: Duplicate data can lead to conflicting information.  
3. Difficulty in Accessing Data: Searching across multiple files is slow and complex.  
4. Limited Data Sharing: Hard for multiple users to access and update data simultaneously.  
5. Poor Data Security: No built-in access control; data is vulnerable.  
6. Data Integrity Problems: No mechanism to enforce accuracy or consistency.  
7. Maintenance Overhead: Changes in file structure may require changes in all programs using it.

---

## Purpose of DBMS
- Provide users with an **abstract view** of the data.  
- Simplifies user interaction with the system.

**Three-Level Architecture Objective:**  
- Enable multiple users to access the same data with a personalized view while storing the underlying data only once.

---

### Physical Level / Internal Level
- Lowest level of abstraction describing how the data are stored.  
- Low-level data structures used.  
- **Physical schema:** Describes physical storage structure of DB.  
- Talks about: Storage allocation (N-ary tree etc.), Data compression & encryption.  
- **Goal:** Define algorithms for efficient data access.

---

### Logical Level / Conceptual Level
- **Conceptual schema:** Design of a database at the conceptual level, describing what data are stored and what relationships exist.  
- Users do not need to know physical-level structures.  
- Used by DBA to decide what information to keep in the DB.  
- **Goal:** Ease of use.

---

### View Level / External Level
- Highest level of abstraction, simplifying user interaction.  
- Provides different views to different end-users.  
- **Subschema:** User-specific schemas at external level.  
- Provides security mechanism to restrict access.

---

## Types of Database Schema

1. **Internal Schema (Physical Schema):**  
   - How data is physically stored.  
   - Focuses on storage structures, indexes, and access methods.

2. **Conceptual Schema (Logical Schema):**  
   - Overall logical structure of the database.  
   - Shows entities, relationships, constraints, and data types.  
   - Independent of physical storage.

3. **External Schema (View Schema):**  
   - Defines user-specific views of the database.  
   - Shows only relevant data to each user or application.  
   - Helps in data security and simplicity.

---

## Instances and Schemas
1. **Database Instance:**  
   - Collection of information stored in the database at a particular moment.  
   - Example: Current records of all students in a university database.

2. **Database Schema:**  
   - Overall design or structure of the database.  
   - Blueprint showing what kind of data will be stored and how it will be organized.  
   - Schema doesn’t change frequently; data (instances) change often.  
   - **Analogy:** Schema is like variable declarations; instances are actual values stored.

---

## Data Models
- Provides a way to describe the design of a DB at logical level.  
- **Underlying structure of DB:** Collection of conceptual tools for describing data, relationships, semantics & constraints.  
- **Examples:** ER model, Relational Model, Object-oriented model, Object-relational model.

---

## How Database is Accessed from Application Programs
- Applications (C/C++, Java) interact with DB via APIs to send DML/DDL statements and retrieve results.  
**Examples:**  
- ODBC (Open Database Connectivity)  
- JDBC (Java Database Connectivity)

---

## Database Administrator (DBA)
- Manages and controls the database system.  
- Ensures database runs smoothly, securely, and efficiently.

**Main Responsibilities:**
1. Database Installation & Setup  
2. Database Design  
3. User Management  
4. Security Management  
5. Backup & Recovery  
6. Performance Tuning  
7. Maintenance

---

## DBMS Application Architectures

### T1 Architecture
- Client, server, & DB on same machine.

### T2 Architecture
- App partitioned into 2 components:  
  1. Client machine invokes DB functionality at server via query language.  
  2. API standards like ODBC & JDBC used for communication.

### T3 Architecture
- App partitioned into 3 components:  
  1. Client is just frontend, no direct DB calls.  
  2. Client communicates with App server; App server communicates with DB.  
  3. Business logic resides in App server.  
**Advantages:**  
- Scalability, Data integrity, Security.

---

## ER Model
- Look directly from the PDF

---

## **Types of Relationships in DBMS**

### One-to-One (1:1)
- One entity in A ↔ at most one entity in B, and vice versa.  
**Example:** Citizen ↔ Aadhar Card

### One-to-Many (1:N)
- One entity in A ↔ many entities in B, but each B entity ↔ at most one A entity.  
**Example:** Teacher ↔ Students

### Many-to-One (N:1)
- Many entities in A ↔ one entity in B, but each B entity ↔ many A entities.  
**Example:** Many Courses ↔ One Professor

### Many-to-Many (M:N)
- Entities in A ↔ many entities in B, and vice versa.  
**Example:** Student ↔ Courses, Customer ↔ Products

### Participation Constraint
1. Aka Minimum cardinality constraint.  
2. Types: Partial & Total Participation.  
3. Partial Participation: Not all entities involved in the relationship.  
4. Total Participation: Each entity must be involved in at least one relationship.  
**Example:**  
- Customer borrows loan → Loan has total participation.  
- Weak entity has total participation; strong may not.

## **Specialisation**

**Definition:**
- Specialisation is splitting up the entity set into further sub-entity sets on the basis of their **functionalities, specialities, and features**.  
- It is a **Top-Down approach**.

**Example:**
A `Person` entity set can be divided into:
- `Customer`
- `Student`
- `Employee`

Here, `Person` is the **superclass**, and the other specialised entity sets are **subclasses**.

- There exists an **"is-a" relationship** between the superclass and subclass.  

- It is **depicted by a triangle** component in ER diagrams.

---

### **Why Specialisation?**
- Allows the database designer to **show distinctive features** of the sub-entities.  
- Used to **group similar entities** and **refine the database blueprint** for better clarity.

---

## **Generalisation**

1. It is the **reverse of Specialisation**.
2. A DB Designer may find **overlapping properties** between two or more entities.
3. To avoid duplication, the designer may create a **new generalised entity set**, which becomes the **superclass**.
4. There exists an **"is-a" relationship** between subclass and superclass.
5. **Example:**  
   Entities like `Car`, `Jeep`, and `Bus` have common attributes.  
   To avoid data repetition, these can be generalised into a single entity `Vehicle`.
6. It follows a **Bottom-Up approach**.

---

### **Why Generalisation?**
- Makes the database **simpler and more refined**.  
- Ensures **common attributes are not repeated**, improving data integrity and structure.

---

## **Attribute Inheritance**

1. Both **Specialisation** and **Generalisation** involve **attribute inheritance**.
2. Attributes of higher-level entity sets are **inherited** by lower-level entity sets.
3. **Example:**  
   `Customer` and `Employee` inherit attributes from `Person`.

---

## **Participation Inheritance**

- If a **parent entity set** participates in a relationship, then its **child entity sets** also participate in that relationship.

---

## **Aggregation (Reference: YouTube / Notes)**


---

## **Prime Attributes**
Prime attributes are those attributes that are **part of at least one candidate key** of a relation.

---

# **Integrity Constraints in DBMS**

- CRUD operations (Create, Read, Update, Delete) must follow **integrity policies** to keep the database **consistent and accurate**.  
- Integrity constraints are introduced to **prevent accidental corruption** or invalid data in the database.

---
# Different Types of **Integrity Constraints in DBMS**
## **1. Domain Constraints**

- Restrict the **type of values** that can be stored in an attribute.  
- Define the **domain** (valid range, data type, or condition) for each attribute.  

**Example:**  
A student’s birth year must be **less than 2002** for enrollment.

```sql
CHECK (BirthYear < 2002)
```

## **2. Entity Integrity Constraint**

- Ensures that **every table has a Primary Key (PK)**.
- The **Primary Key cannot be NULL**, since it uniquely identifies each record.
  **Example:**  
  Every student must have a unique `RollNo`.

---

## **3. Referential Integrity Constraint**

- Maintains **consistency between two related tables**.
- Each FK value must **match an existing PK** in the parent table **or be NULL**.
- This ensures there are **no broken references** between tables.

**Example:**  
`STUDENT(CourseID)` must refer to a valid `CourseID` in the `COURSE` table.

---

## **4. Key Constraints**

These are specific rules that ensure **data uniqueness and validity**.

|**Constraint**|**Description**|
|---|---|
|**NOT NULL**|Ensures that a column cannot have NULL values.|
|**UNIQUE**|Ensures all values in a column are different.|
|**DEFAULT**|Sets a default value for a column when no value is provided.|
|**CHECK**|Ensures that data meets a specific condition before insertion or update.|
|**PRIMARY KEY**|Uniquely identifies each record (must be unique and not null).|
|**FOREIGN KEY**|Creates a link between two tables using a common attribute (PK in one table becomes FK in another). Prevents actions that break the link between tables.|
### 🔹 **Referenced Table**
- It is the **parent table** that contains the **Primary Key (PK)**.
### 🔹 **Referencing Table**
- It is the **child table** that contains the **Foreign Key (FK)**.
---
### Normalisation- from notes (revise once from youtube too)
### Transactions - from notes
### Indexing -->  [Indexing](https://takeuforward.org/dbms/indexing-and-its-types)(Tuf)
### clustering-->From notes 

Will do later:
### partitioning and sharding-->ytb love babbar
### Types of Database-->chatgpt+ytb love babbar

#Todo
Lec-13 will look later(only understand the concept that's it, and say the ans in your own words)

## **SDLC (Software Development Life Cycle)**
### 🔹 **Definition**

A step-by-step process to **design, develop, test, and deploy** high-quality software.

---
### **Phases of SDLC**

1. **Requirement Analysis** – Gather and analyze user needs (SRS document).
2. **System Design** – Plan architecture, database, and UI (DDS).
3. **Implementation** – Write and test the code (unit testing).
4. **Testing** – Detect and fix bugs; ensure quality.
5. **Deployment** – Release software to users.    
6. **Maintenance** – Update, fix, and enhance software post-deployment.

---

### **Models**

- **Waterfall** – Linear and sequential.
- **Iterative** – Repeated improvements.
- **V-Model** – Testing alongside development.
- **Spiral** – Risk-based iterative model.
- **Agile** – Fast, flexible, customer-focused.

---

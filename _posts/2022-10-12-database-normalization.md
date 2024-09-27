---
layout: post
section-type: post
has-comments: true
title: "Database Normalization"
category: database
---

## Anomaly

1. **Insertion Anomaly**: One cannot insert a new tuple into a relationship due to **lack of data**.
2. **Deletion Anomaly**: The deletion of data results in the unintended **loss** of some other important data.
3. **Updatation Anomaly**: When an update of a single data value requires **multiple rows** of data to be updated.

## Normalization

- Reduce **redundancy** from the database table
- Divide larger table into **smaller** and link them using relationship

### 1NF

- Each cell contains an **atomic** value.
    
    Not in 1NF because Subject contains multiple values.
    
    | Student_id | Name | Subject |
    | --- | --- | --- |
    | 101 | Akash | Computer Network, JAVA |
    | 102 | Vikrant | Database Management System |
    | 103 | Amrita | Software Engineering, Compiler Design |
    
    | Student_id | Name | Subject |
    | --- | --- | --- |
    | 101 | Aksh | Computer Network |
    | 101 | Aksh | JAVA |
    | 102 | Vikrant | Database Management System |
    | 103 | Amrita | Software Engineering |
    | 103 | Amrita | Compiler Design |

### 2NF

- The candidate key should **determine all** non-prime attributes or no partial dependency should exist.
    - **Super key**: Any combination of columns that **uniquely identifies a row** in table.
    - **Candidate key**: A super key from which you **cannot remove any fields**.
    - **Prime attributes**: Attributes used to **form a candidate key**.
    - **Non-prime attributes**: Attributes do **not** form a candidate key.
    - **Partial dependency**: A **non-prime attribute** can be determined by **part of** the candidate key.
    
    | student_id | programming_langauges | student_age |
    | --- | --- | --- |
    | 101 | Computer Network | 20 |
    | 101 | JAVA | 20 |
    | 102 | Database Management System | 20 |
    | 103 | Software Engineering | 21 |
    | 103 | Compiler Design | 21 |
    
    Candidate Keys: {student_id, programming_language}
    
    Non-prime attribute: student_age
    
    Partial dependency: student_id → student_age
    
    | student_id | student_age |
    | --- | --- |
    | 101 | 20 |
    | 101 | 20 |
    | 102 | 20 |
    | 103 | 21 |
    | 103 | 21 |
    
    | student_id | programming_langauge |
    | --- | --- |
    | 101 | Computer Network |
    | 101 | JAVA |
    | 102 | Database Management System |
    | 103 | Software Engineering |
    | 103 | Compiler Design |

### 3NF

- No **transitive functional dependency** exists for non-prime attributes.
    - **Transitive dependency**: If X → Y and Y → Z, then X → Z is called a transitive dependency.
    
    | Rollno | State | City |
    | --- | --- | --- |
    | 1 | Punjab | Chandigarh |
    | 2 | Haryana | Ambala |
    | 3 | Punjab | Chandigarh |
    | 4 | Haryana | Ambala |
    | 5 | Uttar Pradesh | Ghaziabad |
    
    Candidate Key: {Rollno}
    
    Prime attribute: Rollno
    
    Non-prime attribute: {State, City}
    
    Transitive dependency: Rollno → State, State → City
    
    | Rollno | State |
    | --- | --- |
    | 1 | Punjab |
    | 2 | Haryana |
    | 3 | Punjab |
    | 4 | Haryana |
    | 5 | Uttar Pradesh |
    
    | State | City |
    | --- | --- |
    | Punjab | Chandigarh |
    | Haryana | Ambala |
    | Uttar Pradesh | Ghaziabad |

### **Boyce-Codd Normal Form (BCNF)**

- For every X → Y, **X must be a super key**.
    
    
    | Ground | Begin_Time | End_Time | Package |
    | --- | --- | --- | --- |
    | G01 | 07:00 | 09:00 | Gold |
    | G01 | 10:00 | 12:00 | Gold |
    | G01 | 10:30 | 11:00 | Bronze |
    | G02 | 10:15 | 11:15 | Silver |
    | G02 | 08:00 | 09:00 | Silver |
    
    Candidate Key: {Ground}
    
    Prime attribute: Ground
    
    Non-prime attribute: {Begin_Time, End_Time, Package}
    
    Package → Ground and Package is not a super key
    
    | Package | Ground |
    | --- | --- |
    | Gold | G01 |
    | Silver | G02 |
    | Bronze | G01 |
    
    | Ground | Begin_Time | End_Time |
    | --- | --- | --- |
    | G01 | 07:00 | 09:00 |
    | G01 | 10:00 | 12:00 |
    | G01 | 10:30 | 11:00 |
    | G02 | 10:15 | 11:15 |
    | G02 | 08:00 | 09:00 |

### 4NF

- **No multivalued dependency** exists.
    
    **Multivalued dependency**: X → Y, if for a single value of X, multiple values of Y exist.
    
    | student_id | Name | Course |
    | --- | --- | --- |
    | 101 | Ankit | Python |
    | 102 | Kartikey | Java |
    | 103 | Krishna | R programming |
    | 101 | Ankit | Java |
    | 105 | Akash | PHP |
    
    Student_id → Name
    
    Student_id → Course
    
    | student_id | Name |
    | --- | --- |
    | 101 | Ankit |
    | 102 | Kartikey |
    | 103 | Krishna |
    | 105 | Akash |
    
    | student_id | Course |
    | --- | --- |
    | 101 | Python |
    | 102 | Java |
    | 103 | R programming |
    | 101 | Java |
    | 105 | PHP |

# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
*Paste or attach your diagram here*  
<img width="1246" height="521" alt="Screenshot from 2026-07-31 11-18-31" src="https://github.com/user-attachments/assets/e4febebc-3865-4eab-a972-bf67501f7d89" />


# Entity-Relationship (ER) Diagram Breakdown

This document presents the detailed breakdown of Entities, Attributes, and Relationships extracted from the Fitness Center / Gym Management System ER Diagram.

---

## 1. Entities & Attributes

### **MEMBER**
Representing individual gym members registered in the system.
* **Attributes:**
  * `Member_ID` *(Primary Key / Unique Identifier)*
  * `Name`
  * `Membership_Type`

### **FITNESS_PROGRAM**
Representing structured fitness courses, classes, or programs offered by the gym.
* **Attributes:**
  * `Program_ID` *(Primary Key / Unique Identifier)*
  * `Program_Name`

### **TRAINER**
Representing fitness trainers employed or associated with the gym.
* **Attributes:**
  * `Trainer_ID` *(Primary Key / Unique Identifier)*
  * `Name`
  * `Specialization`

### **PT_SESSION**
Representing personal training sessions scheduled between members and trainers.
* **Attributes:**
  * `Session_ID` *(Primary Key / Unique Identifier)*
  * `Date_Time`

### **PAYMENT**
Representing financial transactions and payment records made by members.
* **Attributes:**
  * `Payment_ID` *(Primary Key / Unique Identifier)*
  * `Amount`
  * `Date`

---

## 2. Relationships Summary

| Relationship Name | Connected Entities | Cardinality | Type | Explanation |
| :--- | :--- | :---: | :---: | :--- |
| **Joins** | `MEMBER` $\leftrightarrow$ `FITNESS_PROGRAM` | **M:N** | Many-to-Many | A member can join multiple programs, and a program can have multiple members. |
| **Teaches** | `TRAINER` $\leftrightarrow$ `FITNESS_PROGRAM` | **M:N** | Many-to-Many | A trainer can teach multiple fitness programs, and a program can be taught by multiple trainers. |
| **Books** | `MEMBER` $
ightarrow$ `PT_SESSION` | **1:N** | One-to-Many | A single member can book multiple PT sessions, but each session is booked by one member. |
| **Conducts** | `TRAINER` $
ightarrow$ `PT_SESSION` | **1:N** | One-to-Many | A single trainer can conduct multiple PT sessions, but each session is conducted by one trainer. |
| **Makes** | `MEMBER` $
ightarrow$ `PAYMENT` | **1:N** | One-to-Many | A single member can make multiple payments over time, but each payment belongs to one member. |

---

## 3. Detailed Cardinality & Mapping

```
[ MEMBER ] (M) <--- Joins ---> (N) [ FITNESS_PROGRAM ]
[ TRAINER ] (M) <--- Teaches ---> (N) [ FITNESS_PROGRAM ]
[ MEMBER ] (1) <--- Books ---> (N) [ PT_SESSION ]
[ TRAINER ] (1) <--- Conducts ---> (N) [ PT_SESSION ]
[ MEMBER ] (1) <--- Makes ---> (N) [ PAYMENT ]
```
### Assumptions
- 
- 
- 

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
<img width="1246" height="649" alt="Screenshot from 2026-07-31 11-18-51" src="https://github.com/user-attachments/assets/194ebf72-b0fc-4d16-a6f4-c6a11e3eb5ba" />


# Library Management System - ER Diagram Breakdown

This document details the Entities, Attributes, and Relationships extracted from the Library Management System ER Diagram.

---

## 1. Entities & Attributes

### **MEMBER**
Represents individuals registered with the library.
* **Attributes:**
  * `Member_ID` *(Primary Key)*
  * `Name`

### **BOOK**
Represents the books available in the library collection.
* **Attributes:**
  * `Book_ID` *(Primary Key)*
  * `Title`
  * `Category`

### **EVENT**
Represents special events or workshops hosted by the library.
* **Attributes:**
  * `Event_ID` *(Primary Key)*
  * `Event_Name`
  * `Date`

### **SPEAKER**
Represents guest speakers or presenters invited to events.
* **Attributes:**
  * `Speaker_ID` *(Primary Key)*
  * `Name`

### **ROOM**
Represents physical library rooms or spaces reserved for events.
* **Attributes:**
  * `Room_Number` *(Primary Key)*
  * `Capacity`

### **FINE**
Represents financial penalties issued to members (e.g., for overdue books).
* **Attributes:**
  * `Fine_ID` *(Primary Key)*
  * `Amount`

---

## 2. Relationships Summary

| Relationship Name | Connected Entities | Cardinality | Type | Explanation |
| :--- | :--- | :---: | :---: | :--- |
| **Borrows** | `MEMBER` $\leftrightarrow$ `BOOK` | **M:N** | Many-to-Many | A member can borrow multiple books, and a book can be borrowed by multiple members over time. |
| **Registers** | `MEMBER` $\leftrightarrow$ `EVENT` | **M:N** | Many-to-Many | A member can register for multiple events, and an event can have multiple members registered. |
| **Features** | `SPEAKER` $\leftrightarrow$ `EVENT` | **M:N** | Many-to-Many | A speaker can be featured in multiple events, and an event can feature multiple speakers. |
| **Reserves** | `EVENT` $
ightarrow$ `ROOM` | **N:1** | Many-to-One | Multiple events can reserve the same room, but each event reservation points to one room. |
| **Incurs** | `MEMBER` $
ightarrow$ `FINE` | **1:N** | One-to-Many | A single member can incur multiple fines, but each fine belongs to one member. |

---

## 3. Structural Mapping

```
[ MEMBER ] (M) <--- Borrows ---> (N) [ BOOK ]
[ MEMBER ] (M) <--- Registers --> (N) [ EVENT ]
[ SPEAKER ] (M) <-- Features --> (N) [ EVENT ]
[ EVENT ] (N) <---- Reserves ---> (1) [ ROOM ]
[ MEMBER ] (1) <---- Incurs ----> (N) [ FINE ]
```

### Assumptions
- 
- 
- 

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="1103" height="715" alt="Screenshot from 2026-07-31 11-19-15" src="https://github.com/user-attachments/assets/dc89b279-8fe7-4d08-9b08-44ab4b8a118b" />
 


# Restaurant Management System - ER Diagram Breakdown

This document presents the detailed breakdown of Entities, Attributes, and Relationships extracted from the Restaurant Management System ER Diagram.

---

## 1. Entities & Attributes

### **CUSTOMER**
Represents patrons who visit the restaurant and make reservations.
* **Attributes:**
  * `Customer_ID` *(Primary Key / Unique Identifier)*
  * `Name`

### **RESERVATION**
Represents booking bookings created for dining at specific times.
* **Attributes:**
  * `Reservation_ID` *(Primary Key / Unique Identifier)*
  * `Date_Time`
  * `Guest_Count`

### **TABLE**
Represents physical dining tables within the restaurant.
* **Attributes:**
  * `Table_Number` *(Primary Key / Unique Identifier)*
  * `Capacity`

### **ORDER**
Represents food/beverage orders placed during a reservation.
* **Attributes:**
  * `Order_ID` *(Primary Key / Unique Identifier)*
  * `Order_Time`

### **DISH**
Represents menu items offered by the restaurant.
* **Attributes:**
  * `Dish_ID` *(Primary Key / Unique Identifier)*
  * `Dish_Name`
  * `Category`

### **BILL**
Represents the final financial invoice for a reservation.
* **Attributes:**
  * `Bill_ID` *(Primary Key / Unique Identifier)*
  * `Total_Amount`

### **WAITER**
Represents staff members assigned to serve dining tables/reservations.
* **Attributes:**
  * `Waiter_ID` *(Primary Key / Unique Identifier)*
  * `Name`

---

## 2. Relationships Summary

| Relationship Name | Connected Entities | Cardinality | Type | Explanation |
| :--- | :--- | :---: | :---: | :--- |
| **Makes** | `CUSTOMER` $
ightarrow$ `RESERVATION` | **1:N** | One-to-Many | A single customer can make multiple reservations over time. |
| **Reserves** | `RESERVATION` $
ightarrow$ `TABLE` | **N:1** | Many-to-One | Multiple reservations can be booked for the same table at different time slots. |
| **Places** | `RESERVATION` $
ightarrow$ `ORDER` | **1:N** | One-to-Many | A single reservation session can place multiple food orders. |
| **Contains** | `ORDER` $\leftrightarrow$ `DISH` | **M:N** | Many-to-Many | An order can contain multiple dishes, and a dish can appear across multiple orders. |
| **Generates** | `RESERVATION` $\leftrightarrow$ `BILL` | **1:1** | One-to-One | Each reservation generates exactly one final bill. |
| **Serves** | `WAITER` $
ightarrow$ `RESERVATION` | **1:N** | One-to-Many | A assigned waiter can serve multiple reservations. |

---

## 3. Structural Mapping

```
[ CUSTOMER ] (1) <--- Makes -----> (N) [ RESERVATION ]
[ RESERVATION ] (N) <- Reserves -> (1) [ TABLE ]
[ RESERVATION ] (1) <-- Places --> (N) [ ORDER ]
[ ORDER ] (M) <----- Contains ---> (N) [ DISH ]
[ RESERVATION ] (1) <- Generates -> (1) [ BILL ]
[ WAITER ] (1) <---- Serves -----> (N) [ RESERVATION ]
```
### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**

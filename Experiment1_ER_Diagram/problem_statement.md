# ER Diagram Workshop

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

Restaurant Table Reservation & Ordering

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
<img width="1364" height="710" alt="image" src="https://github.com/user-attachments/assets/a3dfd95b-084c-4245-a9a9-75b1e7e6d35c" />


## Entities and Attributes Table

| S.No. | Entity     | Attribute      | Key / Description                               |
| ----- | ---------- | -------------- | ----------------------------------------------- |
| 1     | Customer   | CustomerID     | Primary Key (PK)                                |
|       |            | Name           | Customer name                                   |
|       |            | ContactDetails | Contact information                             |
|       |            | TableNumber    | Assigned table number                           |
| 2     | Waiter     | WaiterID       | Primary Key (PK)                                |
|       |            | Name           | Waiter name                                     |
|       |            | ContactDetails | Contact information                             |
| 3     | Chef       | ChefID         | Primary Key (PK)                                |
|       |            | Name           | Chef name                                       |
|       |            | ContactDetails | Contact information                             |
| 4     | Table      | TableID        | Primary Key (PK)                                |
|       |            | Location       | Table location                                  |
|       |            | Status         | Occupied / Available                            |
| 5     | FoodItem   | FoodItemID     | Primary Key (PK)                                |
|       |            | Name           | Food item name                                  |
|       |            | Description    | Food item description                           |
|       |            | Price          | Food item price                                 |
|       |            | Category       | Appetizer / Main course / Dessert               |
| 6     | Order      | OrderID        | Primary Key (PK)                                |
|       |            | DateTime       | Order date and time                             |
|       |            | TotalAmount    | Total order amount                              |
|       |            | Status         | Pending / In preparation / Completed / Canceled |
| 7     | OrderItem  | OrderItemID    | Primary Key (PK)                                |
|       |            | OrderID        | Foreign Key (FK)                                |
|       |            | FoodItemID     | Foreign Key (FK)                                |
|       |            | Quantity       | Quantity ordered                                |
|       |            | Status         | Ordered / Being prepared / Ready                |
| 8     | Bill       | BillID         | Primary Key (PK)                                |
|       |            | OrderID        | Foreign Key (FK)                                |
|       |            | TotalAmount    | Total bill amount                               |
|       |            | PaymentStatus  | Paid / Unpaid                                   |
| 9     | Supervisor | SupervisorID   | Primary Key (PK)                                |
|       |            | Name           | Supervisor name                                 |
|       |            | ContactDetails | Contact information                             |
### Relationships and Constraints

Relationship	Cardinality	Participation	Notes
Customer – Table (Has)	Many-to-One (N:1)	Customer: Total; Table: Partial	A customer is assigned to one table. A table can accommodate multiple customers over time.
Waiter – Table (Serves)	One-to-Many (1:N)	Waiter: Partial; Table: Total	A waiter serves multiple tables. A table is served by one waiter at a time.
Waiter – Order (Creates)	One-to-Many (1:N)	Waiter: Partial; Order: Total	A waiter creates multiple orders. An order is created by one waiter.
Order – Table (Belongs to)	Many-to-One (N:1)	Order: Total; Table: Partial	An order belongs to one table. A table can have multiple orders over time.
Order – OrderItem (Contains)	One-to-Many (1:N)	Order: Total; OrderItem: Total	An order contains multiple order items. Each order item belongs to one order.
OrderItem – FoodItem (Refers to)	Many-to-One (N:1)	OrderItem: Total; FoodItem: Partial	Each order item refers to one food item. A food item can appear in multiple order items.
Order – Bill (Generates)	One-to-One (1:1)	Order: Total; Bill: Total	A bill is generated for one order. An order has one bill.
Chef – OrderItem (Prepares)	One-to-Many (1:N)	Chef: Partial; OrderItem: Total	A chef prepares multiple order items. Each order item is prepared by one chef.
Supervisor – Order (Manages)	One-to-Many (1:N)	Supervisor: Partial; Order: Partial	A supervisor manages exceptional cases related to orders. An order may have supervisor oversight.


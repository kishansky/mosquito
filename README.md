# Design Document

  

By AMAN KUSHWAHA

  

Video overview: <URL  HERE>

  

## Scope

* This database will enable order based custom manufacturing businesses to manage orders

* The database can include shoe makers, jewellers, tailors,  carpenters, goldsmiths, etc.

* Retailers, sellers, suppliers, etc. are outside the scope of this database.

  

## Functional Requirements

  

By using this database:

* Customer and their details can be added.
* Multiple specific measurements and details of each customer can be managed.
* Orders of customers can be managed.
* Orders can be assigned to employees.
* Order status can be tracked.

Limitations:
* multiple users can't  place a single order.
* multiple users can't have single measurement.
* One order can use only one measurement.


  


Hi


 

## Representation

  

### Entities

 <details ><summary>Customer</summary>
  Customer is the key component of any business. This database can contain following details about customers:
  * Name
  * Contact number
  * Address
  * Measurements for their custom orders
  * Orders placed by the customer
  </details>
  
  #### Families
  Best way to build a good customer base is to target them as a family. Database can store following details about family(This is an optional field):
  * Name of a family.
  * Members of the family who are costumers of the business,
  * Details of the head of the family.
  * Address of the family.
 #### Employees
 Employees of any business are the backbone of the business structure. Following details about Employees can be stored:
 * Name 
 * Contact Number
 * Address 
 * Post on which he/she is currently working.
 #### Stores
 A order based business can't operate efficiently without the proper storage facility. Following details about the storage facility can be stored in this database:
 * Physical name of the storage space.
 * Description and caution about the space.
 

In this section you should answer the following questions:

* Which entities will you choose to represent in your database?

* What attributes will those entities have?

* Why did you choose the types you did?

* Why did you choose the constraints you did?

  

### Relationships
mermaid
erDiagram

FAMILIES  ||--|{  USERS  : includes

FAMILIES  {

int id

string family_name

int head_id

}

USERS  {

int id

string first_name

string last_name

string gender

int phone_number

int family_id

string address

int pincode

}

USERS  ||--|{  ORDERS  : places

  

EMPLOYEES{

int id

string first_name

string last_name

int phone_number

eNum post

string address

int pincode

}

EMPLOYEES||--o{  MEASUREMENTS  : makes

EMPLOYEES||--o{  ORDERS  : accepts

  

MEASUREMENTS  {

int id

int user_id

int employee_id

eNum type

string measurements

string description

datetime timestamp

}

ORDERS{

int id

int user_id

int measurement_id

int serial_id

int employee_id

datetime timestamp

string order_details

string additional_measurement

money cost

datetime return_date

}

  

ORDERS  }|--||  MEASUREMENTS  : uses

ORDERS  ||--|{  STORES  : is_stored_in

ORDERS  ||--|{  ACTIONS  : has

  

STORES{

int id

string name

string description

}

ACTIONS{

int id

int order_id

datetime timestamp

int employee_id

string action

int store_id

decimal cost

string details

}

EMPLOYEES||--o{ACTIONS  : takes

ACTIONS||--o|STORES: in

In this section you should include your entity relationship diagram and describe the relationships between the entities in your database.

  

## Optimizations

  

In this section you should answer the following questions:

  

* Which optimizations (e.g., indexes, views) did you create? Why?

  

## Limitations

  

In this section you should answer the following questions:

  

* What are the limitations of your design?

* What might your database not be able to represent very well?

# Use Case Diagram

## Description

In the Unified Modeling Language (UML), a use case diagram is used to represent the interactions between a system and its users. It provides a high-level view of the system’s functional requirements by showing how external entities, called actors, interact with the system to achieve specific goals.

A use case diagram is created using a set of standard symbols and connectors. It helps in clearly identifying the scenarios in which the system interacts with people, organizations, or other external systems. Each use case represents a goal that an actor wants to accomplish with the help of the system.

Use case diagrams also define the scope of the system by clearly separating what is inside the system boundary and what lies outside it.

By identifying all external actors and their required actions, use case diagrams ensure that no major functionality is missed before moving on to system design and implementation.

## Components (with Symbols & Examples)

### Use Case
**Symbol:** Horizontally shaped oval  
**Description:** Indicates a specific task the system performs in response to an actor  
**Example:** Login, Payment  

### Actor
**Symbol:** Stick figure  
**Description:** Represents the user or any external system that interacts with the system  

- ## Primary Actor (left side of the system)

Initiates the use case.

Has a goal to be achieved using the system.

Directly benefits from the system.

Example: Student submitting an assignment, Customer placing an order.

-- ## Secondary Actor (right side of the system)

Supports the system to complete the use case.

Does not initiate the interaction.

Provides a service to the system.

Example: Database, Payment Gateway, Email Service.

**Example:** Customer, Bank  

### Association
**Symbol:** Straight line  
**Description:** Line between actors and use cases showing interaction  
**Example:** Customer — Place Order  

### System Boundary Box
**Symbol:** Rectangle  
**Description:** Encloses use cases and represents the scope of the system  
**Example:** Online Shopping System  

## Relationships (with Symbols & Examples)

### Association Relationship
**Symbol:** Solid line  
**Description:** Represents communication or interaction between actor and use case  
**Example:** Customer — Place Order  

### Dependency Relationship
Shows that one use case depends on another  

Two types (stereotypes):

#### <<include>>
**Symbol:** Dashed arrow with <<include>>  
**Description:** One use case always uses another use case  
**Arrow Direction:** Main use case → Included use case  
**Example:** Place Order <<include>> Login  

#### <<extend>>
**Symbol:** Dashed arrow with <<extend>>  
**Description:** One use case optionally adds behavior to another  
**Arrow Direction:** Optional use case → Base use case  
**Example:** Apply Coupon <<extend>> Checkout  

### Generalization
**Symbol:** Solid line with hollow triangle pointing to parent  
**Description:** Shows inheritance between actors or use cases  

**Example:**  
Payment  
Online Payment  
Cash Payment  

### Specialization
**Description:** A specialized actor or use case inherits features from a general one but may add extra behavior  

**Example:**  
User  
Student  
Faculty  

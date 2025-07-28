# Course Management System Design

## Objective  
Simulate a **System Design Interview** by applying **Object-Oriented Programming (OOP)** principles to design and implement a scalable, real-world **Online Course Management System**.

## Scenario  
You have been tasked with designing an **Online Course Management System** using core OOP principles such as **Abstraction, Inheritance, Polymorphism**, and **Encapsulation**. The system should handle multiple **user roles**, support **course and assignment management**, and enforce **role-based access control**.

## User Roles  
- **Student**  
  - View available courses  
  - Enroll in courses  
  - Upload assignments  
  - View grades  

- **Instructor**  
  - Create and manage courses  
  - View enrolled students  
  - Upload assignments  
  - Grade student submissions  


## Role-Based Access Control  
Each user can only access the features allowed for their role:
- **Student**: Cannot create or grade assignments.  
- **Instructor**: Cannot enroll in courses as a student.

## UML Class Diagram  
![UML Diagram](https://github.com/user-attachments/assets/27d1b116-63af-4292-a75e-79132081c42f)

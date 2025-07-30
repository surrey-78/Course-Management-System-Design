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

## JavaScript Implementation

### User (Superclass)

```javascript
class User {
  #id;
  #name;
  #email;

  constructor(id, name, email) {
    this.#id = id;
    this.#name = name;
    this.#email = email;
  }

  getName() { return this.#name; }
  getEmail() { return this.#email; }

  login() { console.log(`${this.#name} has logged in.`); }
  logout() { console.log(`${this.#name} has logged out.`); }

  displayInfo() {
    console.log(`User: ${this.#name}, Email: ${this.#email}`);
  }
}
```

### Student and Instructor (Subclasses)

```javascript
class Student extends User {
  #major;
  #year;

  constructor(id, name, email, major, year) {
    super(id, name, email);
    this.#major = major;
    this.#year = year;
  }

  getMajor() { return this.#major; }
  getYear() { return this.#year; }

  displayInfo() {
    console.log(`Student: ${this.getName()}, Major: ${this.#major}, Year: ${this.#year}`);
  }
}

class Instructor extends User {
  #department;

  constructor(id, name, email, department) {
    super(id, name, email);
    this.#department = department;
  }

  getDepartment() { return this.#department; }

  displayInfo() {
    console.log(`Instructor: ${this.getName()}, Department: ${this.#department}`);
  }
}
```

### Course, Assignment, Grade Classes

```javascript
class Course {
  constructor(code, title) {
    this.code = code;
    this.title = title;
    this.assignments = [];
  }

  addAssignment(assignment) {
    this.assignments.push(assignment);
  }
}

class Assignment {
  constructor(title, dueDate) {
    this.title = title;
    this.dueDate = dueDate;
  }

  submit() {
    console.log(`Assignment "${this.title}" submitted.`);
  }
}

class Grade {
  constructor(score, comments) {
    this.score = score;
    this.comments = comments;
  }

  getGrade() {
    return this.score;
  }
}
```

### Example Usage

```javascript
const student1 = new Student(1, "Alice", "alice@example.com", "Computer Science", 3);
const instructor1 = new Instructor(2, "Dr. Smith", "smith@example.com", "Engineering");

student1.login();
student1.displayInfo();

instructor1.login();
instructor1.displayInfo();

const course = new Course("CS101", "Intro to Programming");
const assignment = new Assignment("Project 1", "2025-08-10");

course.addAssignment(assignment);
assignment.submit();

const grade = new Grade(95, "Excellent work!");
console.log("Grade:", grade.getGrade());
```

---

## OOP Design Explanation

### 1. Abstraction
- Classes like `User`, `Student`, `Course`, etc., model real-world entities.
- `User` provides a general interface, hiding internal details.

### 2. Encapsulation
- Private fields (`#name`, `#email`) hide internal state.
- Getter methods expose only necessary information.

### 3. Inheritance
- `Student` and `Instructor` inherit from `User`.
- Common behavior is reused; subclasses add specific behavior.

### 4. Polymorphism
- `displayInfo()` is overridden in `Student` and `Instructor` to customize output.
---

## SOLID Principles

- **S**: Single Responsibility — Each class has one purpose.
- **O**: Open/Closed — Classes are open for extension, closed for modification.
- **L**: Liskov Substitution — Subclasses can replace their base type without issue.

---

The system is modular, extensible, and demonstrates clean OOP practices in JavaScript.

# Task.ERD.2 Language School
WSI Task.ERD.2

Go to [Task.ERD.1](https://github.com/WSI-PJATK/Task.ERD.1)

[Vertabelo Solution](https://my.vertabelo.com/public-model-view/p7oixJnyEbMx8RFLjos9CqVzxRwQU0NLs8GNo4zjOYdIWlM5gnM1rD9LHd5y9594?x=2501&y=2634&zoom=0.393)

## Task

Create an **entity relationship diagram** for requirements below. The diagram should be created using [Vertabelo](https://vertabelo.com/).

After you finish: upload your solution (exported from vertabelo in **png** or **svg** format) as an attachment of your assignment.

* Design an entity-relationship model for the language school. 

* We should store the information about courses available in the school, start and end date of the course and the price for each of our courses in the school. 

* Every course is dedicated for a certain language and is taught by a single teacher, but of course the same teacher may deliver multiple courses over the time. 

* We want to know the personal information about the teacher, his email address, phone number and the salary he earns in our school. 

* The system should be capable to store the languages each teacher knows, teacher’s level (e.g. A1, B2, C2 etc.) and the certification date for each language. 

* For each course in the school we need to have a list of students who participate in it, their date of joining and if they are enrolled in this course as an individual student or they have a group classes. 

* Also, we need to know some personal information about the students, their date of birth, email address and phone number for possible contacts. 

* Don’t forget that student may participate in multiple courses.

* The system should store information about payment, so that we know who performed the payment, for which course, when the payment happened and what was the amount of transferred money.

## Solution

Based on the requirements you provided, here's an entity-relationship (ER) model for the language school:

Entities:
1. Course
2. Language
3. Teacher
4. TeacherLanguage
5. Student
6. Enrollment
7. Payment

Relationships:
1. Course is dedicated to Language (many-to-one)
2. Teacher teaches Course (one-to-many)
3. Teacher knows Language (many-to-many) through TeacherLanguage
4. Student enrolls in Course (many-to-many) through Enrollment
5. Student makes Payment (one-to-many)

Attributes:
1. Course:
   - CourseID (primary key)
   - StartDate
   - EndDate
   - Price
   - LanguageID (foreign key referencing Language)
   - TeacherID (foreign key referencing Teacher)

2. Language:
   - LanguageID (primary key)
   - Name

3. Teacher:
   - TeacherID (primary key)
   - FirstName
   - LastName
   - Email
   - PhoneNumber
   - Salary

4. TeacherLanguage:
   - TeacherLanguageID (primary key)
   - TeacherID (foreign key referencing Teacher)
   - LanguageID (foreign key referencing Language)
   - Level
   - CertificationDate

5. Student:
   - StudentID (primary key)
   - FirstName
   - LastName
   - DateOfBirth
   - Email
   - PhoneNumber

6. Enrollment:
   - EnrollmentID (primary key)
   - StudentID (foreign key referencing Student)
   - CourseID (foreign key referencing Course)
   - DateJoined
   - IsIndividual (boolean indicating individual or group classes)

7. Payment:
   - PaymentID (primary key)
   - StudentID (foreign key referencing Student)
   - CourseID (foreign key referencing Course)
   - PaymentDate
   - Amount

ER Diagram:

```
+--------------+          +------------+
|   Language   |          |   Course   |
+--------------+          +------------+
| LanguageID (PK) |       | CourseID (PK) |
| Name         |<---------| StartDate  |
+--------------+          | EndDate    |
                          | Price      |
                          | LanguageID (FK) |
                          | TeacherID (FK) |
                          +------------+
                               ^
                               |
                               |
                          +------------+
                          |  Teacher   |
                          +------------+
                          | TeacherID (PK) |
                          | FirstName  |
                          | LastName   |
                          | Email      |
                          | PhoneNumber|
                          | Salary     |
                          +------------+
                               ^
                               |
                               |
            +------------------+------------------+
            |                                     |
+--------------+                           +--------------+
| TeacherLanguage |                       |  Enrollment  |
+--------------+                           +--------------+
| TeacherLanguageID (PK) |                | EnrollmentID (PK) |
| TeacherID (FK) |                        | StudentID (FK) |
| LanguageID (FK) |                       | CourseID (FK) |
| Level        |                          | DateJoined   |
| CertificationDate |                     | IsIndividual |
+--------------+                          +--------------+
                                                 ^
                                                 |
                                                 |
                                          +--------------+
                                          |   Student    |
                                          +--------------+
                                          | StudentID (PK) |
                                          | FirstName    |
                                          | LastName     |
                                          | DateOfBirth  |
                                          | Email        |
                                          | PhoneNumber  |
                                          +--------------+
                                                 ^
                                                 |
                                                 |
                                          +--------------+
                                          |   Payment    |
                                          +--------------+
                                          | PaymentID (PK) |
                                          | StudentID (FK) |
                                          | CourseID (FK) |
                                          | PaymentDate  |
                                          | Amount       |
                                          +--------------+
```

This ER model captures the main entities, their attributes, and the relationships between them based on the provided requirements. It allows for storing information about courses, languages, teachers, students, enrollments, and payments in a structured manner.


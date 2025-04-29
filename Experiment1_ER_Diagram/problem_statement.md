# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - POOVIZHI P

## Scenario Chosen:
University 

## ER Diagram:
[University er]https://github.com/user-attachments/assets/290b1430-751a-417d-8b5d-fdea41295679


## Entities and Attributes:
```
-DEPARTMENT:Dept_ID (Primary Key),Name
-PROGRAM:Program_ID (Primary Key),Program Name
-STUDENT:Student_ID (Primary Key),Admission No,Name,DOB,Phone No,E-mail,Age (Derived/optional)
-INSTRUCTOR:Instructor_ID (Primary Key),Name,Phone No,E-mail,Experience
-COURSE:Course_ID (Primary Key),Course Name,Credits,Faculty
-ENROLLMENT:Student_ID (Foreign Key),Course_ID (Foreign Key),Enrollment Date
...

## Relationships and Constraints:
```
1.INCLUDES
Entities involved: PROGRAM — STUDENT
Cardinality: One program includes many students (1:N)
Participation: Total on STUDENT, Partial on PROGRAM
2.OFFERS (Program → Course)
Cardinality: One program offers many courses (1:N)
Participation: Partial on PROGRAM, Total on COURSE
3.HAS (Program → Instructor)
Cardinality: One program has many instructors (1:N)
Participation: Partial
4.TEACHES (Instructor → Course)
Cardinality: One instructor teaches many courses (1:N)
Participation: Partial
5.ENROLLS IN (Student → Course)
Cardinality: Many-to-Many (M:N)
Participation: Partial
```
## Extension (Prerequisite / Billing):
Prerequisite is modeled via a recursive relationship on the COURSE entity. This allows one course to reference another as a prerequisite.

Billing is not represented in this diagram. To support billing, you would introduce a new entity like BILLING with attributes (Bill_ID, Student_ID, Amount, Date) and relate it to STUDENT (1:N).

## Design Choices:
-Derived Attribute: Age is derived from DOB, showing normalization.
-Use of ENROLLMENT Entity: To resolve the M:N relationship between STUDENT and COURSE.
-Recursive Relationship: The COURSE entity uses this to elegantly model prerequisites.
-Modular Design: Entities are separated logically by roles (e.g., STUDENT, COURSE, INSTRUCTOR), improving maintainability.
-Departmental Structure: Reflects academic hierarchy by linking DEPARTMENT to both PROGRAM and INSTRUCTOR.

## RESULT
Thus the er diagram was created with entities,attributes and relationships.

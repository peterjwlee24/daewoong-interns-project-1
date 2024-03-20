# Student Grading Portal Backend System

## Project Overview

Develop a Node.js and MongoDB backend system for a student grading portal. The system supports student and teacher interactions with academic records, including viewing and updating grades, managing class enrollments, and calculating GPAs.

## Technology Stack

- **Backend:** Node.js
- **Database:** MongoDB
- **Testing Tool:** Postman

## Database Schemas and Relationships

### Students Schema

```json
{
  "_id": "<MongoDB Generated ID>",
  "name": "string",
  "major": "string"
}
```
### Teachers Schema

```json
{
  "_id": "<MongoDB Generated ID>",
  "name": "string",
  "subjectsTaught": ["string"]
}
```
### Classes Schema

```json
{
  "_id": "<MongoDB Generated ID>",
  "classId": "string",
  "subject": "string",
  "teacher_id": "<MongoDB Teachers _id>",
  "student_ids": ["<MongoDB Students _id>"]
}
```
### Grades Schema

```json
{
  "_id": "<MongoDB Generated ID>",
  "student_id": "<MongoDB Students _id>",
  "class_id": "<MongoDB Classes _id>",
  "grade": "string",
  "semester": "string",
  "year": "number"
}
```
# GPA Calculation Method
GPAs are calculated based on the grades obtained in each course, converted to grade points (e.g., A = 4, B = 3), and then averaged. Assume each course contributes equally to the GPA.

# API Specifications with Sample Requests and Error Handling

## For Students

- **POST `/students`**: Create a new student profile.
  - **Sample Request Body**:
    ```json
    {
      "name": "Jane Doe",
      "major": "Computer Science"
    }
    ```

## For Teachers

- **POST `/teachers`**: Create a new teacher profile.
  - **Sample Request Body**:
    ```json
    {
      "name": "John Smith",
      "subjectsTaught": ["Mathematics", "Physics"]
    }
    ```

## For Grades

- **POST `/grades`**: Add a grade record for a student in a class.
  - **Sample Request Body**:
    ```json
    {
      "student_id": "<MongoDB Students _id>",
      "class_id": "<MongoDB Classes _id>",
      "grade": "A",
      "semester": "Fall",
      "year": 2023
    }
    ```

## GPA Calculation APIs

- **GET `/students/{studentId}/gpa/{semester}`**: Calculate the GPA for a specific semester.
  - **Error Cases**: If studentId or semester is invalid, return 404 Not Found.

- **GET `/students/{studentId}/gpa`**: Calculate the cumulative GPA across all semesters.
  - **Error Cases**: If studentId is invalid, return 404 Not Found.

## Additional APIs

- **PUT `/grades/{gradeId}`**: Update a specific grade record.
  - **Sample Request Body**:
    ```json
    {
      "grade": "B+"
    }
    ```

- **GET `/students/{studentId}/grades`**: Fetch all grades for a student.

- **GET `/teachers/{teacherId}/classes`**: List all classes taught by a teacher.

- **PUT `/classes/{classId}/enroll`**: Enroll students in a class.
  - **Sample Request Body**:
    ```json
    {
      "student_ids": ["<MongoDB Students _id>"]
    }
    ```

- **DELETE `/classes/{classId}/drop`**: Drop a student from a class.
  - **Sample Request Body**:
    ```json
    {
      "student_id": "<MongoDB Students _id>"
    }
    ```

- **GET `/grades/class/{classId}`**: Get all grades for a class.

# Submission Guidelines

Include project code in a zip file and send to daewoongstaff@gmail.com by June 2nd, 2024 11:59PM PST and Postman screenshots (successful and error interactions) as attachments to the same email, and name and team in the subject line of the email. Please test that your zip file can be extracted where if I get your zip file I should be able to unzip it easily and read through the code. 

# Chat GPT and Help and Rules
You are allowed to use ChatGPT to help you with understanding concepts and debugging your code. You are NOT allowed to use ChatGPT to write the API code for you. My team and I will spend the first two weeks of June reviewing each student's code. If we suspect ChatGPT was used to generate all the code, we will do an investigation and have a review together to determine if you will be allowed to continue the internship with our organization during the summer. Please be honest when doing this project. You will have about 2 months to complete this where half these APIs will be copy and pasting the same code logic. If you take your time and not wait until the last minute, you will finish without any stress. You can also reach out to me during those 2 months and I will be happy to do office hours to help students who are stuck. If you wait until the last minute and never reached out for help and never finished, this will lead to a conversation if the internship is a right fit at the time. Please know you will get tons of support! Please just manage your time effectively and this project should not take too much time. 

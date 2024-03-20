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

# COMP1004 Database Exam Guide

Source: exam info provided by Alex.

## Exam Structure

- Duration: 2 hours
- Platform: Examsys
- Total: 4 main questions
- Each main question has multiple parts.

## Question Types

Expect a mixture of:

- multiple choice questions;
- fill in the blanks;
- short answer questions;
- SQL query writing.

## Topics Included

The exam covers:

- entity relationship modelling;
- normalisation;
- structured query language, including DDL and DML.

## What This Means for Revision

The exam is likely to test both recognition and production.

Recognition questions include MCQs and fill-in-the-blanks. These usually reward precise definitions and knowing the correct vocabulary.

Production questions include short answers, ER modelling, normalisation steps, and SQL writing. These need you to show the method, not just know the term.

## Priority 1: Entity Relationship Modelling

You should be able to:

- identify entities, attributes, and relationships from a scenario;
- choose sensible primary keys;
- explain cardinality, such as one-to-one, one-to-many, and many-to-many;
- map an ER diagram into relational tables;
- use foreign keys to represent relationships;
- create a junction table for many-to-many relationships.

Typical answer pattern:

```text
Student(StudentID, StudentName)
Module(ModuleCode, ModuleTitle)
Enrolment(StudentID, ModuleCode)
```

Here, `Enrolment` represents the many-to-many relationship between students and modules.

## Priority 2: Normalisation

You should be able to:

- explain why normalisation is used;
- identify functional dependencies;
- recognise insertion, update, and deletion anomalies;
- convert unnormalised data to 1NF;
- convert 1NF to 2NF;
- convert 2NF to 3NF.

Quick definitions:

- 1NF: values are atomic, with no repeating groups.
- 2NF: in 1NF, and every non-key attribute depends on the whole key.
- 3NF: in 2NF, and no non-key attribute depends on another non-key attribute.

Typical method:

1. Find the key.
2. Find functional dependencies.
3. Remove repeating groups for 1NF.
4. Remove partial dependencies for 2NF.
5. Remove transitive dependencies for 3NF.

## Priority 3: SQL DDL

DDL is used to define database structures.

Know how to write:

```sql
CREATE TABLE Student (
    StudentID INT PRIMARY KEY,
    StudentName VARCHAR(100) NOT NULL,
    Email VARCHAR(255) UNIQUE
);
```

Also know common constraints:

- `PRIMARY KEY`
- `FOREIGN KEY`
- `NOT NULL`
- `UNIQUE`
- `CHECK`
- `DEFAULT`

Foreign key example:

```sql
CREATE TABLE Enrolment (
    StudentID INT,
    ModuleCode VARCHAR(20),
    PRIMARY KEY (StudentID, ModuleCode),
    FOREIGN KEY (StudentID) REFERENCES Student(StudentID),
    FOREIGN KEY (ModuleCode) REFERENCES Module(ModuleCode)
);
```

## Priority 4: SQL DML

DML is used to work with the data inside tables.

Know these commands:

```sql
INSERT INTO Student (StudentID, StudentName)
VALUES (1001, 'Asha Khan');
```

```sql
UPDATE Student
SET StudentName = 'Asha K'
WHERE StudentID = 1001;
```

```sql
DELETE FROM Student
WHERE StudentID = 1001;
```

```sql
SELECT StudentName
FROM Student
WHERE Course = 'Computer Science';
```

For query writing, practise:

- `SELECT`
- `WHERE`
- `ORDER BY`
- aggregate functions such as `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`
- `GROUP BY`
- `HAVING`
- joins
- subqueries

## Two-Hour Exam Strategy

Because there are 4 main questions in 2 hours, you have about 30 minutes per main question.

A sensible split:

- first 5 minutes: scan all questions;
- about 25-30 minutes per main question;
- final 5 minutes: check SQL syntax and missing parts.

For SQL questions, check:

- table names are correct;
- selected columns match the question;
- joins use the right keys;
- `WHERE` filters rows;
- `HAVING` filters grouped results;
- every `UPDATE` and `DELETE` has a `WHERE` clause unless the question clearly asks for all rows.

## Best Final Revision Tasks

1. Write five ERD-to-table mappings.
2. Normalise three messy tables to 3NF.
3. Write ten `SELECT` queries using joins and grouping.
4. Write five `CREATE TABLE` statements with primary and foreign keys.
5. Practise explaining 1NF, 2NF, and 3NF in one sentence each.


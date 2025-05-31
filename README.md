# SQL-101
Welcome to SQL world.
CREATE DATABASE collage3;
USE collage3;

'''
CREATE TABLE student(
id INT PRIMARY KEY,
name VARCHAR(50)
);

INSERT INTO student
VALUES
(101,"adam"),
(102,"bob"),
(103,"casey");

CREATE TABLE course(
id INT PRIMARY KEY,
course VARCHAR(50)
);

INSERT INTO course
VALUES
(102,"english"),
(105,"math"),
(103,"science"),
(107,"computer scinence");

SELECT * FROM student;
SELECT * FROM course;

SELECT * FROM student AS s
LEFT JOIN course AS c
ON s.id = c.id;'''

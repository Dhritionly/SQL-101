

## SQL JOINS





SQL joins are essential for bringing together data from multiple tables based on related columns. Understanding the different types allows for powerful data retrieval and analysis.

First Going deep into that Part We have to create a Database after that Two sample dataset to perform these actions.

```

CREATE DATABASE collage3;

USE collage3;

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

```

Run Last two lines two lines so check if the dataset is working Properly or not.

**If your code is not working or partially working then type it manually.**

Student Table

![student](https://github.com/user-attachments/assets/d8fd3985-02c5-40e6-ae9a-4b6d4bbd8acd)




Course Table


![Course](https://github.com/user-attachments/assets/3bee32bf-a1b0-4e27-b92f-6a2144d98adb)


Here's a breakdown of the key concepts:

Inner Join: This join returns only the rows that have matching values in both tables, showing the common data between them.

```

SELECT * FROM student

INNER JOIN course

ON student.id = course.id;

```

Output :


![inner](https://github.com/user-attachments/assets/3ce29a35-a7ee-4317-aed8-2bef1587005e)




Left Join (or Left Outer Join): With a Left Join, you get all records from the "left" table, plus any matching records from the "right" table. If there's no match on the right, the right-side columns will show as NULL.

```

SELECT * FROM student

LEFT JOIN course

ON student.id = course.id;

```

Output:


![left](https://github.com/user-attachments/assets/b9ed79b7-da82-4bb2-af36-dce0667d8c49)




Right Join (or Right Outer Join): Conversely, a Right Join retrieves all records from the "right" table, along with any matching records from the "left" table. Non-matching left-side columns will appear as NULL.

```

SELECT * FROM student

RIGHT JOIN course

ON student.id = course.id;

```

Output:


![Right](https://github.com/user-attachments/assets/bb96547a-19bb-420e-a0c7-5d986d270e76)




Full Join (or Full Outer Join): This join returns all records when there's a match in either the left or the right table. It effectively combines all unique rows from both tables.

```

SELECT * FROM student

LEFT JOIN course

ON student.id = course.id

UNION

SELECT * FROM student

RIGHT JOIN course

ON student.id = course.id;

```

Output:




![full ](https://github.com/user-attachments/assets/658ebfd1-b9bc-4d23-a530-cbf388c1f95b)



Left Exclusive Join: This type of join specifically returns only the data present in the left table that is not common in the right table.

```

SELECT * FROM student

LEFT JOIN course

ON student.id = course.id

WHERE course.id IS NULL

```

Output:


![left exclu](https://github.com/user-attachments/assets/790087b8-241a-4b4a-addb-f5e2d3bb469d)



Right Exclusive Join: Similar to the Left Exclusive Join, this returns only the data present in the right table that is not common in the left table.

```

SELECT * FROM student

RIGHT JOIN course

ON student.id = course.id

WHERE student.id IS NULL

```

Output:



![right excle](https://github.com/user-attachments/assets/10f2ef0d-8861-4ead-9a6f-77b4b0531094)




Full Exclusive Join: This concept represents data that is in either table but has no common data between them.

```

SELECT * FROM student

LEFT JOIN course

ON student.id = course.id

WHERE course.id IS NULL

UNION

SELECT * FROM student

RIGHT JOIN course

ON student.id = course.id

WHERE student.id IS NULL;

```

Output:


![full exclusive](https://github.com/user-attachments/assets/8d2d06e6-3382-4bb8-a459-381ddbcfd6b0)




Self Join: A Self Join is used when you need to combine rows from a single table with itself. This is useful when different types of related data exist within the same table, for example, finding managers and their employees from an employee table.

Let's Create another dataset for this task

```

CREATE TABLE employee(

id INT PRIMARY KEY,

name VARCHAR(50),

manager_id int);

INSERT INTO employee

VALUES

(101, "adam", 103),

(102,"bob",104),

(103,"casey",NULL),

(104,"donald",103);

SELECT * FROM employee;

```

Now to perform the " Self Join " ,

```

SELECT *

FROM employee as a

JOIN employee as b

ON a.id = b.manager_id;

```

Output:




![self](https://github.com/user-attachments/assets/0ab07da9-f08e-4eeb-913f-8b28aaf8a0f8)




Understanding Aliases: Aliases are temporary names given to tables or columns in a SQL query. They are often used to make queries shorter, more readable, and easier to manage, especially when dealing with long table names or when performing self-joins where a table is referenced multiple times.
> 

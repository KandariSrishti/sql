--QUESTION 1
-- INIT database
-- Create the Students table
CREATE TABLE Students (
    student_id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    grade_level INT
);

-- Create the Courses table
CREATE TABLE Courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(50),
    credits INT
);

-- Create the Enrollments table
CREATE TABLE Enrollments (
    enrollment_id INT PRIMARY KEY,
    student_id INT,
    course_id INT,
    grade DECIMAL(3, 2),
    FOREIGN KEY (student_id) REFERENCES Students(student_id),
    FOREIGN KEY (course_id) REFERENCES Courses(course_id)
);

-- Insert sample data into Students
INSERT INTO Students (student_id, name, age, grade_level) VALUES
(1, 'Alice', 20, 3),
(2, 'Bob', 21, 4),
(3, 'Charlie', 19, 3),
(4, 'Diana', 22, 4),
(5, 'Ethan', 20, 3);

-- Insert sample data into Courses
INSERT INTO Courses (course_id, course_name, credits) VALUES
(1, 'Math', 3),
(2, 'Science', 4),
(3, 'History', 3),
(4, 'Art', 2);

-- Insert sample data into Enrollments
INSERT INTO Enrollments (enrollment_id, student_id, course_id, grade) VALUES
(1, 1, 1, 3.5),
(2, 1, 2, 4.0),
(3, 2, 1, 2.5),
(4, 2, 3, 3.0),
(5, 3, 2, 3.0),
(6, 3, 4, 2.0),
(7, 4, 1, 3.5),
(8, 4, 3, 4.0),
(9, 5, 2, 3.0),
(10, 5, 4, 3.5);
SELECT AVG(grade) AS average_grade
FROM Enrollments;

<img width="406" alt="image" src="https://github.com/user-attachments/assets/c00c6322-4828-421d-862a-c5c323d41377">


--QUESTION 2

SELECT Students.name, Courses.course_name
FROM Students
INNER JOIN Enrollments ON Students.student_id = Enrollments.student_id
INNER JOIN Courses ON Enrollments.course_id = Courses.course_id; 1 

<img width="401" alt="image" src="https://github.com/user-attachments/assets/466b21b6-21d5-49b2-ac46-fe1d5bf779e5">


--QUESTION 3

SELECT grade_level, COUNT(*) AS student_count 
FROM Students 
GROUP BY grade_level;

<img width="447" alt="image" src="https://github.com/user-attachments/assets/3dff2747-a1dd-4e74-8df0-e475d75f1ae9">


--QUESTION 4

SELECT Courses.course_name, MAX(Enrollments.grade) AS max_grade
FROM Courses
INNER JOIN Enrollments ON Courses.course_id = Enrollments.course_id
GROUP BY Courses.course_name;

<img width="460" alt="image" src="https://github.com/user-attachments/assets/6dceed82-831b-443d-b49e-f4847ef87a84">


--QUESTION 5

SELECT AVG(grade) AS average_grade 
FROM Enrollments 
INNER JOIN Students ON Enrollments.student_id = Students.student_id 
WHERE Students.grade_level = 3;

<img width="338" alt="image" src="https://github.com/user-attachments/assets/145df314-7777-4acf-867a-454b21d8c45f">


--QUESTION 6

SELECT Students.name, Courses.course_name, Courses.credits
FROM Students
INNER JOIN Enrollments ON Students.student_id = Enrollments.student_id
INNER JOIN Courses ON Enrollments.course_id = Courses.course_id;

<img width="428" alt="image" src="https://github.com/user-attachments/assets/7d9c0589-da93-4883-9817-918d7f360288">


--QUESTION 7

SELECT Courses.course_name
FROM Courses
INNER JOIN Enrollments ON Courses.course_id = Enrollments.course_id
GROUP BY Courses.course_id
HAVING AVG(Enrollments.grade) > 3.0;

<img width="314" alt="image" src="https://github.com/user-attachments/assets/3c5c03d1-7fc8-4c63-b521-8b1b029845b6">


--QUESTION 8

SELECT Students.student_id, Students.name 
FROM Students 
LEFT JOIN Enrollments ON Students.student_id = Enrollments.student_id 
WHERE Enrollments.grade IS NULL OR Enrollments.grade <> 4.0 
GROUP BY Students.student_id, Students.name 
HAVING MAX(Enrollments.grade) IS NULL OR MAX(Enrollments.grade) <> 4.0;

<img width="430" alt="image" src="https://github.com/user-attachments/assets/783c32b3-7797-4ba7-bc8b-675095c27fb5">


--QUESTION 9

SELECT Students.name
FROM Students
INNER JOIN Enrollments ON Students.student_id = Enrollments.student_id
GROUP BY Students.student_id
HAVING AVG(Enrollments.grade) > (SELECT AVG(grade) FROM Enrollments);

<img width="388" alt="image" src="https://github.com/user-attachments/assets/a88067ac-8c7c-426e-ab8e-ed45df7e413a">


--QUESTION 1O

SELECT Students.name, COUNT(Enrollments.course_id) AS total_courses, AVG(Enrollments.grade) AS average_grade
FROM Students
INNER JOIN Enrollments ON Students.student_id = Enrollments.student_id
GROUP BY Students.student_id;

<img width="436" alt="image" src="https://github.com/user-attachments/assets/0518d5b3-3223-48aa-b6ce-3815a6aa4f26">

















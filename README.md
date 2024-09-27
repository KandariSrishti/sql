-- INIT database -- Create the Students table CREATE TABLE Students ( student_id INT PRIMARY KEY, name VARCHAR(50), age INT, grade_level INT );

-- Create the Courses table CREATE TABLE Courses ( course_id INT PRIMARY KEY, course_name VARCHAR(50), credits INT );

-- Create the Enrollments table CREATE TABLE Enrollments ( enrollment_id INT PRIMARY KEY, student_id INT, course_id INT, grade DECIMAL(3, 2), FOREIGN KEY (student_id) REFERENCES Students(student_id), FOREIGN KEY (course_id) REFERENCES Courses(course_id) );

-- Insert sample data into Students INSERT INTO Students (student_id, name, age, grade_level) VALUES (1, 'Alice', 20, 3), (2, 'Bob', 21, 4), (3, 'Charlie', 19, 3), (4, 'Diana', 22, 4), (5, 'Ethan', 20, 3);

-- Insert sample data into Courses INSERT INTO Courses (course_id, course_name, credits) VALUES (1, 'Math', 3), (2, 'Science', 4), (3, 'History', 3), (4, 'Art', 2);

-- Insert sample data into Enrollments INSERT INTO Enrollments (enrollment_id, student_id, course_id, grade) VALUES (1, 1, 1, 3.5), (2, 1, 2, 4.0), (3, 2, 1, 2.5), (4, 2, 3, 3.0), (5, 3, 2, 3.0), (6, 3, 4, 2.0), (7, 4, 1, 3.5), (8, 4, 3, 4.0), (9, 5, 2, 3.0), (10, 5, 4, 3.5); SELECT AVG(grade) AS average_grade FROM Enrollments;


![image](https://github.com/user-attachments/assets/8487b8f6-f160-444b-815b-4bb945543091)

SELECT Students.name, Courses.course_name FROM Students INNER JOIN Enrollments ON Students.student_id = Enrollments.student_id INNER JOIN Courses ON Enrollments.course_id = Courses.course_id; 1


![image](https://github.com/user-attachments/assets/6375fa58-74ab-4a8c-9dd9-cb3111fdcaec)

SELECT grade_level, COUNT(*) AS student_count FROM Students GROUP BY grade_level;


![image](https://github.com/user-attachments/assets/92ff73ef-74db-45fa-ad3e-9803f58a9ca7)

SELECT Courses.course_name, MAX(Enrollments.grade) AS max_grade FROM Courses INNER JOIN Enrollments ON Courses.course_id = Enrollments.course_id GROUP BY Courses.course_name;


![image](https://github.com/user-attachments/assets/5e5fd891-3951-4d11-b28f-f36805a7ee6c)

SELECT AVG(grade) AS average_grade FROM Enrollments INNER JOIN Students ON Enrollments.student_id = Students.student_id WHERE Students.grade_level = 3;


![image](https://github.com/user-attachments/assets/1e5e742b-f59e-4650-9dbc-288a95fbb49a

SELECT Students.name, Courses.course_name, Courses.credits FROM Students INNER JOIN Enrollments ON Students.student_id = Enrollments.student_id INNER JOIN Courses ON Enrollments.course_id = Courses.course_id;


![image](https://github.com/user-attachments/assets/1dd628bc-e57f-4542-a4d6-641eed48683a)

SELECT Courses.course_name FROM Courses INNER JOIN Enrollments ON Courses.course_id = Enrollments.course_id GROUP BY Courses.course_id HAVING AVG(Enrollments.grade) > 3.0;


![image](https://github.com/user-attachments/assets/8feb3e65-6560-499e-83ce-0f8bb180d1d6)

SELECT Students.student_id, Students.name FROM Students LEFT JOIN Enrollments ON Students.student_id = Enrollments.student_id WHERE Enrollments.grade IS NULL OR Enrollments.grade <> 4.0 GROUP BY Students.student_id, Students.name HAVING MAX(Enrollments.grade) IS NULL OR MAX(Enrollments.grade) <> 4.0;


![image](https://github.com/user-attachments/assets/a877d97e-78fd-41ea-9f1c-9b9781f65c9b)

SELECT Students.name FROM Students INNER JOIN Enrollments ON Students.student_id = Enrollments.student_id GROUP BY Students.student_id HAVING AVG(Enrollments.grade) > (SELECT AVG(grade) FROM Enrollments);


![image](https://github.com/user-attachments/assets/f37fe14f-8db3-4c43-91b2-bac7f299d453)

SELECT Students.name, COUNT(Enrollments.course_id) AS total_courses, AVG(Enrollments.grade) AS average_grade FROM Students INNER JOIN Enrollments ON Students.student_id = Enrollments.student_id GROUP BY Students.student_id;


![image](https://github.com/user-attachments/assets/bf33c99d-753f-4ae5-ad11-3400b1ed9db6)







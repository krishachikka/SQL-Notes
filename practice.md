# SQL Interview Practice – Student Table

## Select the Database
```sql
USE interview;
````

## Create the Student Table

```sql
-- create table
create table Student (
	RollNo int primary key,
    Name varchar(100) not null,
    Marks int
);
```

## Insert Dummy Data

```sql
insert into Student (RollNo, Name, Marks)
values
  (1, 'Aarav Mehta', 85),
  (2, 'Riya Kapoor', 92),
  (3, 'Dev Sharma', 76),
  (4, 'Ananya Rao', 89),
  (5, 'Kabir Singh', 67);

insert into Student (RollNo, Name, marks)
values (6, 'Krisha', 99);
```
<img width="279" height="216" alt="image" src="https://github.com/user-attachments/assets/ba7e50d4-2555-4b33-95b8-bca86aa538f3" />

## Filter Students with Marks ≥ 70

```sql
select * from Student where marks >= 70;
```
<img width="280" height="201" alt="image" src="https://github.com/user-attachments/assets/298b7cdf-7652-4fdf-86a4-6351378d09de" />

## Add a Department Column

```sql
-- adding another column 
alter table Student 
add dept varchar(100);
```

## Update Data

```sql
UPDATE Student SET Marks = '85' WHERE Name = 'Dev Sharma';
UPDATE Student SET Dept = 'IT';
```
<img width="337" height="217" alt="image" src="https://github.com/user-attachments/assets/961d2f42-bccf-48d3-9711-c6cf0a04e2bd" />

```sql
UPDATE Student SET Dept = 'CS' WHERE Marks >= 80;
UPDATE Student SET Dept = 'Comps' WHERE Name = 'Krisha';
UPDATE Student SET Dept = NULL WHERE Name = 'Krisha';
```
<img width="343" height="229" alt="image" src="https://github.com/user-attachments/assets/671fd277-3176-45f3-b542-e27be3c097c0" />

## Count Students in Each Department

```sql
select Dept, count(*) as StudentCount
from Student
group by Dept;
```
<img width="240" height="133" alt="image" src="https://github.com/user-attachments/assets/43400d4f-efb0-483a-9f83-7890797c9286" />

## Second Highest Marks

```sql
select max(marks) as second_highest from Student
  where marks < (select max(marks) from Student);

```
<img width="220" height="110" alt="image" src="https://github.com/user-attachments/assets/5536a0e9-7a67-4dd6-ae80-aa29adf7c5ea" />

## Students Without Assigned Department

```sql
select * from Student where dept is null;
```
<img width="298" height="116" alt="image" src="https://github.com/user-attachments/assets/c3adb00e-7d1d-44e4-9470-9871ae243e1b" />

## List All Distinct Departments

```sql
select distinct (dept) from Student;
```
<img width="135" height="150" alt="image" src="https://github.com/user-attachments/assets/b73e3c86-c357-4603-89b9-620bd19c2641" />

## Order Students by Marks (Descending)

```sql
select * from Student order by marks desc;
```
<img width="382" height="248" alt="image" src="https://github.com/user-attachments/assets/04374d41-54ce-48fc-a584-f68dc486b3f6" />

## Count Students Scoring Between 70 and 90

```sql
select Count(*) from student
WHERE Marks BETWEEN 70 AND 90;
```
<img width="138" height="86" alt="image" src="https://github.com/user-attachments/assets/8188f9bb-94c2-41d2-bfb8-fd622f1c8b49" />

## Departments with More Than 2 Students

```sql
select dept from student
  group by dept
  having count(*) >2;
```
<img width="160" height="109" alt="image" src="https://github.com/user-attachments/assets/d453e0b3-89db-454d-9713-47dff1cac2d4" />

## Students with Duplicate Marks

```sql
-- Find students who have the same marks as someone else
select * from student where marks in(
	select marks from student group by marks having count(*) > 1
);
```
<img width="367" height="140" alt="image" src="https://github.com/user-attachments/assets/756786f3-51f4-4ba2-8323-c7144a1e3222" />

## Average Marks in Each Department

```sql
-- avg marks in each dept
select dept, avg(marks) as avgmarks from student group by dept;
```
<img width="250" height="148" alt="image" src="https://github.com/user-attachments/assets/d9220339-0012-4858-b6e4-f1ac8d8846c4" />

## Students Whose Names Start With 'A'

```sql
--  Students whose name starts with 'A'
select * from student where name like 'A%';
```
<img width="407" height="150" alt="image" src="https://github.com/user-attachments/assets/c2b73c5e-d609-43bd-b725-6ac8cd2087fd" />

## Top 3 Scoring Students

```sql
select * from student order by marks desc limit 3;
```
<img width="363" height="169" alt="image" src="https://github.com/user-attachments/assets/afcf5658-9771-4ae7-98a2-f99a89d96ce9" />

## Percentage of Students in Each Department

```sql
SELECT Dept,
       ROUND(COUNT(*) * 100.0 / (SELECT COUNT(*) FROM Student), 2) AS Percentage
FROM Student
GROUP BY Dept;
```
<img width="237" height="150" alt="image" src="https://github.com/user-attachments/assets/0de83e73-d078-4de6-87af-69a446cfbc7a" />

## Students Scoring Above Department Average

```sql
 select * from student s
  where marks > (
  select avg(marks) from student
  where dept = s.dept);

```
<img width="337" height="132" alt="image" src="https://github.com/user-attachments/assets/78fc4434-9201-4f86-8fd7-473cd0b1a422" />

## Student(s) with Lowest Marks in Each Department

```sql
 select * from student s
  where marks = (
  select min(marks) from student
  where dept = s.dept);

```
<img width="367" height="197" alt="image" src="https://github.com/user-attachments/assets/7056da4b-1d8d-464e-a6cd-547bd233cb50" />

## View Full Table

```sql
SELECT * FROM Student;
```
<img width="354" height="208" alt="image" src="https://github.com/user-attachments/assets/28e585f8-a603-41c9-b0ce-3161dc8be361" />

---
[← Transactions](./transactions.md) | [Back to Home](./README.md)

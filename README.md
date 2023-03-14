# SQL_assignment
# SQLDBAssignment 
## Creating tables 
### Creating Table 
**EmployeeInfo**  
CREATE table EmployeeInfo(<br>
EmpID SERIAL PRIMARY KEY,<br>
EmpFname VARCHAR(50) NOT NULL,<br>
EmpLname VARCHAR(50) NOT NULL,<br>
Department VARCHAR(50) ,<br>
Project VARCHAR(50) ,<br>
Address VARCHAR(100),<br>
DOB DATE,<br>
Gender CHAR(1) <br>
);<br> 
#### Output of above table will be:
https://simformsolutionspvtltd-my.sharepoint.com/:i:/g/personal/janvi_s_simformsolutions_com/EYDavU-7H8tMn6U0bmNrFF4BcafH91oxVxMFHcUHAh4eVw?email=eshan%40simformsolutions.com&e=k5uuhJ
### Inserting data in this table
INSERT INTO EmployeeInfo(EmpFname,EmpLname,Department,Project,Address,DOB,Gender)<br>
VALUES('Sanjay','Mehra','HR','P1','Hyderabad(HYD)','01/12/1976','M'),<br>
('Ananya','Mishra','Admin','P2','Delhi(DEL)','02/05/1968','F'),<br>
('Rohan','Diwan','Account','P3','Mumbai(BOM)','01/01/1980','M'),<br>
('Sonia','Kulkarni','HR','P1','Hyderabad(HYD)','02/05/1992','F'),<br>
('Ankit','Kapoor','Admin','P2','Delhi(DEL)','03/07/1994','M');<br>
#### Output of above table will be:
https://simformsolutionspvtltd-my.sharepoint.com/:i:/g/personal/janvi_s_simformsolutions_com/EWSb8mViuhVArmD0wDBTgSwBPSS-JE7JtflUYM0yKWPjIg?email=eshan%40simformsolutions.com&e=r4598g

### Creating Table 
**EmployeePosition**  
CREATE table EmployeePosition(<br>
EmpID SERIAL NOT NULL,<br>
EmpPosition VARCHAR(50) NOT NULL,<br>
DateofJoining DATE,<br>
Salary INT,<br>
CONSTRAINT pk_EmposID PRIMARY KEY(EmpID),<br>
CONSTRAINT fk_EmPos_EmpID FOREIGN KEY(EmpID) REFERENCES EmployeeInfo(EmpID)<br>
);<br>  
#### Output of above table will be:
https://simformsolutionspvtltd-my.sharepoint.com/:i:/g/personal/janvi_s_simformsolutions_com/EWFINKMusOBMjR7I1L-htrsB06420ZgHEXQaXdZ1jT_WSA?email=eshan%40simformsolutions.com&e=XEEdO1

### Inserting data in this table
INSERT INTO EmployeePosition(EmpId,EmpPosition,DateofJoining,Salary)<br>
VALUES(1,'Manager','01/05/2022',500000),<br>
(2,'Executive','02/05/2022',75000),<br>
(3,'Manager','01/05/2022',90000),<br>
(4,'Lead','02/05/2022',85000),<br>
(5,'Executive','01/05/2022',300000);<br> 
#### Output of above table will be
https://simformsolutionspvtltd-my.sharepoint.com/:i:/g/personal/janvi_s_simformsolutions_com/EczGi8CmqydKi2vOzZ77GoUBkRzg1tbOHs4dFDZY_Ohg6A?email=eshan%40simformsolutions.com&e=wBEUr9

>### Question 1
>Write a query to fetch the number of employees working in the department ‘Admin’:<br>  
>*SELECT COUNT( * ) FROM EmployeeInfo*<br>
>*WHERE department='Admin';*<br>
>* Here COUNT() function is used in SELECT function to return the number of employees working in Admin department.<br>
>* The COUNT() function is an aggregate function that allows you to get the number of rows that match a specific condition of a query.
>#### Output will be:
>https://simformsolutionspvtltd-my.sharepoint.com/:i:/g/personal/janvi_s_simformsolutions_com/EYT5euGhZ2RHmgRvckaWMEABCYyRTNXfl0QAikTTW1U5NQ?email=eshan%40simformsolutions.com&e=EMDnV6 <br>  
>### Question 2    
>Write a query to retrieve the first four characters of  EmpLname from the EmployeeInfo table.<br>    
>*SELECT substr(EmpLname,1,4) as Firstfourchars <br>*
>*FROM EmployeeInfo;*<br>
>* The PostgreSQL SUBSTR() function returns a portion of string, beginning at a specified character position, and a specified number of characters long.<br>
>#### Output will be:
>https://simformsolutionspvtltd-my.sharepoint.com/:i:/g/personal/janvi_s_simformsolutions_com/EQIWL10i6HlAsDnAuw-Uzq4BXzb_XVdwBQDGBa6Sz_-Qgw?email=eshan%40simformsolutions.com&e=8cqzay  
>### Question 3
>Write q query to find all the employees whose salary is between 50000 to 100000.<br>  
>*SELECT Einfo.EmpID,Einfo.EmpFname,Einfo.EmpLname,Epos.Salary <br>*
>*FROM EmployeeInfo einfo*<br>
>*INNER JOIN EmployeePosition Epos*<br>
>*ON Einfo.EmpID=Epos.EmpID*<br>
>*WHERE Epos.Salary BETWEEN 50000 AND 100000;*<br>
>#### Output will be:
>https://simformsolutionspvtltd-my.sharepoint.com/:i:/g/personal/janvi_s_simformsolutions_com/ERmp2j5EaWZAoHy11qmNZEIBC72o61tssY5P4HiWxDRw3g?email=eshan%40simformsolutions.com&e=jv1bkm
>### Question 4
>Write a query to find the names of employees that begin with ‘S’.<br>  
>*SELECT EmpFname,EmpLname*<br>
>*FROM employeeinfo*<br>
>*WHERE empfname LIKE 'S%';*<br>
>* Apart from this if we want to make the search case insensitive, we can use the ILIKE as well.<br>
>#### Output will be:
>https://simformsolutionspvtltd-my.sharepoint.com/:i:/g/personal/janvi_s_simformsolutions_com/EXy-lZf5u-hNnMh0U8M-b-MB3yQixTfSbkh7SMBY4OO-6A?email=eshan%40simformsolutions.com&e=FxardV
>### Question 5
>Write a query to fetch top N records order by salary. (ex. top 5 records).<br>  
>*SELECT Einfo.EmpID,Einfo.EmpFname,Einfo.EmpLname,Epos.Salary*<br>
>*FROM EmployeeInfo einfo*<br>
>*INNER JOIN EmployeePosition Epos*<br>
>*ON Einfo.EmpID=Epos.EmpID*<br>
>*ORDER BY Epos.salary DESC*<br>
>*LIMIT 5;*<br>
>* LIMIT restricts the number of outputs a query returns.<br> 
>* LIMIT is not used as an SQL standard  practice, instead FETCH is used.<br>
> #### Output will be:
>https://simformsolutionspvtltd-my.sharepoint.com/:i:/g/personal/janvi_s_simformsolutions_com/ESDcxkyjkVFIrdK_lFYw4bwBP8Jo7Q31W8UggaM8a_wPfQ?email=eshan%40simformsolutions.com&e=NUWLWf
>### Question 6
>Write a query to fetch details of all employees excluding the employees with first names, “Sanjay” and “Sonia” from the EmployeeInfo table.<br>  
>*SELECT * <br>*
>*FROM EmployeeInfo*<br>
>*WHERE EmpFname NOT IN('Sanjay','Sonia');*<br>
> #### Output will be:
>https://simformsolutionspvtltd-my.sharepoint.com/:i:/g/personal/janvi_s_simformsolutions_com/ETS6B8XOH8lBonV2K4-AqYIB2Cuj7CrO7reLLBUeuWEb4w?email=eshan%40simformsolutions.com&e=fWLaDm
>### Question 7
>Write a query to fetch the department-wise count of employees sorted by department’s count in ascending order.<br><br>
>*SELECT department, COUNT( * ) AS EmployeeCount*<br>
>*FROM EmployeeInfo*<br>
>*GROUP BY department*<br>
>*ORDER BY EmployeeCount ASC;*<br>
> #### Output will be:
>https://simformsolutionspvtltd-my.sharepoint.com/:i:/g/personal/janvi_s_simformsolutions_com/EfmH1pjs5DNBtzKrCCHU494Bb5rqzZJZzet4Lfb2UOVk9Q?email=eshan%40simformsolutions.com&e=Jbyuk2
>### Question 8
>Create indexing for any particular field and show the difference in data fetching before and after indexing.<br>  
>*CREATE INDEX Salary_index ON EmployeePosition(Salary);*<br>
> #### Output will be:
>https://simformsolutionspvtltd-my.sharepoint.com/:i:/g/personal/janvi_s_simformsolutions_com/ERopvQmpYuZKnSTlxb4BPCsB5-Vxk_mqEWJdpEm3wHaTdA?email=eshan%40simformsolutions.com&e=wyMzjm
>* On examining the results closely, we find that the time cost reduces when we apply index on a particular column.<br>
>#### Before indexing
>https://simformsolutionspvtltd-my.sharepoint.com/:i:/g/personal/janvi_s_simformsolutions_com/Eeqq31RELDJFr-mu1gqgrxMBqz9dP5k8RkkrYT8pn3dkAA?email=eshan%40simformsolutions.com&e=2WhqoO
>#### After indexing
>https://simformsolutionspvtltd-my.sharepoint.com/:i:/g/personal/janvi_s_simformsolutions_com/EbiuVS5p7tpGtYjCJSRqq4oBR5-SXl4HozrPThSLTcvdDw?email=eshan%40simformsolutions.com&e=LJcryn
>* Here we can clearly see that after indexing execution time of same query is reduced  to 0.034 msecs from 0.107 msecs
>* This can make significant deifferent when handling large amount of data

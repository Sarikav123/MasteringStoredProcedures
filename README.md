# MasteringStoredProcedures
A collection of SQL stored procedures for efficient data manipulation and retrieval in a worker database.

1. Create a table with the following specifications.

   Worker_Id INT FirstName CHAR(25), LastName CHAR(25), Salary INT(15), JoiningDate DATETIME, Department CHAR(25))
     
      create table Worker (
      Worker_Id INT primary key,
      FirstName char(25),
      LastName char(25),
      Salary INT,
      JoiningDate DATETIME,
      Department CHAR(25)) ;
2. Create a stored puse employees;
      delimiter ##
      create procedure insert_data(IN id int,IN fname char(25),IN lname char(25),IN salary int,IN joining_date datetime,IN dept char(25))
      begin 
      insert into worker (worker_id,FirstName,LastName,Salary,JoiningDate,Department) values 
      (id,fname,lname,salary,joining_date,dept);
      select * from worker;
      end ##
      DELIMITER ;

3. 

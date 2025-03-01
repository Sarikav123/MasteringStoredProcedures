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
2. Create a stored procedure that takes in IN parameters for all the columns in the Worker table and adds a new record to the table and then invokes the procedure call. 
      delimiter ##
      create procedure insert_data(IN id int,IN fname char(25),IN lname char(25),IN salary int,IN joining_date datetime,IN dept char(25))
      begin 
      insert into worker (worker_id,FirstName,LastName,Salary,JoiningDate,Department) values 
      (id,fname,lname,salary,joining_date,dept);
      select * from worker;
      end ##
      DELIMITER ;
      call insert_data(1,'Sarika','Diju',3000000,'2025-10-08 10:00:00','DA');

3. Write stored procedure takes in an IN parameter for WORKER_ID and an OUT parameter for SALARY. It should retrieve the salary of the worker with the given ID and returns      it in the p_salary parameter
      DELIMITER ##
      create procedure worker_salary(IN worker_id int, OUT Salary_w INT)
      BEGIN 
      select Salary,Worker_id from worker where worker.worker_id=worker_id;
      END ##
      DELIMITER ;
      SET @salary=0;
      call worker_salary(1,@salary);

4. Create a stored procedure that takes in IN parameters for WORKER_ID and DEPARTMENT. It should update the department of the worker with the given ID. Then make a procedure    call.
   delimiter ##
   create procedure dept_update(IN workerid INT,IN Dept_u char(25))
   BEGIN
   SET SQL_SAFE_UPDATES=0;
   update worker set Department=Dept_u where worker_id=workerid;
   SET SQL_SAFE_UPDATES = 1;
   END ##
   delimiter ;
   
   call dept_update(2,'Pharmd')

5. Write a stored procedure that takes in an IN parameter for DEPARTMENT and an OUT parameter for p_workerCount. It should retrieve the number of workers in the given       
   department and returns it in the p_workerCount parameter. Make procedure call.

   delimiter ##
   create procedure workercount(IN dept char(25),OUT p_workerCount INT)
   begin
   select count(worker_id) from worker where department=dept;
   end ##
   delimiter ;
   
   SET @workercount=0;
   call workercount('DS',@workercount)
   
6. Write a stored procedure that takes in an IN parameter for DEPARTMENT and an OUT parameter for p_avgSalary. It should retrieve the average salary of all workers in the    
   given department and returns it in the p_avgSalary parameter and call the procedure.

   delimiter ##
   create procedure avgsalary(IN dept char(25),OUT p_avgSalary INT)
   begin
   select avg(salary) from worker where department=dept;
   end ##
   delimiter ;
   
   
   set @avgsalary=0;
   call avgsalary('DS',@avgsalary);
   
      




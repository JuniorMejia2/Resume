1.  Write a SQL command to retrieve assignment number, assignment date, employee number, employee first name, and employee last name.

      SELECT ASSIGN_NUM, ASSIGN_DATE, EMPLOYEE.EMP_NUM, EMP_FNAME, EMP_LNAME
      FROM ASSIGNMENT JON EMPLOYEE ON ASSIGNMENT.EMP_NUM=EMPLOYEE.EMP_NUM;

2.  Add database aliases to the previous command and re-run your query.

      SELECT ASSIGN_NUM, ASSIGN_DATE, E.EMP_NUM, EMP_FNAME, EMP_LNAME
      FROM ASSIGMENT AS A JOIN EMPLOYEE AS E ON A.EMP_NUM=E.EMP_NUM;

Add a where clause to search for emp_num = 117.

      SELECT ASSIGN_NUM, ASSIGN_DATE, E.EMP_NUM, EMP_FNAME, EMP_LNAME
      FROM ASSIGNMENT AS A JOIN EMLOYEE AS E ON A.EMP_NUM=E.EMP_NUM
      WHERE A.EMP_NUM = '117';

Store the above command in a stored procedure. When the stored procedure is run, the user should search for the emp_num.

      CREATE PROCEDURE EMP_NUM @NUM NVARCHAR (3)
      AS
      SELECT ASSIGN_NUM, ASSIGN_DATE, E.EMP_NUM, EMP_FNAME, EMP_LNAME
      FROM ASSIGNMENT AS A JOIN EMLOYEE AS E ON A.EMP_NUM=E.EMP_NUM
      WHERE A.EMP_NUM = @NUM;

Execute stored procedure written in problem 4 and search for emp_num = 103.

      EXEC EMP_NUM @NUM = '103';
      
Create a stored procedure called ProjValue that shows job code, job description, job charge per hour, project number, project name, and project value where proj_num is like @projnum.

      CREATE PROCEDURE PROJVALUE @PROJNUM NVARCHAR (3)
      AS
      SELECT A.JOB_CODE, A.JOB_DESCRIPTION, JOB_CHG_HOUR, P.PROJ_NUM, PROJ_NAME, PRJ_VALUE
      FROM PROJECT AS P JOIN EMPLOYEE AS E ON P.EMP_NUM=E.E,P_NUM JOIN JOB AS A ON A.JOB_CODE=E.JOB_CODE
      WHERE PROJ_NUM= @PROJNUM;

Execute your stored procedure to show the results where project number starts with the number 2.

      EXEC PROJVALUE @PROJNUM= '%2';
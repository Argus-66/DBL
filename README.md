mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| Ishan              |
| anurag             |
| information_schema |
| mysql              |
| performance_schema |
| rental_db          |
| sagar              |
| sagar1             |
| sagarassgin1       |
| southwind          |
| sys                |
+--------------------+
11 rows in set (0.00 sec)

mysql> use anurag;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+------------------+
| Tables_in_anurag |
+------------------+
| customer         |
| employee         |
| employee2        |
| location         |
| pack_grades      |
| packages         |
| sector           |
+------------------+
7 rows in set (0.01 sec)

mysql> create table borrower(rollno int unsigned not null,name varchar(30) not null,dateofissue date,nameofbook varchar(30) not null,status varchar(30) not null,primary key(rollno));
Query OK, 0 rows affected (1.65 sec)

mysql> desc borrower;
+-------------+--------------+------+-----+---------+-------+
| Field       | Type         | Null | Key | Default | Extra |
+-------------+--------------+------+-----+---------+-------+
| rollno      | int unsigned | NO   | PRI | NULL    |       |
| name        | varchar(30)  | NO   |     | NULL    |       |
| dateofissue | date         | YES  |     | NULL    |       |
| nameofbook  | varchar(30)  | NO   |     | NULL    |       |
| status      | varchar(30)  | NO   |     | NULL    |       |
+-------------+--------------+------+-----+---------+-------+
5 rows in set (0.10 sec)

mysql> create table fine(rollno int unsigned not null,Date date,amt int unsigned not null,primary key(rollno));
Query OK, 0 rows affected (0.60 sec)

mysql> desc fine;
+--------+--------------+------+-----+---------+-------+
| Field  | Type         | Null | Key | Default | Extra |
+--------+--------------+------+-----+---------+-------+
| rollno | int unsigned | NO   | PRI | NULL    |       |
| Date   | date         | YES  |     | NULL    |       |
| amt    | int unsigned | NO   |     | NULL    |       |
+--------+--------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> insert into borrower(rollno,name,dateofissue,nameofbook,status)values(1,'rahul','2024-07-11','dbms','I');
Query OK, 1 row affected (0.16 sec)

mysql> insert into borrower(rollno,name,dateofissue,nameofbook,status)values(2,'Anurag','2024-07-12','sql','I');
Query OK, 1 row affected (0.14 sec)

mysql> insert into borrower(rollno,name,dateofissue,nameofbook,status)values(3,'aditya','2024-07-13','toc','I');
Query OK, 1 row affected (0.12 sec)

mysql> insert into borrower(rollno,name,dateofissue,nameofbook,status)values(4,'tusar','2024-07-14','java','I');
Query OK, 1 row affected (0.18 sec)

mysql> insert into fine(rollno,Date,amt)values(1,'2024-07-17','100');
Query OK, 1 row affected (0.09 sec)

mysql> insert into fine(rollno,Date,amt)values(2,'2024-07-17','1000');
Query OK, 1 row affected (0.13 sec)

mysql> insert into fine(rollno,Date,amt)values(3,'2024-07-15','200');
Query OK, 1 row affected (0.10 sec)

mysql> insert into fine(rollno,Date,amt)values(4,'2024-07-20','2000');
Query OK, 1 row affected (0.11 sec)

mysql> select *from borrower;
+--------+--------+-------------+------------+--------+
| rollno | name   | dateofissue | nameofbook | status |
+--------+--------+-------------+------------+--------+
|      1 | rahul  | 2024-07-11  | dbms       | I      |
|      2 | Anurag | 2024-07-12  | sql        | I      |
|      3 | aditya | 2024-07-13  | toc        | I      |
|      4 | tusar  | 2024-07-14  | java       | I      |
+--------+--------+-------------+------------+--------+
4 rows in set (0.00 sec)

mysql> select *from fine;
+--------+------------+------+
| rollno | Date       | amt  |
+--------+------------+------+
|      1 | 2024-07-17 |  100 |
|      2 | 2024-07-17 | 1000 |
|      3 | 2024-07-15 |  200 |
|      4 | 2024-07-20 | 2000 |
+--------+------------+------+
4 rows in set (0.00 sec)

mysql> delete from fine where rollno=2,3;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ',3' at line 1
mysql> delete from fine where rollno=2;
Query OK, 1 row affected (0.09 sec)

mysql> delete from fine where rollno=3;
Query OK, 1 row affected (0.14 sec)

mysql> select *from fine;
+--------+------------+------+
| rollno | Date       | amt  |
+--------+------------+------+
|      1 | 2024-07-17 |  100 |
|      4 | 2024-07-20 | 2000 |
+--------+------------+------+
2 rows in set (0.01 sec)

mysql> delete from fine where rollno=1;
Query OK, 1 row affected (0.09 sec)

mysql> delete from fine where rollno=4;
Query OK, 1 row affected (0.15 sec)

mysql> select *from fine;
Empty set (0.00 sec)

mysql> dilimiter $
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'dilimiter $' at line 1
mysql> dilimiter $;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'dilimiter $' at line 1
mysql> create procedure calfine(rollno int(20),name varchar(50))
    -> begin
    -> declare ldate date;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 3
mysql> create procedure calfine(rollno int(20),name varchar(50)) 
    -> begin
    -> declare 1date
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 3
mysql> dilimiter $
    -> create procedure calfine(rollno int(20),name);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'dilimiter $
create procedure calfine(rollno int(20),name)' at line 1
mysql> dilimiter $ create procedure calfine(rollno int(20),name varchar(30));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'dilimiter $ create procedure calfine(rollno int(20),name varchar(30))' at line 1
mysql> dilimiter $ create procedure calfine(rollno int unsigned(20),name varchar(30));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'dilimiter $ create procedure calfine(rollno int unsigned(20),name varchar(30))' at line 1
mysql> 
mysql> begin
    -> declare ldate date;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'declare ldate date' at line 2
mysql> dilimiter $ create procedure calfine(rollno int(20),name varchar(30));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'dilimiter $ create procedure calfine(rollno int(20),name varchar(30))' at line 1
mysql> delimiter $ create procedure calfine(rollno int(20),name varchar(30));
mysql> begin
    -> declare ldate date;
    -> declare fine int(20);
    -> select dateofissue into ldate from borrower where rollno=rollno and nameofbook=name;
    -> set day=DATEDIFF(CURDATE(),ldate);
    -> if(day>=15 and day<=30) then 
    -> set fine=day*5;
    -> end IF;
    -> update borrower set status='R' where rollno=rollno and nameofbook=name;
    -> if(fine is not null)then
    -> insert into fine values(rollno,CURDATE(),fine);
    -> end IF;
    -> end $
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'declare ldate date;
declare fine int(20);
select dateofissue into ldate from bor' at line 2
mysql> begin declare ldate date; declare fine int(20);declare day int(20); select dateofissue into ldate from borrower where rollno=rollno and nameofbook=name; set day=DATEDIFF(CURDATE(),ldate); if(day>=15 and day<=30) then  set fine=day*5; end IF; update borrower set status='R' where rollno=rollno and nameofbook=name; if(fine is not null)then insert into fine values(rollno,CURDATE(),fine); end IF; end$
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'declare ldate date; declare fine int(20);declare day int(20); select dateofissue' at line 1
mysql> begin declare ldate date; declare fine int(20);declare day int(20); select dateofissue into ldate from borrower where rollno=rollno and nameofbook=name; set day=DATEDIFF(CURDATE(),ldate); IF(day>=15 and day<=30) then  set fine=day*50; end IF; update borrower set status='R' where rollno=rollno and nameofbook=name; IF(fine is not null)then insert into fine values(rollno,CURDATE(),fine); end IF; end$
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'declare ldate date; declare fine int(20);declare day int(20); select dateofissue' at line 1
mysql> mysql> show tables;
ERROR 1046 (3D000): No database selected
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| Ishan              |
| anurag             |
| information_schema |
| mysql              |
| performance_schema |
| rental_db          |
| sagar              |
| sagar1             |
| sagarassgin1       |
| southwind          |
| sys                |
+--------------------+
11 rows in set (0.03 sec)

mysql> use anurag;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+------------------+
| Tables_in_anurag |
+------------------+
| borrower         |
| customer         |
| employee         |
| employee2        |
| fine             |
| location         |
| pack_grades      |
| packages         |
| sector           |
+------------------+
9 rows in set (0.01 sec)

mysql> select *from borrower;
+--------+--------+-------------+------------+--------+
| rollno | name   | dateofissue | nameofbook | status |
+--------+--------+-------------+------------+--------+
|      1 | rahul  | 2024-07-11  | dbms       | I      |
|      2 | Anurag | 2024-07-12  | sql        | I      |
|      3 | aditya | 2024-07-13  | toc        | I      |
|      4 | tusar  | 2024-07-14  | java       | I      |
+--------+--------+-------------+------------+--------+
4 rows in set (0.02 sec)

mysql> select *from fine;
Empty set (0.04 sec)

mysql> delimiter $
mysql> create procedure calfine(rollno int(20),name varchar(50))
    -> begin
    -> declare ldate date;
    -> declare fine int(20);
    -> declare day int(20);
    -> select dateofissue into ldate from borrower where rollno=rollno and nameofbook=name;
    -> set day=DATEDIFF(CURDATE(),ldate);
    -> IF(day>=15 and day<=30) then set fine=day*5;
    -> ELSEIF(day>30) then set fine=day*50;
    -> end IF;
    -> update borrower set status='R' where rollno=rollno and nameofbook=name;
    -> IF(fine is not null) then insert into fine values(rollno,CURDATE(),fine);
    -> end IF;
    -> end $
Query OK, 0 rows affected, 3 warnings (0.19 sec)

mysql> call calfine(33,'toc')$
Query OK, 1 row affected (0.25 sec)

mysql> select *from fine$
+--------+------------+------+
| rollno | Date       | amt  |
+--------+------------+------+
|     33 | 2024-08-13 | 1550 |
+--------+------------+------+
1 row in set (0.00 sec)

mysql> call calfine(2,'sql')$
Query OK, 1 row affected (0.25 sec)

mysql> call calfine(1,'dbms')$
Query OK, 1 row affected (0.22 sec)

mysql> select *from borrower;
    -> 
    -> ;
    -> vss
    -> aadad
    -> awd
    -> ad
    -> a
    -> 
    -> 
    -> 
    -> d
    -> a
    -> d
    -> ad
    -> a
    -> wd
    -> ^C
mysql> select * from borrower;
    -> ^C
mysql> select * from borrower;
    -> ;;
    -> ^C
mysql> show tables;
    -> mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| Ishan              |
| anurag             |
| information_schema |
| mysql              |
| performance_schema |
| rental_db          |
| sagar              |
| sagar1             |
| sagarassgin1       |
| southwind          |
| sys                |
+--------------------+
11 rows in set (0.01 sec)

mysql> use anurag;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+------------------+
| Tables_in_anurag |
+------------------+
| borrower         |
| customer         |
| employee         |
| employee2        |
| fine             |
| location         |
| pack_grades      |
| packages         |
| sector           |
+------------------+
9 rows in set (0.00 sec)

mysql> select *from borrower;
+--------+--------+-------------+------------+--------+
| rollno | name   | dateofissue | nameofbook | status |
+--------+--------+-------------+------------+--------+
|      1 | rahul  | 2024-07-11  | dbms       | R      |
|      2 | Anurag | 2024-07-12  | sql        | R      |
|      3 | aditya | 2024-07-13  | toc        | R      |
|      4 | tusar  | 2024-07-14  | java       | I      |
+--------+--------+-------------+------------+--------+
4 rows in set (0.00 sec)

mysql> select *from fine;
+--------+------------+------+
| rollno | Date       | amt  |
+--------+------------+------+
|      1 | 2024-08-13 | 1650 |
|      2 | 2024-08-13 | 1600 |
|     33 | 2024-08-13 | 1550 |
+--------+------------+------+
3 rows in set (0.00 sec)

mysql> delete from fine where roll=33;
ERROR 1054 (42S22): Unknown column 'roll' in 'where clause'
mysql> delete from fine where rollno=33;
Query OK, 1 row affected (0.16 sec)

mysql> select *from fine;
+--------+------------+------+
| rollno | Date       | amt  |
+--------+------------+------+
|      1 | 2024-08-13 | 1650 |
|      2 | 2024-08-13 | 1600 |
+--------+------------+------+
2 rows in set (0.00 sec)

mysql> call calfine(3,'toc')$
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '$' at line 1
mysql> call calfine(3,'toc')$;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '$' at line 1
mysql> call calfine(3,'toc')$
    -> ^C
mysql> call calfine(3,'toc')$
    -> mysql> use anurag;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+------------------+
| Tables_in_anurag |
+------------------+
| borrower         |
| customer         |
| employee         |
| employee2        |
| fine             |
| location         |
| pack_grades      |
| packages         |
| sector           |
+------------------+
9 rows in set (0.01 sec)

mysql> select *from borrower;
+--------+--------+-------------+------------+--------+
| rollno | name   | dateofissue | nameofbook | status |
+--------+--------+-------------+------------+--------+
|      1 | rahul  | 2024-07-11  | dbms       | R      |
|      2 | Anurag | 2024-07-12  | sql        | R      |
|      3 | aditya | 2024-07-13  | toc        | R      |
|      4 | tusar  | 2024-07-14  | java       | I      |
+--------+--------+-------------+------------+--------+
4 rows in set (0.00 sec)

mysql> select *from fine;
+--------+------------+------+
| rollno | Date       | amt  |
+--------+------------+------+
|      1 | 2024-08-13 | 1650 |
|      2 | 2024-08-13 | 1600 |
+--------+------------+------+
2 rows in set (0.00 sec)

mysql> 

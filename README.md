DESIGNING A DATABASE USING ER MODELLING AND NORMALIZATION 
 
First Normal Form 
1. Create a property table with the following fields: property id, country name, padd, area, price, tax rate and having property id as the primary key. 
SQL> create table prop(propid number(2) primary key, cname varchar(20), padd varchar(50), area int,  
price number(9,2),tax_rate number(2)); 
SQL> desc prop; 
Name Null? Type 
----------------------------------------- -------- ---------------------------- 
PROPID NOT NULL NUMBER(2) 
CNAME VARCHAR2(20) 
PADD VARCHAR2(50) 
AREA NUMBER(38) 
PRICE NUMBER(9,2) 
TAX_RATE NUMBER(2) 
2. Insert values in the property table. 
SQL> insert into prop values('34','india','ganthi nagar,Coimbatore, india','500','500000','2'); 1 row created. 
SQL> insert into prop values('45','united states','first street southeast, Washington, United  states','400','2550000','5'); 1 row created. 
SQL> 	insert 	into 	prop 	values('39','scotland','capelrig 	road, 	Glasgow, scotland','600','2500000','4'); 1 row created. Before Normalization prop 
Propid Cname Padd Area Price Tax_rate 
Normalization to first normal form 
1.	Creating the prop11 tabale with propid, cname, area,price, tax_rate from prop. 
SQL> create table prop11 as select , cname, area,price, tax_rate from prop; 
2.	Creating the table prop12 with propid, sname,city,country from prop 
SQL> create table prop12 as select propid,padd from emp; 
3.	Altering the table prop11 with primary key on prop. 
SQL> alter table prop12 add constraint c1 foreign key(propid) references prop11(propid); 4. Altering the table prop12 with foreign key on propid with reference from prop11. 
SQL> alter table prop12 add constraint c1 foreign key(propid) references prop11(propid); 
After Normalization  
Prop11 
Propid Cname Area Price Tax_rate 
  
Prop12 
Propid sname City country 
SECOND NORMAL FORM 
Normalization to Second Normal Form 
1.	Create the table prop21 with propid, cname, area, price from the table prop. 
SQL> create table prop21 as select propid,cname,area, price from prop; 
2.	Create the table prop22 with cname, tax_rate from the table prop. 
SQL> create table prop22 as select cname,tax_rate from prop; 
3.	Alter table prop21 with a primary key constraint on propid. SQL> alter table prop21 add constraint prop21 primary key(propid); 4. Alter table prop22 with a primary key constraint on cname. 
SQL> alter table prop22 add constraint prop22 primary key(cname); 
5. Alter table prop21 with foreign key on cname with references on cname from prop22. 
SQL> alter table prop21 add constraint prop212 foreign key(cname) references prop22(cname); 
After normalization 
Prop21 prop22  
Propid Cname Area Price 
THIRD NORMAL FORM 
 The 2NF table is given as input here and convert it to 3NF. 
Input: prop21, prop22 tables. 
For converting to 3NF it is enough making changes in prop21 table. 
Before Normalization 
Prop21 
Propid Cname Area Price 
1.	Create table prop31 with propid, cname, area from prop21. SQL> create table prop31 as select propid,cname,area from prop21; 
2.	Create table prop32 with area, price from prop21. 
SQL> create table prop32 as select area, price from prop21; 
3.	Alter table prop31 with the constraint primary key on propid. SQL> alter table prop31 add constraint prop31 primary key(propid); 
4.	Alter table prop32 with the constraint primary key on area. 
SQL> alter table prop32 add constraint prop32 primary key(area); 
5.	Alter table prop31 with the constraint foreign key on area with refernce from area in prop32. 
SQL> alter table prop31 add constraint prop311 foreign key(area) references prop32(area); 
After Normalization 
Prop31 prop32  
Propid Cname Area 

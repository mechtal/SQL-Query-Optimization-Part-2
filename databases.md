### The first
```sql
create DATABASE HOUSE_2
go 
use HOUSE_2
go 
create table DISEASE
(disease_id int not null primary key
,name nvarchar(100))
go
create table DIAGNOSIS
(diagnosis_id int not null primary key
,disease_id int not null
,doctor_id int not null
,patient_id int not null)
go
create table DOCTOR
(doctor_id int not null primary key
,first_name nvarchar(20) not null
,last_name nvarchar(20) not null
,inn varchar(20) not null)
go
alter table DIAGNOSIS 
add constraint FK_dbo_DIAGNOSIS_disease_id foreign key (disease_id)
references DISEASE(disease_id)
go
alter table DIAGNOSIS 
add constraint FK_dbo_DIAGNOSIS_doctor_id foreign key (doctor_id)
references DOCTOR(doctor_id)
go
create nonclustered index ix_name on DOCTOR(first_name)
go 
create nonclustered index ix_inn on DOCTOR(inn)
```
### The second
```sql
create DATABASE HOUSE_3
go 
use HOUSE_3
go 
create table DISEASE
(disease_id int not null primary key
,name nvarchar(100))
go
create table DIAGNOSIS
(diagnosis_id int not null primary key
,disease_id int not null
,doctor_id int not null
,patient_id int not null)
go
create table DOCTOR
(doctor_id int not null primary key
,first_name varchar(20) not null
,last_name varchar(20) not null
,inn varchar(20) not null)
go
alter table DIAGNOSIS 
add constraint FK_dbo_DIAGNOSIS_disease_id foreign key (disease_id)
references DISEASE(disease_id)
go
alter table DIAGNOSIS 
add constraint FK_dbo_DIAGNOSIS_doctor_id foreign key (doctor_id)
references DOCTOR(doctor_id)
go
create nonclustered index ix_name on DOCTOR(first_name)
go 
create nonclustered index ix_inn on DOCTOR(inn)
```
### The third
```sql
CREATE DATABASE HOUSE_4 
COLLATE Latin1_General_100_CS_AS_SC;  
go
use HOUSE_4
go 
create table DISEASE
(disease_id int not null primary key
,name nvarchar(100))
go
create table DIAGNOSIS
(diagnosis_id int not null primary key
,disease_id int not null
,doctor_id int not null
,patient_id int not null)
go
create table DOCTOR
(doctor_id int not null primary key
,first_name varchar(20) not null
,last_name varchar(20) not null
,inn varchar(20) not null)
go
alter table DIAGNOSIS 
add constraint FK_dbo_DIAGNOSIS_disease_id foreign key (disease_id)
references DISEASE(disease_id)
go
alter table DIAGNOSIS 
add constraint FK_dbo_DIAGNOSIS_doctor_id foreign key (doctor_id)
references DOCTOR(doctor_id)
go
create nonclustered index ix_name on DOCTOR(first_name)
go 
create nonclustered index ix_inn on DOCTOR(inn)
```
### The difference
(1-2&3) first_name nvarchar(20) -> first_name varchar(20)

(1-2&3) last_name nvarchar(20) -> last_name varchar(20)

(2-3) collate https://docs.microsoft.com/en-us/sql/relational-databases/collations/set-or-change-the-database-collation?view=sql-server-ver15
```sql
select TABLE_NAME, COLUMN_NAME, COLLATION_NAME
from HOUSE_2.INFORMATION_SCHEMA.COLUMNS
where TABLE_NAME = 'DOCTOR'

select TABLE_NAME, COLUMN_NAME, COLLATION_NAME
from HOUSE_3.INFORMATION_SCHEMA.COLUMNS
where TABLE_NAME = 'DOCTOR'

select TABLE_NAME, COLUMN_NAME, COLLATION_NAME
from HOUSE_4.INFORMATION_SCHEMA.COLUMNS
where TABLE_NAME = 'DOCTOR'
```
![image](https://github.com/mechtal/part2/blob/master/collate.png?raw=true)


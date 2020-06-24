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
### The difference
first_name nvarchar(20) -> first_name varchar(20)

last_name nvarchar(20) -> last_name varchar(20)


### The query

```sql
-----------------------------------------
go
set statistics xml on
go
-----------------------------------------
select d.disease_id, d.patient_id
from DIAGNOSIS as d
where dbo.is_autoimmune_disease(d.disease_id) = 1 
-----------------------------------------
go
set statistics xml off 
go
-----------------------------------------
```
![image](https://github.com/mechtal/part2/blob/master/DIS.png?raw=true)
![image](https://github.com/mechtal/part2/blob/master/DIS_ext.png?raw=true)

### The solve

### The first
```sql
-----------------------------------------
go
set statistics xml on
go
-----------------------------------------
select d.disease_id, d.patient_id
from DIAGNOSIS as d
where d.disease_id in (10,12,13)
-----------------------------------------
go
set statistics xml off 
go
-----------------------------------------
```
![image](https://github.com/mechtal/part2/blob/master/DIS_res_1.png?raw=true)
![image](https://github.com/mechtal/part2/blob/master/DIS_res_1_ext.png?raw=true)

### The second
```sql
create function dbo.list_of_autoimmune_disease()
returns table as return
(select 10 as disease_id
union all
select 12
union all 
select 33)
```
```sql
-----------------------------------------
go
set statistics xml on
go
-----------------------------------------
select d.disease_id, d.patient_id
from DIAGNOSIS as d
where d.disease_id in (select disease_id from dbo.list_of_autoimmune_disease())
-----------------------------------------
go
set statistics xml off 
go
-----------------------------------------
```
![image](https://github.com/mechtal/part2/blob/master/DIS_res_2.png?raw=true)
![image](https://github.com/mechtal/part2/blob/master/DIS_res_2_ext.png?raw=true)

#### The third
```sql
alter table DIAGNOSIS 
add is_autoimmune_disease as
(case when disease_id in (10,12,13)
then 1 
else 0 
end)
persisted not null
```
```sql
-----------------------------------------
go
set statistics xml on
go
-----------------------------------------
select d.disease_id, d.patient_id
from DIAGNOSIS as d
where is_autoimmune_disease = 1
-----------------------------------------
go
set statistics xml off 
go
-----------------------------------------
```
![image](https://github.com/mechtal/part2/blob/master/DIS_res_3.png?raw=true)
![image](https://github.com/mechtal/part2/blob/master/DIS_res_3_ext.png?raw=true)

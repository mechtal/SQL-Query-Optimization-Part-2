### The query
```sql
-----------------------------------------
go
set statistics xml on
go
-----------------------------------------
select dct.last_name + ', ' + dct.first_name as full_name
from DOCTOR as dct
where dct.first_name = N'Gregory'
and dct.last_name = N'House'
-----------------------------------------
go
set statistics xml off 
go
-----------------------------------------
```
![image](https://github.com/mechtal/part2/blob/master/DOCT_full_name.png?raw=true)
![image](https://github.com/mechtal/part2/blob/master/DOCT_full_name_ext.png?raw=true)
```sql
alter table DOCTOR 
add full_name as last_name + ', ' + first_name
persisted not null

create nonclustered index ix_full_name 
on DOCTOR (full_name asc)
```
```sql
-----------------------------------------
go
set statistics xml on
go
-----------------------------------------
select full_name
from DOCTOR as dct
where dct.full_name = N'Gregory, House'
-----------------------------------------
go
set statistics xml off 
go
-----------------------------------------
```
![image](https://github.com/mechtal/part2/blob/master/DOCT_full_name_res.png?raw=true)
![image](https://github.com/mechtal/part2/blob/master/DOCT_full_name_res_ext.png?raw=true)

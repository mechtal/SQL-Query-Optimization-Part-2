```sql
-----------------------------------------
go
set STATISTICS xml on
go
-----------------------------------------
use HOUSE_3
go 
select d.disease_id
,d.patient_id
,dct.first_name + ', ' + dct.last_name as full_name 
from DIAGNOSIS as d 
    inner join DOCTOR as dct on dct.doctor_id = d.doctor_id
where dbo.is_autoimmune_disease(d.disease_id) = 1
and dct.first_name = N'Gregory'
and dct.last_name = N'House'
-----------------------------------------
GO
set STATISTICS xml off
go
-----------------------------------------
```

```sql
-----------------------------------------
go
set STATISTICS xml on
go
-----------------------------------------
use HOUSE_3
go 
select d.disease_id
,d.patient_id
,dct.first_name + ', ' + dct.last_name as full_name 
from DIAGNOSIS as d 
    inner join DOCTOR as dct on dct.doctor_id = d.doctor_id
where d.is_autoimmune_disease = 1
and dct.full_name = N'Gregory, House'
-----------------------------------------
GO
set STATISTICS xml off
go
-----------------------------------------
```
![image](https://github.com/mechtal/part2/blob/master/DIS_res_3.png?raw=true)
![image](https://github.com/mechtal/part2/blob/master/DIS_res_3_1.png?raw=true)
![image](https://github.com/mechtal/part2/blob/master/DIS_res_3_2.png?raw=true)

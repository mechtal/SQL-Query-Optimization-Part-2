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

### The query
```sql
-----------------------------------------
go
set statistics xml on
go
-----------------------------------------
select doctor_id, first_name
from DOCTOR
where first_name = N'Gregory'
-----------------------------------------
go
set statistics xml off 
go
-----------------------------------------
```
![image](https://github.com/mechtal/part2/blob/master/DOCT_plan.png?raw=true)

### The HOUSE_2

![image](https://github.com/mechtal/part2/blob/master/DOCT_2.png?raw=true)
![image](https://github.com/mechtal/part2/blob/master/DOCT_plan_ext_2.png?raw=true)

### The HOUSE_3

![image](https://github.com/mechtal/part2/blob/master/DOCT_3.png?raw=true)
![image](https://github.com/mechtal/part2/blob/master/DOCT_plan_ext_3.png?raw=true)

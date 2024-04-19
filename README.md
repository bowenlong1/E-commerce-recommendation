proc sql;
create table dq_sum1 as select 
move46_ct,
avg(payct/12) as last_12pay,
avg(pay) as pay_pred_14d, 
avg(payd7) as pay_actual_7d, 
avg(payd15) as pay_actual_15d,
avg(payd24) as pay_actual_24d,
avg(payd30) as pay_actual_30d,
count(*) as ct
from workable
where move46_ct>=0 and loan_age>=12
group by 1;
quit;

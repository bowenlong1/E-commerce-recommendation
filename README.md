proc sql;
create table fcall as select loan_acct_nbr, day_key, workload_dt, sum(oc_call) as oc_call
from 
ic.apr46_janapr24
ic.apr46_janapr24
group by 1,2,3;
quit;

proc sql;
create table call as select loan_acct_nbr, workload_dt, sum(oc_call) as sum_call
from call0
group by 1,2
having sum_call>0;
quit;


proc sql;
create table email as select loan_acct_nbr, datepart("Event date"n) as workload_dt format date9., count(*) as sum_email
from email0
group by 1,2;
quit;

proc sql;
create table push as select loan_acct_nbr, datepart("Event date"n) as workload_dt format date9., count(*) as sum_push
from push0
group by 1,2;
quit;

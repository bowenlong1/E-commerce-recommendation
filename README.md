proc sql;
create table dist_acct as select distinct loan_acct_nbr, contact_dt from df1;
quit;


proc sql;
create table tgt_call as select loan_acct_nbr, workload_dt, sum(oc_call) as sum_call
from call
group by 1,2
having sum_call>0;
quit;


proc sql;
create table tgt_email as select loan_acct_nbr, datepart("Event date"n) as workload_dt format date9., count(*) as sum_email
from email
group by 1,2;
quit;

proc sql;
create table tgt_push as select loan_acct_nbr, datepart("Event date"n) as workload_dt format date9., count(*) as sum_push
from push
group by 1,2;
quit;


proc sql;
create table dist_call as select a.*,
COALESCE(sum(d1.sum_call),0) as call7
from dist_acct a
left join tgt_call d1
on a.loan_acct_nbr = d1.loan_acct_nbr
and a.contact_dt+7>=d1.workload_dt>=a.contact_dt
group by a.loan_acct_nbr, a.contact_dt;

proc sql;
create table dist_email as select a.*,
COALESCE(sum(d1.sum_email),0) as email7
from dist_acct a
left join tgt_email d1
on a.loan_acct_nbr = d1.loan_acct_nbr
and a.contact_dt+7>=d1.workload_dt>=a.contact_dt
group by a.loan_acct_nbr, a.contact_dt;

proc sql;
create table dist_push as select a.*,
COALESCE(sum(d1.sum_push),0) AS push7
from dist_acct a
left join tgt_push d1
on a.loan_acct_nbr = d1.loan_acct_nbr
and a.contact_dt+7>=d1.workload_dt>=a.contact_dt
group by a.loan_acct_nbr, a.contact_dt;
quit;

proc sql;
create table dist2 as select a.*,

/*COALESCE(SUM (CASE WHEN b2.workload_dt <= a.contact_dt+7 THEN 1 ELSE 0 END),0) AS bcall7,*/
/*COALESCE(SUM (CASE WHEN c2.workload_dt <= a.contact_dt+7 THEN 1 ELSE 0 END),0) AS bemail7,*/
/*COALESCE(SUM (CASE WHEN d2.workload_dt <= a.contact_dt+7 THEN 1 ELSE 0 END),0) AS bpush7*/
count(distinct b2.workload_dt) as bcall7,
count(distinct c2.workload_dt) as bemail7,
count(distinct d2.workload_dt) as bpush7

from dist_acct a 

left join tgt_call b2
on a.loan_acct_nbr = b2.loan_acct_nbr
and a.contact_dt+7 >=b2.workload_dt>=a.contact_dt

left join tgt_email c2
on a.loan_acct_nbr = c2.loan_acct_nbr
and a.contact_dt+7 >=c2.workload_dt>=a.contact_dt

left join tgt_push d2
on a.loan_acct_nbr = d2.loan_acct_nbr
and a.contact_dt+7>=d2.workload_dt>=a.contact_dt

group by a.loan_acct_nbr, a.contact_dt;

quit;

proc sql;
create table df2 as select a.*,

b1.call7,
b2.email7,
b3.push7,
c.bcall7,
c.bemail7,
c.bpush7

from df1 a left join dist_call b1
on a.loan_acct_nbr = b1.loan_acct_nbr
and a.contact_dt = b1.contact_dt

left join dist_email b2
on a.loan_acct_nbr = b2.loan_acct_nbr
and a.contact_dt = b2.contact_dt

left join dist_push b3
on a.loan_acct_nbr = b3.loan_acct_nbr
and a.contact_dt = b3.contact_dt

left join dist2 c
on a.loan_acct_nbr = c.loan_acct_nbr
and a.contact_dt = c.contact_dt;
quit;

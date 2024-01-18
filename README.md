proc sql;
create table dist as select a.*,

COALESCE(SUM (CASE WHEN b1.workload_dt <= a.contact_dt+7 THEN b1.sum_call ELSE 0 END),0) AS call7,
COALESCE(SUM (CASE WHEN c1.workload_dt <= a.contact_dt+7 THEN c1.sum_email ELSE 0 END),0) AS email7,
COALESCE(SUM (CASE WHEN d1.workload_dt <= a.contact_dt+7 THEN d1.sum_push ELSE 0 END),0) AS push7,

COALESCE(SUM (CASE WHEN b2.workload_dt <= a.contact_dt+7 THEN 1 ELSE 0 END),0) AS bcall7,
COALESCE(SUM (CASE WHEN c2.workload_dt <= a.contact_dt+7 THEN 1 ELSE 0 END),0) AS bemail7,
COALESCE(SUM (CASE WHEN d2.workload_dt <= a.contact_dt+7 THEN 1 ELSE 0 END),0) AS bpush7

from dist_acct a 

left join tgt_call b1
on a.loan_acct_nbr = b1.loan_acct_nbr
and b1.workload_dt>=a.contact_dt

left join tgt_email c1
on a.loan_acct_nbr = c1.loan_acct_nbr
and c1.workload_dt>=a.contact_dt

left join tgt_push d1
on a.loan_acct_nbr = d1.loan_acct_nbr
and d1.workload_dt>=a.contact_dt

left join tgt_call b2
on a.loan_acct_nbr = b2.loan_acct_nbr
and b2.workload_dt>=a.contact_dt

left join tgt_email c2
on a.loan_acct_nbr = c2.loan_acct_nbr
and c2.workload_dt>=a.contact_dt

left join tgt_push d2
on a.loan_acct_nbr = d2.loan_acct_nbr
and d2.workload_dt>=a.contact_dt

group by 1,2;
quit;

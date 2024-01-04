proc sql;
create table target as select a.*,
b.day_key as day7,
b.days_delinq_qty as dpd7
from mlops_work.contact_strategy_46_60_samp3_archive a 
left join prsnt_svcng.acct_status_fact b
on a.loan_acct_nbr = b.partial_acct_nbr
and input(put(input(put(a.day_key,8.),YYMMDD8.)+7,yymmddn8.),8.) = b.day_key;
quit;

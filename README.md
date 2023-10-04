proc sql;
create table pmt_track  as select a.loan_acct_nbr, a.dt,
COALESCE(SUM (CASE WHEN b.process_dt < a.dt+1 THEN b.TOTL_TRANSACT_AMT ELSE 0 END),0) AS pm1,
COALESCE(SUM (CASE WHEN b.process_dt < a.dt+2 THEN b.TOTL_TRANSACT_AMT ELSE 0 END),0) AS pm2,
COALESCE(SUM (CASE WHEN b.process_dt < a.dt+3 THEN b.TOTL_TRANSACT_AMT ELSE 0 END),0) AS pm3
from  dist_acct a left join pmt_hist b
on a.loan_acct_nbr = b.partial_acct_nbr
and a.dt <= b.process_dt
group by 1,2;
quit;

proc sql;
create table fst_serv_wt as select a.*,
b.EFF_DT_KEY,
b.orig_total_amt
from fst_serv a 
where a.FEE_DESCR_TXT = "EXCESS WEAR&TEAR FEE"
left join s3 b
on a.PARTIAL_ACCT_NBR = b.PARTIAL_ACCT_NBR
and a.FEE_DESCR_TXT = b.FEE_DESCR_TXT
and b.eff_dt_key>=a.serv_daykey
group by a.PARTIAL_ACCT_NBR, a.EFF_DT_KEY, a.FEE_DESCR_TXT
having b.eff_dt_key = min(b.eff_dt_key);
quit;

proc sql;
create table vint_first as select cat, dpd_cat, avg(first_dt_sent-dt), mode(first_dt_sent-dt)
from vint_sum1
where first_dt_sent^=. and dpd_cat^='Others'
group by 1,2;
quit;

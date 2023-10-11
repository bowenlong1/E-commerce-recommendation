proc sql;
create table vint_first as
select cat, dpd_cat, avg(first_dt_sent - dt) as avg_diff,
    (select distinct first_dt_sent - dt
    from vint_sum1
    where first_dt_sent^=. and dpd_cat^='Others'
    group by first_dt_sent - dt
    order by count(*) desc
    having count(*) = max(count(*))
    limit 1) as mode_diff
from vint_sum1
where first_dt_sent^=. and dpd_cat^='Others'
group by cat, dpd_cat;
quit;

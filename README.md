proc sql;
create table freq_table as
select first_dt_sent - dt as diff, count(*) as freq
from vint_sum1
where first_dt_sent^=. and dpd_cat^='Others'
group by diff;

create table vint_first as
select cat, dpd_cat, avg(first_dt_sent - dt) as avg_diff,
       (select diff
        from freq_table
        order by freq desc
        limit 1
       ) as mode_diff
from vint_sum1
where first_dt_sent^=. and dpd_cat^='Others'
group by cat, dpd_cat;

drop table freq_table; /* Drop the temporary frequency table */
quit;


proc sql;
create table track2 as select 
a.acct_nbr,
a.dt15,
b1.days_past_due as dpd62,
b2.days_past_due as dpd63,
from track a 
left join dpd as b1
on a.acct_nbr = b1.acct_nbr 
and a.dt15 + 1 = b1.dt
left join dpd as b2
on a.acct_nbr = b2.acct_nbr 
and a.dt15 + 2 = b2.dt

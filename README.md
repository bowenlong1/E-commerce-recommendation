proc sql;
create table acct2 as select a.*,
b1.dpd as dpd1,
b2.dpd as dpd2
from acct a left join all_dpd b1
on a.loan_acct_nbr = b1.loan_acct_nbr
and a.dt+1 = b1.dt
left join all_dpd b2
on a.loan_acct_nbr = b2.loan_acct_nbr
and a.dt+2 = b2.dt;
quit;


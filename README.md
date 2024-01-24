proc sql;
create table acct2 as 
select a.*,
       %do i = 1 %to 120;
           b&i..dpd as dpd&i.
       %end;
from acct a
%do i = 1 %to 120;
    left join all_dpd b&i.
    on a.loan_acct_nbr = b&i..loan_acct_nbr
    and a.dt + &i. = b&i..dt
%end;
;
quit;

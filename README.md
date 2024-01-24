proc sql;
create table acct_p1 as 
select a.*,
%do i = 1 %to 20;
    b&i..dpd as dpd&i.
%end;
from acct a
%do i = 1 %to 20;
    left join all_dpd b&i.
    on a.loan_acct_nbr = b&i..loan_acct_nbr
    and a.dt + &i. = b&i..dt
%end;
;
quit;

proc sql;
create table acct_p2 as 
select a.*,
%do i = 21 %to 40;
    b&i..dpd as dpd&i.
%end;
from acct a
%do i = 21 %to 40;
    left join all_dpd b&i.
    on a.loan_acct_nbr = b&i..loan_acct_nbr
    and a.dt + &i. = b&i..dt
%end;
;
quit;

proc sql;
create table acct_p3 as 
select a.*,
%do i = 41 %to 60;
    b&i..dpd as dpd&i.
%end;
from acct a
%do i = 41 %to 60;
    left join all_dpd b&i.
    on a.loan_acct_nbr = b&i..loan_acct_nbr
    and a.dt + &i. = b&i..dt
%end;
;
quit;

proc sql;
create table acct_p4 as 
select a.*,
%do i = 61 %to 80;
    b&i..dpd as dpd&i.
%end;
from acct a
%do i = 61 %to 80;
    left join all_dpd b&i.
    on a.loan_acct_nbr = b&i..loan_acct_nbr
    and a.dt + &i. = b&i..dt
%end;
;
quit;

proc sql;
create table acct_p5 as 
select a.*,
%do i = 81 %to 100;
    b&i..dpd as dpd&i.
%end;
from acct a
%do i = 81 %to 100;
    left join all_dpd b&i.
    on a.loan_acct_nbr = b&i..loan_acct_nbr
    and a.dt + &i. = b&i..dt
%end;
;
quit;

proc sql;
create table acct_p6 as 
select a.*,
%do i = 101 %to 120;
    b&i..dpd as dpd&i.
%end;
from acct a
%do i = 101 %to 120;
    left join all_dpd b&i.
    on a.loan_acct_nbr = b&i..loan_acct_nbr
    and a.dt + &i. = b&i..dt
%end;
;
quit;



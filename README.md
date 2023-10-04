proc sort data=cred_rpt out=cred_rpt_sorted;
    by loan_acct_nbr dt_sent;
run;

data cred_rpt_sorted;
    set cred_rpt_sorted;
    by loan_acct_nbr dt_sent;
    if first.loan_acct_nbr then count=1;
    else count + 1;
run;

proc sql;
    create table combined as
    select 
        a.loan_acct_nbr, 
        a.dt as start_date,
        MIN(case when b.dt_sent between a.dt and a.dt+65 and count=1 then b.dt_sent else . end) as first_dt_sent,
        MIN(case when b.dt_sent between a.dt and a.dt+65 and count=2 then b.dt_sent else . end) as second_dt_sent,
        MIN(case when b.dt_sent between a.dt and a.dt+65 and count=3 then b.dt_sent else . end) as third_dt_sent
    from 
        dist_acct a
        left join cred_rpt_sorted b
        on a.loan_acct_nbr = b.loan_acct_nbr 
        and b.dt_sent between a.dt and a.dt+65
    group by 
        a.loan_acct_nbr, 
        a.dt
    ;
quit;

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
        CASE
            WHEN count = 1 THEN MIN(case when b.dt_sent between a.dt and a.dt+65 then b.dt_sent else . end)
            ELSE . END as first_dt_sent,
        CASE
            WHEN count = 2 THEN MIN(case when b.dt_sent between a.dt and a.dt+65 then b.dt_sent else . end)
            ELSE . END as second_dt_sent,
        CASE
            WHEN count = 3 THEN MIN(case when b.dt_sent between a.dt and a.dt+65 then b.dt_sent else . end)
            ELSE . END as third_dt_sent
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


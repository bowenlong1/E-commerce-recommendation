proc sql;
    create table first_sent as
    select a.loan_acct_nbr, a.dt, min(b.dt_sent) as first_dt_sent format=date9.
    from dist_acct a 
    left join cred_rpt b 
    on a.loan_acct_nbr = b.loan_acct_nbr 
    where b.dt_sent between a.dt and intnx('day', a.dt, 65)
    group by a.loan_acct_nbr, a.dt;
quit;


proc sql;
    create table second_sent as
    select a.loan_acct_nbr, a.dt, 
           case when a.first_dt_sent is missing then . 
                else min(b.dt_sent) end as second_dt_sent format=date9.
    from first_sent a 
    left join cred_rpt b 
    on a.loan_acct_nbr = b.loan_acct_nbr 
    where (a.first_dt_sent is missing or b.dt_sent > a.first_dt_sent) and b.dt_sent <= intnx('day', a.dt, 65)
    group by a.loan_acct_nbr, a.dt;
quit;

proc sql;
    create table third_sent as
    select a.loan_acct_nbr, a.dt, 
           case when a.first_dt_sent is missing or a.second_dt_sent is missing then . 
                else min(b.dt_sent) end as third_dt_sent format=date9.
    from second_sent a 
    left join cred_rpt b 
    on a.loan_acct_nbr = b.loan_acct_nbr 
    where (a.second_dt_sent is missing or b.dt_sent > a.second_dt_sent) and b.dt_sent <= intnx('day', a.dt, 65)
    group by a.loan_acct_nbr, a.dt;
quit;

proc sql;
    create table final_result as
    select dist_acct.*, 
           first_sent.first_dt_sent, 
           second_sent.second_dt_sent, 
           third_sent.third_dt_sent
    from dist_acct 
    left join first_sent on dist_acct.loan_acct_nbr = first_sent.loan_acct_nbr
    left join second_sent on dist_acct.loan_acct_nbr = second_sent.loan_acct_nbr
    left join third_sent on dist_acct.loan_acct_nbr = third_sent.loan_acct_nbr;
quit;

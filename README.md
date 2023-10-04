/* Step 1: Filter cred_rpt based on the dt in dist_acct */
proc sql;
    create table cred_rpt_filtered as 
    select b.loan_acct_nbr, b.dt_sent
    from dist_acct a, cred_rpt b
    where a.loan_acct_nbr = b.loan_acct_nbr
    and b.dt_sent between a.dt and intnx('day', a.dt, 65);
quit;

/* Step 2: Sort the subset by loan_acct_nbr and dt_sent */
proc sort data=cred_rpt_filtered;
    by loan_acct_nbr dt_sent;
run;

/* Step 3: Flag the first, second, and third dt_sent for each loan_acct_nbr */
data cred_rpt_flagged;
    set cred_rpt_filtered;
    by loan_acct_nbr;
    retain count;
    if first.loan_acct_nbr then count = 0;
    count + 1;
    if count = 1 then first_dt_sent = dt_sent;
    else if count = 2 then second_dt_sent = dt_sent;
    else if count = 3 then third_dt_sent = dt_sent;
    else do;
        first_dt_sent = .;
        second_dt_sent = .;
        third_dt_sent = .;
    end;
    drop count dt_sent;
run;

/* Step 4: Merge the flagged dataset with dist_acct */
proc sql;
    create table final_data as 
    select a.*, b.first_dt_sent, b.second_dt_sent, b.third_dt_sent
    from dist_acct a 
    left join cred_rpt_flagged b
    on a.loan_acct_nbr = b.loan_acct_nbr;
quit;


/* Sorting cred_rpt by loan_acct_nbr and dt_sent */
proc sort data=cred_rpt out=cred_rpt_sorted;
    by loan_acct_nbr dt_sent;
run;

/* Merge data sets */
data combined;
    merge dist_acct(in=in1) cred_rpt_sorted(in=in2);
    by loan_acct_nbr;
    if in1 and in2 and dt_sent between dt and intnx('day', dt, 65);
    retain count 0;
    count+1;
    if count = 1 then first_dt_sent = dt_sent;
    else if count = 2 then second_dt_sent = dt_sent;
    else if count = 3 then third_dt_sent = dt_sent;
    drop count;
run;

/* Drop duplicates */
proc sort data=combined out=final_data nodupkey;
    by loan_acct_nbr dt;
run;


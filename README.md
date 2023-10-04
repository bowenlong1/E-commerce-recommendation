/* Step 1: Order by loan_acct_nbr and dt_sent and assign a count */
proc sort data=cred_rpt out=cred_rpt_sorted;
    by loan_acct_nbr dt_sent;
run;

data cred_rpt_sorted;
    set cred_rpt_sorted;
    by loan_acct_nbr;
    if first.loan_acct_nbr then count=1;
    else count+1;
run;

/* Step 2: Extract the reports that fall between dt and dt+65 and limit to the first 3 reports */
data combined;
    merge dist_acct(in=in1) cred_rpt_sorted(in=in2);
    by loan_acct_nbr;
    if in1 and in2 and dt_sent between dt and dt + 65 and count <= 3;
run;

/* Step 3: Pivot the data */
proc transpose data=combined out=final prefix=dt_sent_;
    by loan_acct_nbr dt;
    var dt_sent;
    id count;
run;

data final;
    set final;
    rename dt_sent_1 = first_dt_sent dt_sent_2 = second_dt_sent dt_sent_3 = third_dt_sent;
run;

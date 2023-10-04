/* Step 2: Extract the reports that fall between dt and dt+65 and limit to the first 3 reports */
data combined;
    merge dist_acct(in=in1) cred_rpt_sorted(in=in2);
    by loan_acct_nbr;
    if in1 and in2 and dt_sent between dt and intnx('day', dt, 65) and count <= 3;
run;


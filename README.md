32         /* Merge data sets */
33         data combined;
34             merge dist_acct(in=in1) cred_rpt_sorted(in=in2);
35             by loan_acct_nbr;
2                                                          The SAS System                           14:51 Wednesday, October 4, 2023

36             if in1 and in2 and dt_sent between dt and intnx('day', dt, 65);
                                          _______
                                          388
                                          76
ERROR 388-185: Expecting an arithmetic operator.

ERROR 76-322: Syntax error, statement will be ignored.


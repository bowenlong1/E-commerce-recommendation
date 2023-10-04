28         data combined;
29             merge dist_acct(in=in1) cred_rpt_sorted(in=in2);
30             by loan_acct_nbr;
31             if in1 and in2 and dt_sent between dt and intnx('day', dt, 65) and count <= 3;
                                          _______
                                          388
                                          76
ERROR 388-185: Expecting an arithmetic operator.

ERROR 76-322: Syntax error, statement will be ignored.

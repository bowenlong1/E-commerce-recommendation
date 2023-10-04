36         (select loan_acct_nbr, dt_sent, monotonic() as rownum from cred_rpt order by loan_acct_nbr, dt_sent ) sub where rownum <=
                                                                               _____
                                                                               22
                                                                               76
36       !  3 ) b
ERROR 22-322: Syntax error, expecting one of the following: a name, (, ), ',', '.', ANSIMISS, AS, CROSS, EXCEPT, FULL, GROUP, 
              HAVING, INNER, INTERSECT, JOIN, LEFT, NATURAL, NOMISS, OUTER, RIGHT, UNION, WHERE.  

ERROR 76-322: Syntax error, statement will be ignored.

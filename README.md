   
28         proc sql;
29         create table acct2 as
30         select a.*,
31                %do i = 1 %to 120;
ERROR: The %DO statement is not valid in open code.
32                    b&i..dpd as dpd&i.
                          __
                          22
                          200
ERROR 22-322: Syntax error, expecting one of the following: a name, *.  

ERROR 200-322: The symbol is not recognized and will be ignored.

32       !            b&i..dpd as dpd&i.
                                     _
                                     22
WARNING: Apparent symbolic reference I not resolved.
WARNING: Apparent symbolic reference I not resolved.
ERROR 22-322: Syntax error, expecting one of the following: a quoted string, ',', AS, FORMAT, FROM, INFORMAT, INTO, LABEL, LEN, 
              LENGTH, TRANSCODE.  

33                %end;
ERROR: The %END statement is not valid in open code.
32                    b&i..dpd as dpd&i.
                                     _
                                     76
ERROR 76-322: Syntax error, statement will be ignored.

34         from acct a
35         %do i = 1 %to 120;
2                                                          The SAS System                          10:24 Wednesday, January 24, 2024

ERROR: The %DO statement is not valid in open code.

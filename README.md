38             count(*) / sum(count(*)) over () as percentage,
                                        ____
                                        22
ERROR 22-322: Syntax error, expecting one of the following: !, !!, &, *, **, +, ',', -, /, <, <=, <>, =, >, >=, ?, AND, BETWEEN, 
              CONTAINS, EQ, EQT, FROM, GE, GET, GT, GTT, LE, LET, LIKE, LT, LTT, NE, NET, OR, ^=, |, ||, ~=.  

39         	count(*) as ct
40         from
           ____
           78
           76
ERROR 78-322: Expecting a ','.

ERROR 76-322: Syntax error, statement will be ignored.

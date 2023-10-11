34             group by first_dt_sent - dt
35             order by count(*) desc
               _____
               22
               76
ERROR 22-322: Syntax error, expecting one of the following: !, !!, &, (, ), *, **, +, ',', -, '.', /, <, <=, <>, =, >, >=, ?, AND, 
              BETWEEN, CONTAINS, EQ, EQT, EXCEPT, GE, GET, GT, GTT, HAVING, IN, INTERSECT, IS, LE, LET, LIKE, LT, LTT, NE, NET, 
              NOT, NOTIN, OR, OUTER, UNION, ^, ^=, |, ||, ~, ~=.  

ERROR 76-322: Syntax error, statement will be ignored.

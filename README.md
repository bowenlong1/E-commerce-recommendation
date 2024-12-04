Hi Amy/Anna,
We observed some ds request holdout % differences during the 3 days, with portfolio day key 20241120 has the highest request %, 20241201 came the second, while 1119 came the third. As below.
Workload Date	Portfolio Day Key	DS Total Accounts	DS request holdout	DS request holdout %
11/19/2024	20241117	1426	844	59.2%
11/22/2024	20241120	1318	898	68.1%
12/3/2024	20241201	1433	911	63.6%

We think part of the reason for the difference is due to portfolio shift, Please see below for the portfolio distribution across the 3 days for test 1 and test 2. As we can see, our test 1, which target holdout more on good customers, and for daykey 20241120, we see the there are more good customers in this date than other two dates, contribute to higher holdouts. At the same time, our test 2, which target holdout more on bad customers, and for daykey 20241120, we see the there are more bad customers in this date than other two dates, contribute to higher holdouts. Collectively, it may explain higher DS request % in this date – 20241120 than other two dates.

Below is the recap of the two strategy proposals, so strategy proposal 1 (test 1) target more holdouts on lower days past and high likely to pay customers, which proposal 2 (test 2) is the opposite.


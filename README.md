exp_grp	pay_grp	count	avg_pay_rate	avg_calls	avg_emails	avg_pushes
0	control	high	192328	0.427442	7.279164	0.000000	0.000000
1	control	low	168082	0.123618	9.240990	0.000000	0.000000
2	control	med	168857	0.269092	8.270158	0.000000	0.000000
3	test0	high	27894	0.424787	6.900409	0.000000	0.000000
4	test0	low	25215	0.122943	8.289748	0.000000	0.000000
5	test0	med	24781	0.258424	7.775796	0.000000	0.000000
6	test1	high	28431	0.432134	5.940487	0.026802	0.087440
7	test1	low	24558	0.122933	8.251649	0.041738	0.154043
8	test1	med	24425	0.269191	7.138547	0.032057	0.101699
9	test2	high	28369	0.425958	6.537805	0.042476	0.139201
10	test2	low	25126	0.121667	7.540516	0.054764	0.195933
11	test2	med	24333	0.267004	7.236798	0.070234	0.243907


It gives me table result as above, however, I want to get a two tables formated like this, in the second table there is statistically signifcant column that compare each exp_grp with control regarding the pay_rate

	low			med			high					low			med			high		
group	avg_calls	avg_emails	avg_pushes	avg_calls	avg_emails	avg_pushes	avg_calls	avg_emails	avg_pushes		group	count	avg_pay_rate	statistically significant	count	avg_pay_rate	statistically significant	count	avg_pay_rate	statistically significant
control											control			N/A			N/A			N/A
test0											test0									
test1											test1									
test2											test2									
![image](https://github.com/bowenlong1/E-commerce-recommendation/assets/38050947/7706ea10-03bd-48f3-a8bf-de6c01387774)

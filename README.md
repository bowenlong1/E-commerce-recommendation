ACCT_NBR	loan_acct_nbr	dt	dpd	first_dt_sent	second_dt_sent	third_dt_sent	cat	first_dt=vint_dt	dpd_cat
002300010000000000000170762032	170762032	01FEB2019	1	.	.	.	Jan2019 - Dec2019	0	1DPD
002300010000000000000170762625	170762625	09FEB2019	0	.	.	.	Jan2019 - Dec2019	0	0DPD
002300010000000000000170762858	170762858	21JAN2019	1	.	.	.	Jan2019 - Dec2019	0	1DPD

I have a dataset like above, help me write a SAS code. Maybe you need generate 3 tables, for the first table, I want to for any records that first_dt_sent not missing, help me find the average days of difference between first_dt_sent and dt, and where is mode for this difference between first_dt_sent and dt. So on and so forth for second_dt_sent, third_dt_sent. It would be even great you can just generate one table with all those information.

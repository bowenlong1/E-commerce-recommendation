df_notax[['dpd', 'dsf', 'days_since_last_rpt', 'precsn_score', 'past_due_amt', 'pay', 'pay_grp']]

for this data, create bar plots for ‘pay’ (propensity to pay) by ‘dpd’ (days past due), dsf (days since finalization), 'days_since_last_rpt' (days since last credit reporting), 'precsn_score' (fico), past_due_amt (past due amount).

•	Note that, 
•	for dpd, breakdown by ‘1-30 DPD’, 31-60 DPD’, ’61-90 DPD’ first and then create the bar plot
•	For dsf, by ‘21-30 DSF’, ‘31-60 DSF’, ‘61-90 DSF’, ‘91+ DSF’ first
•	For 'days_since_last_rpt', by ‘1 Week’ (<=7), ‘2 Weeks’ (>7, <=14), ‘3 Weeks’ (>14, <=21), ‘1 Month’ (>21, <=30), ‘1 Month+’ (>30)
•	For 'precsn_score', by ‘Poor <=579 ’, ‘Fair 580-669’, ‘Good 670-739’, ‘Very Good 740-799’, ‘Exceptional >=800’
•	For 'past_due_amt', by ‘<=$500’, ‘$500-$1000’, ‘$1000-$2000’, ‘$2000+’

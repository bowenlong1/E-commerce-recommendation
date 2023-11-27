Currently, for 1-90DPD EOT accounts, dialer and manual call strategy are separate, 
•	For dialer calls, 1-14DPD accounts are not called on dialer, 15-60DPD accounts are holdout one day after every two days of call (e,g 15-16DPD called, 17dpd holout, 18-19dpd called, 20dpd holdout etc), 61-80dpd accounts are called everyday, 81-90 accounts are called on selected dpd (83, 85, 86, 88, 90dpd)
•	for manual calls there is no holdout strategy/schedule, except the accounts made promise and/or with courtesy hold
Servicing will move manual calls to dialer, also, with market back to normal , we expect less people will choose buyout at the end of lease term so we expect to see increase of EOT workload. So to further reduce workload, Data science designs a alternative 1-90DPD contact strategy based on account’s payment propensity, deficiency balance and days to past due that integrates dialer and manual calls
Data science splits the 1-90DPD EOT portfolio to property tax only and non-property tax only accounts and develops separate strategies
For non-property tax only, data science develops a machine learning model to predict account’s payment propensity and develops the contact strategy based on model results and account’s diffencicy balance leveraging call, email and push channels

For property tax only accounts, we expect the % of this portfolio will naturally reduce with market back to normal, data science primarily focus on develop a email contact strategy to improve the cure rate of this group of customer


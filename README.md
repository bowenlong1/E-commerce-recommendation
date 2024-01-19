import pandas as pd

# Assuming your DataFrame is named dist_acct
# If not, replace dist_acct with your DataFrame's actual name

# Group by 'exp_grp' and 'pay_grp' and calculate counts and averages
grouped_df = dist_acct.groupby(['exp_grp', 'pay_grp']).agg(
    count=('loan_acct_nbr', 'count'),
    avg_pay_rate=('pay_res', 'mean'),
    avg_calls=('sum_call', 'mean'),
    avg_emails=('sum_email', 'mean'),
    avg_pushes=('sum_push', 'mean')
).reset_index()

# Display the result
print(grouped_df)

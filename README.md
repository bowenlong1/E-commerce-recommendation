import pandas as pd

# Assuming 'dist_acct' is your DataFrame
dist_acct['contact_dt'] = pd.to_datetime(dist_acct['contact_dt'])

# Assuming 'call' is your DataFrame
call['workload_dt'] = pd.to_datetime(call['workload_dt'])

# Merging the DataFrames
merged_df = dist_acct.merge(call, how='left', left_on=['loan_acct_nbr'], right_on=['loan_acct_nbr'])

# Filtering and performing the calculation
dist_acct['call7'] = (
    merged_df.query('workload_dt >= contact_dt and workload_dt <= contact_dt + pd.Timedelta(days=7)')
    .groupby(['loan_acct_nbr', 'contact_dt'])['sum_call']
    .sum()
    .fillna(0)
    .astype(int)
)


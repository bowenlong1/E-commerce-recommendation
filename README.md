import pandas as pd

# Assuming merged_df is your DataFrame
merged_df['workload_dt'] = pd.to_datetime(merged_df['workload_dt'])
merged_df['contact_dt'] = pd.to_datetime(merged_df['contact_dt'])

result_df = (
    merged_df.query('workload_dt >= contact_dt and workload_dt <= contact_dt + Timedelta("7 days")')
    .groupby(['loan_acct_nbr', 'contact_dt'])
    .agg(sum_call=('sum_call', 'sum'))
    .reset_index()
)


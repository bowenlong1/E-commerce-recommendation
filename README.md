dist_acct['call7'] = (
    merged_df.query('workload_dt >= contact_dt and workload_dt <= contact_dt + pd.Timedelta("7 days")')
    .groupby(['loan_acct_nbr', 'contact_dt'])['sum_call']
    .sum()
    .fillna(0)
    .astype(int)
)


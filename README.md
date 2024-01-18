merged_df['contact_dt_plus_7'] = merged_df['contact_dt'] + pd.Timedelta("7 days")

result_df = (
    merged_df.query('workload_dt >= contact_dt and workload_dt <= contact_dt_plus_7')
    .groupby(['loan_acct_nbr', 'contact_dt'])
    .agg(sum_call=('sum_call', 'sum'))
    .reset_index()
)


# Convert 'contact_dt' column to datetime
dist_acct['contact_dt'] = pd.to_datetime(dist_acct['contact_dt'])
call_df['contact_dt'] = pd.to_datetime(call_df['contact_dt'])
email_df['contact_dt'] = pd.to_datetime(email_df['contact_dt'])
push_df['contact_dt'] = pd.to_datetime(push_df['contact_dt'])

# Merge dist_acct with call_df, email_df, and push_df
dist_acct = dist_acct.merge(call_df, how='left', on=['loan_acct_nbr', 'contact_dt'])
dist_acct = dist_acct.merge(email_df, how='left', on=['loan_acct_nbr', 'contact_dt'])
dist_acct = dist_acct.merge(push_df, how='left', on=['loan_acct_nbr', 'contact_dt'])

# Fill NaN values with 0 for columns sum_call, sum_email, sum_push
dist_acct[['sum_call', 'sum_email', 'sum_push']] = dist_acct[['sum_call', 'sum_email', 'sum_push']].fillna(0)

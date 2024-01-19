# Merge dist_acct with call_df, email_df, and push_df
dist_acct = dist_acct.merge(call_df, how='left', on=['loan_acct_nbr', 'contact_dt'])
dist_acct = dist_acct.merge(email_df, how='left', on=['loan_acct_nbr', 'contact_dt'])
dist_acct = dist_acct.merge(push_df, how='left', on=['loan_acct_nbr', 'contact_dt'])

# Fill NaN values with 0 for columns sum_call, sum_email, sum_push
dist_acct[['sum_call', 'sum_email', 'sum_push']] = dist_acct[['sum_call', 'sum_email', 'sum_push']].fillna(0)

# If you want to drop temporary columns like contact_dt_plus_7, you can do so
# dist_acct.drop(columns=['contact_dt_plus_7'], inplace=True)


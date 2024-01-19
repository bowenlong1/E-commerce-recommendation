1234567
# Merge dist_acct with call_df, email_df, and push_df
dist_acct = dist_acct.merge(call_df, how='left', on=['loan_acct_nbr', 'contact_dt'])
dist_acct = dist_acct.merge(email_df, how='left', on=['loan_acct_nbr', 'contact_dt'])
dist_acct = dist_acct.merge(push_df, how='left', on=['loan_acct_nbr', 'contact_dt'])

# Fill NaN values with 0 for columns sum_call, sum_email, sum_push
dist_acct[['sum_call', 'sum_email', 'sum_push']] = dist_acct[['sum_call', 'sum_email', 'sum_push']].fillna(0)
ValueError: You are trying to merge on object and datetime64[ns] columns. If you wish to proceed you should use pd.concat
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
File <command-501241298327021>, line 2
      1 # Merge dist_acct with call_df, email_df, and push_df
----> 2 dist_acct = dist_acct.merge(call_df, how='left', on=['loan_acct_nbr', 'contact_dt'])
      3 dist_acct = dist_acct.merge(email_df, how='left', on=['loan_acct_nbr', 'contact_dt'])
      4 dist_acct = dist_acct.merge(push_df, how='left', on=['loan_acct_nbr', 'contact_dt'])

File /databricks/python/lib/python3.10/site-packages/pandas/core/frame.py:9354, in DataFrame.merge(self, right, how, on, left_on, right_on, left_index, right_index, sort, suffixes, copy, indicator, validate)
   9335 @Substitution("")
   9336 @Appender(_merge_doc, indents=2)
   9337 def merge(
   (...)
   9350     validate: str | None = None,
   9351 ) -> DataFrame:
   9352     from pandas.core.reshape.merge import merge
-> 9354     return merge(
   9355         self,
   9356         right,

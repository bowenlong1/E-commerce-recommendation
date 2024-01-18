import pandas as pd

# Assuming email is your DataFrame for emails
email['workload_dt'] = pd.to_datetime(email['workload_dt'])
dist_acct['contact_dt'] = pd.to_datetime(dist_acct['contact_dt'])

# Merge dist_acct with email
merged_email_df = dist_acct.merge(email, how='left', left_on=['loan_acct_nbr'], right_on=['loan_acct_nbr'])

# Create a column for contact_dt + 7
merged_email_df['contact_dt_plus_7'] = merged_email_df['contact_dt'] + pd.Timedelta("7 days")

# Filter based on the condition and perform aggregation
email_df = (
    merged_email_df.query('workload_dt >= contact_dt and workload_dt <= contact_dt_plus_7')
    .groupby(['loan_acct_nbr', 'contact_dt'])
    .agg(sum_email=('sum_email', 'sum'))
    .reset_index()
)

# Drop the temporary column if you don't need it in the final result
email_df.drop(columns=['contact_dt_plus_7'], inplace=True)

import pandas as pd

# Assuming push is your DataFrame for push notifications
push['workload_dt'] = pd.to_datetime(push['workload_dt'])
dist_acct['contact_dt'] = pd.to_datetime(dist_acct['contact_dt'])

# Merge dist_acct with push
merged_push_df = dist_acct.merge(push, how='left', left_on=['loan_acct_nbr'], right_on=['loan_acct_nbr'])

# Create a column for contact_dt + 7
merged_push_df['contact_dt_plus_7'] = merged_push_df['contact_dt'] + pd.Timedelta("7 days")

# Filter based on the condition and perform aggregation
push_df = (
    merged_push_df.query('workload_dt >= contact_dt and workload_dt <= contact_dt_plus_7')
    .groupby(['loan_acct_nbr', 'contact_dt'])
    .agg(sum_push=('sum_push', 'sum'))
    .reset_index()
)

# Drop the temporary column if you don't need it in the final result
push_df.drop(columns=['contact_dt_plus_7'], inplace=True)


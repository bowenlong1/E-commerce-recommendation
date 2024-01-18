import pandas as pd

# Assuming df is your DataFrame
df['day_key'] = df['day_key'].astype(str)  # Convert to string for formatting
df['dt'] = pd.to_datetime(df['day_key'], format='%Y%m%d')
df['real_dt'] = df['dt'] + pd.DateOffset(days=1)
df['contact_dt'] = df['real_dt'] + pd.DateOffset(days=1)
df['contact_dt'] = df['contact_dt'].dt.strftime('%Y-%m-%d')  # Format as 'YYYY-MM-DD'

# Now df contains the new columns 'dt', 'real_dt', and 'contact_dt'

import pandas as pd

# Assuming you already have DataFrame 'df1', 'call', 'email', 'push'
# ...

# Create DataFrame 'dist_acct'
dist_acct = df1[['loan_acct_nbr', 'contact_dt']].drop_duplicates()

# Calculate 'call7' in 'dist_acct'
dist_acct['call7'] = (
    df1.merge(call, how='left', left_on=['loan_acct_nbr'], right_on=['loan_acct_nbr'])
    .query('workload_dt >= contact_dt and workload_dt <= contact_dt + 7')
    .groupby(['loan_acct_nbr', 'contact_dt'])['oc_call']
    .sum()
    .fillna(0)
    .astype(int)
)

# Calculate 'email7' in 'dist_acct'
dist_acct['email7'] = (
    df1.merge(email, how='left', left_on=['loan_acct_nbr'], right_on=['loan_acct_nbr'])
    .query('workload_dt >= contact_dt and workload_dt <= contact_dt + 7')
    .groupby(['loan_acct_nbr', 'contact_dt'])['sum_email']
    .sum()
    .fillna(0)
    .astype(int)
)

# Calculate 'push7' in 'dist_acct'
dist_acct['push7'] = (
    df1.merge(push, how='left', left_on=['loan_acct_nbr'], right_on=['loan_acct_nbr'])
    .query('workload_dt >= contact_dt and workload_dt <= contact_dt + 7')
    .groupby(['loan_acct_nbr', 'contact_dt'])['sum_push']
    .sum()
    .fillna(0)
    .astype(int)
)

# Calculate 'bcall7', 'bemail7', 'bpush7' in 'dist_acct'
dist_acct['bcall7'] = (
    df1.merge(call, how='left', left_on=['loan_acct_nbr'], right_on=['loan_acct_nbr'])
    .query('workload_dt >= contact_dt and workload_dt <= contact_dt + 7')
    .groupby(['loan_acct_nbr', 'contact_dt'])
    .size()
    .fillna(0)
    .astype(int)
)

dist_acct['bemail7'] = (
    df1.merge(email, how='left', left_on=['loan_acct_nbr'], right_on=['loan_acct_nbr'])
    .query('workload_dt >= contact_dt and workload_dt <= contact_dt + 7')
    .groupby(['loan_acct_nbr', 'contact_dt'])
    .size()
    .fillna(0)
    .astype(int)
)

dist_acct['bpush7'] = (
    df1.merge(push, how='left', left_on=['loan_acct_nbr'], right_on=['loan_acct_nbr'])
    .query('workload_dt >= contact_dt and workload_dt <= contact_dt + 7')
    .groupby(['loan_acct_nbr', 'contact_dt'])
    .size()
    .fillna(0)
    .astype(int)
)
![Uploading image.png…]()


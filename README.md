import pandas as pd

# Assuming 'call0', 'email0', and 'push0' are your DataFrames

# Create 'call' DataFrame
call = call0.groupby(['loan_acct_nbr', 'workload_dt']).agg(sum_call=('oc_call', 'sum')).reset_index()
call = call[call['sum_call'] > 0]

# Create 'email' DataFrame
email = email0.groupby(['loan_acct_nbr', 'Event date']).size().reset_index(name='sum_email')
email['workload_dt'] = pd.to_datetime(email['Event date']).dt.strftime('%Y-%m-%d')

# Create 'push' DataFrame
push = push0.groupby(['loan_acct_nbr', 'Event date']).size().reset_index(name='sum_push')
push['workload_dt'] = pd.to_datetime(push['Event date']).dt.strftime('%Y-%m-%d')

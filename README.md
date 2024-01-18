import pandas as pd

# Assuming 'call0' is your DataFrame and 'workload_dt' is the column
call0['workload_dt'] = pd.to_datetime(call0['workload_dt'], format='%d%b%Y').dt.strftime('%Y-%m-%d')

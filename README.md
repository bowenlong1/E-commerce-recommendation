import pandas as pd

# Assuming 'email0' DataFrame
email0['workload_dt'] = pd.to_datetime(email0['Event date'], format='%d%b%y:%H:%M:%S')

# Now, if you want to format it as 'YYYY-MM-DD', you can use the following line:
email0['workload_dt'] = email0['workload_dt'].dt.strftime('%Y-%m-%d')

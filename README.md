import pandas as pd

# Sample DataFrame
data = {'tgt_dt': ['15DEC2023', '20JAN2024', '10FEB2025']}
df = pd.DataFrame(data)

# Convert 'tgt_dt' column to datetime object
df['tgt_dt'] = pd.to_datetime(df['tgt_dt'], format='%d%b%Y')

# Convert 'tgt_dt' to 'tgt_daykey' with the desired format
df['tgt_daykey'] = df['tgt_dt'].dt.strftime('%Y%m%d')

print(df)


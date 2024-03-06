import pandas as pd

# Assuming you have a DataFrame named df containing your data
df['tgt_dt'] = pd.to_datetime(df['dt'], format='%d%b%Y')  # Convert 'dt' column to datetime

dpd_threshold = 46
for i in range(47, 60):
    condition = df[f'dpd{i}'] <= dpd_threshold
    df.loc[condition, 'tgt_dt'] = df.loc[condition, 'tgt_dt'] + pd.DateOffset(days=i-46)

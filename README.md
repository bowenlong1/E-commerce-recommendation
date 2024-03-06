import pandas as pd

# Assuming you have a DataFrame named df containing your data
df['tgt_dt'] = pd.to_datetime(df['dt'], format='%d%b%Y')  # Convert 'dt' column to datetime

dpd_threshold = 46
for i in range(47, 61):
    condition = df[f'dpd{i}'] <= dpd_threshold
    df.loc[condition, 'tgt_dt'] = df.loc[condition, 'tgt_dt'] + pd.DateOffset(days=i-46)

# If 'dt' column is no longer needed, you can drop it using:
# df.drop(columns=['dt'], inplace=True)


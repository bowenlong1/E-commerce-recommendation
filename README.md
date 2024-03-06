import pandas as pd

# Assuming you have a DataFrame named df containing your data
df['tgt_dt'] = pd.to_datetime(df['dt'], format='%d%b%Y')  # Convert 'dt' column to datetime

dpd_threshold = 46
for index, row in df.iterrows():
    for i in range(47, 61):
        if row[f'dpd{i}'] <= dpd_threshold:
            df.at[index, 'tgt_dt'] = row['tgt_dt'] + pd.DateOffset(days=i-46)
            break  # Break out of the inner loop once condition is met

# If 'dt' column is no longer needed, you can drop it using:
# df.drop(columns=['dt'], inplace=True)


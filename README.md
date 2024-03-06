import pandas as pd

# Assuming you have a DataFrame named vint containing your data
vint['tgt_dt'] = pd.to_datetime(vint['dt'], format='%d%b%Y')  # Convert 'dt' column to datetime

dpd_threshold = 46

for index, row in vint.iterrows():
    for i in range(46, 61):
        column_name = f'dpd{i}'
        if row[column_name] <= dpd_threshold:
            vint.at[index, 'tgt_dt'] = row['dt'] + pd.DateOffset(days=i-46)
            break  # Stop iterating through columns once the first drop is found

# If no drop is found, set 'tgt_dt' to dt + 15
if pd.isnull(vint['tgt_dt']).all():
    vint['tgt_dt'] = vint['dt'] + pd.DateOffset(days=15)

# If 'dt' column is no longer needed, you can drop it using:
# vint.drop(columns=['dt'], inplace=True)



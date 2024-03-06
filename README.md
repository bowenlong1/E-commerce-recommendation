import pandas as pd

# Assuming you have a DataFrame named vint containing your data
vint['dt'] = pd.to_datetime(vint['dt'], format='%d%b%Y')  # Convert 'dt' column to datetime

dpd_threshold = 46

# Define a function to find the first drop below the threshold
def find_first_drop(row):
    for i in range(46, 61):
        column_name = f'dpd{i}'
        if row[column_name] <= dpd_threshold:
            return row['dt'] + pd.DateOffset(days=i-46)
    return row['dt'] + pd.DateOffset(days=15)  # Default value if no drop is found

# Apply the function to each row using lambda
vint['tgt_dt'] = vint.apply(lambda row: find_first_drop(row), axis=1)

# If 'dt' column is no longer needed, you can drop it using:
# vint.drop(columns=['dt'], inplace=True)

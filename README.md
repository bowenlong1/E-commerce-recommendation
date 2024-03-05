# Original DataFrame
original_columns = ['acct_nbr', 'day_nxt', 'equity', 'equ_grp', 'pay', 'pay_grp']

# Renamed columns with "_end" suffix
new_columns = [col + '_end' for col in original_columns]

# Rename columns in the DataFrame
df.rename(columns=dict(zip(original_columns, new_columns)), inplace=True)

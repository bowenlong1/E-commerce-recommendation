uppercase_columns = ['FINC_AMT', 'CUR_APR', 'PMT_AMT', 'CREDIT_TIER', 'CUSTOMER_STATE', 
                     'PAST_DUE_AMT', 'LAST_PMT_AMT', 'SINCE_LAST_PMT_DAY_QTY', 'ACCT_PAYOFF_AMT', 
                     'ROLL_121_MIN_DELINQ_DAY_QTY']

# Map for renaming: current lowercase names to new uppercase names
rename_map = {col.lower(): col for col in uppercase_columns}

# Rename the columns using the rename function
df = df.rename(columns=rename_map)

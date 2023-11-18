correct_types = {
    'FINC_AMT': 'float64',
    'CUR_APR': 'float64',
    'PMT_AMT': 'float64',
    'pti': 'float64',
    'CREDIT_TIER': 'object',
    'CUSTOMER_STATE': 'object',
    'loan_age': 'int64',
    # ... (include all other columns with their respective types)
    'days_since_last_plan': 'float64',
    'wav_amt': 'float64'
}

# Filter the correct_types dictionary to only include keys that are actually columns in the DataFrame
correct_types = {col: dtype for col, dtype in correct_types.items() if col in df.columns}

# Apply the type conversion to the DataFrame
df = df.astype(correct_types)

# Check the new data types to confirm the changes
df.dtypes

import pandas as pd

# Sample dataframe
data = {'account_number': ['1234567890123456', '7890123456789012']}
df = pd.DataFrame(data)

# Convert the specified substring of account_number to a number
df['new_account_number'] = df['account_number'].apply(lambda x: int(x[-12:]))

print(df)

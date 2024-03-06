# First, calculate the value counts for the specified columns
counts = vint2[['equ_grp', 'equ_grp_end']].value_counts().reset_index()
counts.columns = ['equ_grp', 'equ_grp_end', 'count']

# Calculate the total count for normalization
total_count = counts['count'].sum()

# Calculate percentages
counts['percentage'] = (counts['count'] / total_count) * 100

# Add 'match' column
counts['match'] = np.where(counts['equ_grp'] == counts['equ_grp_end'], 'Yes', 'No')

# Convert the counts DataFrame to ensure 'count' and 'percentage' columns are numeric
counts['count'] = counts['count'].astype(int)

# Display the modified DataFrame
print(counts)


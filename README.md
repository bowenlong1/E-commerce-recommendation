from scipy.stats import ttest_ind

# Convert the DataFrame to numeric to ensure calculations
grouped_data[['move61_percent', 'move91_percent']] = grouped_data[['move61_percent', 'move91_percent']].apply(pd.to_numeric)

# Separate the control group from the test groups
control_group = grouped_data[grouped_data['exp_grp'] == 'control']
test_groups = grouped_data[grouped_data['exp_grp'] != 'control']

# Perform t-tests for move61_percent and move91_percent for each test group against the control group
ttest_results = {}

for group_name, group_data in test_groups.groupby('exp_grp'):
    ttest_results[group_name] = {}
    for col in ['move61_percent', 'move91_percent']:
        t_stat, p_value = ttest_ind(control_group[col], group_data[col])
        ttest_results[group_name][col] = {'t-statistic': t_stat, 'p-value': p_value}

# Display the results
for group_name, result in ttest_results.items():
    print(f"\nComparison of {group_name} group with control group:")
    for col, stats in result.items():
        print(f"{col}: t-statistic = {stats['t-statistic']}, p-value = {stats['p-value']}")

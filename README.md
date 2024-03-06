from scipy.stats import chi2_contingency

# Calculate proportion differences for each test group compared to the control group
proportion_diff = {}

# Iterate over each test group
for group_name, test_group in grouped_data.groupby('exp_grp'):
    if group_name != 'control':
        proportion_diff[group_name] = {}
        # Merge the control group and the current test group based on 'equ_pay_grp_vint'
        merged_group = pd.merge(control_group, test_group, on='equ_pay_grp_vint', suffixes=('_control', '_test'))
        # Calculate percentage differences
        merged_group['move61_diff'] = merged_group['move61_percent_test'] - merged_group['move61_percent_control']
        merged_group['move91_diff'] = merged_group['move91_percent_test'] - merged_group['move91_percent_control']
        proportion_diff[group_name] = merged_group

# Perform chi-square tests for proportion differences
chi2_results = {}

for group_name, test_data in proportion_diff.items():
    chi2_results[group_name] = {}
    for col in ['move61_diff', 'move91_diff']:
        # Create a contingency table for chi-square test
        contingency_table = pd.crosstab(test_data['equ_pay_grp_vint'], test_data[col], margins=True)
        # Perform chi-square test
        chi2_stat, p_value, _, _ = chi2_contingency(contingency_table)
        # Store the chi-square test results
        chi2_results[group_name][col] = {'chi2_stat': chi2_stat, 'p-value': p_value}

# Display the results
for group_name, result in chi2_results.items():
    print(f"\nComparison of {group_name} group with control group:")
    for col, stats in result.items():
        print(f"{col}: chi-square statistic = {stats['chi2_stat']}, p-value = {stats['p-value']}")

from scipy.stats import chi2_contingency

# Separate the control group from the test groups
control_group = grouped_data[grouped_data['exp_grp'] == 'control']
test_groups = grouped_data[grouped_data['exp_grp'] != 'control']

# Create a dictionary to store chi-square test results
chi2_results = {}

# Iterate over each test group
for group_name, test_group in test_groups.groupby('exp_grp'):
    chi2_results[group_name] = {}
    for col in ['move61_percent', 'move91_percent']:
        # Create a contingency table for chi-square test
        contingency_table = pd.crosstab(control_group['equ_pay_grp_vint'], control_group[col], margins=True)
        
        # Perform chi-square test
        chi2_stat, p_value, _, _ = chi2_contingency(contingency_table)
        
        # Store the chi-square test results
        chi2_results[group_name][col] = {'chi2_stat': chi2_stat, 'p-value': p_value}

# Display the results
for group_name, result in chi2_results.items():
    print(f"\nComparison of {group_name} group with control group:")
    for col, stats in result.items():
        print(f"{col}: chi-square statistic = {stats['chi2_stat']}, p-value = {stats['p-value']}")

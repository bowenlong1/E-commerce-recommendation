from scipy.stats import chi2_contingency

# Filter out the control group from the grouped data
control_group = grouped_data[grouped_data['exp_grp'] == 'control']

# Store chi-square test results
chi2_results = {}

# Iterate over each 'equ_pay_grp_vint' group
for group_name, group_data in grouped_data.groupby('equ_pay_grp_vint'):
    # Create a dictionary to store chi-square test results for the current group
    chi2_results[group_name] = {}
    
    # Create a contingency table for the current 'equ_pay_grp_vint' group
    contingency_table = pd.DataFrame({
        'control_acct_nbr': control_group[control_group['equ_pay_grp_vint'] == group_name]['acct_nbr'],
        'control_move61': control_group[control_group['equ_pay_grp_vint'] == group_name]['move61'],
        'control_move91': control_group[control_group['equ_pay_grp_vint'] == group_name]['move91']
    })
    
    # Iterate over each test group
    for test_group_name in ['test0', 'test1', 'test2']:
        # Extract data for the current test group and the current 'equ_pay_grp_vint' group
        test_group = grouped_data[(grouped_data['exp_grp'] == test_group_name) & (grouped_data['equ_pay_grp_vint'] == group_name)]
        
        # Create the contingency table for the current test group and 'equ_pay_grp_vint' group
        contingency_table[f'{test_group_name}_acct_nbr'] = test_group['acct_nbr']
        contingency_table[f'{test_group_name}_move61'] = test_group['move61']
        contingency_table[f'{test_group_name}_move91'] = test_group['move91']
    
    # Perform chi-square tests for the proportion differences between the control and each test group
    for col in ['move61', 'move91']:
        chi2_stat, p_value, _, _ = chi2_contingency(contingency_table[[f'control_{col}', 'test0_{col}', 'test1_{col}', 'test2_{col}']])
        chi2_results[group_name][col] = {'chi2_stat': chi2_stat, 'p-value': p_value}

# Display the chi-square test results
for group_name, result in chi2_results.items():
    print(f"\nComparison for {group_name}:")
    for col, stats in result.items():
        print(f"{col}: chi-square statistic = {stats['chi2_stat']}, p-value = {stats['p-value']}")

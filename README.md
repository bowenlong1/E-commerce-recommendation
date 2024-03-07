
from scipy.stats import chi2_contingency

# Create a dictionary to store p-values
p_values = {}

# Loop through each test group and perform chi-squared test against control group
for test_group in ['test0', 'test1', 'test2']:
    control_counts = grouped_data[grouped_data['exp_grp'] == 'control']['move61']
    test_group_counts = grouped_data[grouped_data['exp_grp'] == test_group]['move61']
    
    # Create a contingency table
    contingency_table = [[control_counts.sum(), test_group_counts.sum()],
                         [grouped_data['acct_nbr'].sum() - control_counts.sum(), 
                          grouped_data['acct_nbr'].sum() - test_group_counts.sum()]]
    
    # Perform chi-squared test
    _, p_val, _, _ = chi2_contingency(contingency_table)
    
    p_values[test_group] = p_val

# Print p-values
print("P-values for difference in 'move61' between each test group and control group:")
for test_group, p_val in p_values.items():
    print(f"{test_group}: {p_val}")

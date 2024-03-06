import pandas as pd
import numpy as np
from scipy.stats import ttest_ind

# Assuming you have a DataFrame named vint2 containing your data

# Step 1: Group by 'exp_grp' and 'equ_pay_grp_vint', and aggregate
grouped_data = vint2.groupby(['exp_grp', 'equ_pay_grp_vint']).agg({'acct_nbr': 'count', 'move61': 'sum', 'move91': 'sum'})

# Step 2: Calculate the percentage of move61 and move91 for each row
grouped_data['move61_percent'] = grouped_data['move61'] / grouped_data['move61'].sum() * 100
grouped_data['move91_percent'] = grouped_data['move91'] / grouped_data['move91'].sum() * 100

# Step 3: Compare the differences in move61 and move91 between test groups and control group
control_group = grouped_data.loc['control']
test_groups = grouped_data.loc[['test0', 'test1', 'test2']]

# Calculate the difference between test groups and control group
test_groups['move61_diff'] = test_groups['move61'] - control_group['move61']
test_groups['move91_diff'] = test_groups['move91'] - control_group['move91']

# Perform t-test for move61 and move91 differences between test and control groups
ttest_results = {}
for col in ['move61_diff', 'move91_diff']:
    ttest_results[col] = ttest_ind(control_group[col], test_groups[col])

# Display the results as a DataFrame
results_df = pd.DataFrame(ttest_results, index=['t-statistic', 'p-value'])

# Display the grouped data and the statistical test results
print("Grouped Data:")
print(grouped_data)
print("\nStatistical Test Results:")
print(results_df)


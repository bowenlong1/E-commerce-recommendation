import pandas as pd
from statsmodels.stats.proportion import proportions_ztest

# Assuming your grouped DataFrame is named grouped_df
# If not, replace grouped_df with your DataFrame's actual name

# Define the order for pay_grp
pay_grp_order = ['high', 'med', 'low']

# Pivot table for averages
avg_table = pd.pivot_table(grouped_df, index=['exp_grp'], columns=['pay_grp'], values=['avg_calls', 'avg_emails', 'avg_pushes'], aggfunc='mean')
avg_table = avg_table.reorder_levels([1, 0], axis=1).sort_index(axis=1, level=0)
avg_table = avg_table[['avg_calls', 'avg_emails', 'avg_pushes']]  # Move averages to the top

# Create a new DataFrame for statistical significance
significance_df = pd.DataFrame(columns=['group', 'pay_grp', 'count', 'avg_pay_rate', 'statistically_significant'])

# Define the control group
control_row = grouped_df[grouped_df['exp_grp'] == 'control']

# Compare each exp_grp with control regarding the pay_rate and each pay_grp
for exp_grp in grouped_df['exp_grp'].unique():
    exp_grp_row = grouped_df[grouped_df['exp_grp'] == exp_grp]

    # Perform two-proportion z-test for pay_rate
    count = [control_row['count'].values[0], exp_grp_row['count'].values[0]]
    success = [control_row['count'].values[0] * control_row['avg_pay_rate'].values[0],
               exp_grp_row['count'].values[0] * exp_grp_row['avg_pay_rate'].values[0]]
    
    z_stat, p_value = proportions_ztest(success, count)

    # Determine statistical significance
    if p_value < 0.05:
        statistically_significant = 'Yes'
    else:
        statistically_significant = 'No'

    # Append to the significance_df for each pay_grp
    for pay_grp in pay_grp_order:
        pay_grp_row = exp_grp_row[exp_grp_row['pay_grp'] == pay_grp]

        significance_df = significance_df.append({
            'group': exp_grp,
            'pay_grp': pay_grp,
            'count': pay_grp_row['count'].values[0],
            'avg_pay_rate': pay_grp_row['avg_pay_rate'].values[0],
            'statistically_significant': statistically_significant
        }, ignore_index=True)

# Pivot table for statistical significance
significance_table = significance_df.pivot_table(index=['group'], columns=['pay_grp'], values=['count', 'avg_pay_rate', 'statistically_significant'])
significance_table = significance_table.reorder_levels([1, 0], axis=1).sort_index(axis=1, level=0)

# Add a row for control group above test0, test1, test2
control_row = significance_table.loc[['control']]
significance_table = pd.concat([control_row, significance_table])

print(avg_table)
print(significance_table)

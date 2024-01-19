import pandas as pd
from scipy.stats import ttest_ind

# Assuming your grouped DataFrame is named grouped_df
# If not, replace grouped_df with your DataFrame's actual name

# Define the order for pay_grp
pay_grp_order = ['low', 'med', 'high']

# Pivot table for averages
avg_table = pd.pivot_table(grouped_df, index=['exp_grp'], columns=['pay_grp'], values=['avg_calls', 'avg_emails', 'avg_pushes'], aggfunc='mean')
#avg_table = avg_table[['avg_calls', 'avg_emails', 'avg_pushes']].reorder_levels([1, 0], axis=1).sort_index(axis=1, level=0)
#avg_table = avg_table[pay_grp_order]

# Create a new DataFrame for statistical significance
significance_df = pd.DataFrame(columns=['group', 'pay_grp', 'count', 'avg_pay_rate', 'statistically_significant'])

# Define the control group
control_row = grouped_df[grouped_df['exp_grp'] == 'control']

# Compare each exp_grp with control regarding the pay_rate and each pay_grp
for exp_grp in grouped_df['exp_grp'].unique():
    if exp_grp == 'control':
        continue

    exp_grp_row = grouped_df[grouped_df['exp_grp'] == exp_grp]

    # Perform t-test for pay_rate
    t_stat, p_value = ttest_ind(control_row['avg_pay_rate'], exp_grp_row['avg_pay_rate'])

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

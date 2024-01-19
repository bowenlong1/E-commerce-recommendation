import pandas as pd
from scipy.stats import ttest_ind

# Assuming your grouped DataFrame is named grouped_df
# If not, replace grouped_df with your DataFrame's actual name

# Pivot table for averages
avg_table = pd.pivot_table(grouped_df, index=['exp_grp'], columns=['pay_grp'], values=['avg_calls', 'avg_emails', 'avg_pushes'], aggfunc='mean')

# Create a new DataFrame for statistical significance
significance_df = pd.DataFrame(columns=['group', 'count', 'avg_pay_rate', 'statistically_significant'])

# Compare each exp_grp with control regarding the pay_rate
control_row = grouped_df[grouped_df['exp_grp'] == 'control']

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

    # Append to the significance_df
    significance_df = significance_df.append({
        'group': exp_grp,
        'count': exp_grp_row['count'].values[0],
        'avg_pay_rate': exp_grp_row['avg_pay_rate'].values[0],
        'statistically_significant': statistically_significant
    }, ignore_index=True)

# Pivot table for statistical significance
significance_table = significance_df.pivot_table(index=['group'], values=['count', 'avg_pay_rate', 'statistically_significant'])

# Display the tables
print(avg_table)
print(significance_table)

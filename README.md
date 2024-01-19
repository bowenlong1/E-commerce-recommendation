import pandas as pd
from scipy.stats import ttest_ind

# Assuming your grouped DataFrame is named grouped_df
# If not, replace grouped_df with your DataFrame's actual name

# Define the order for pay_grp
pay_grp_order = ['low', 'med', 'high']

# Pivot table for averages
avg_table = pd.pivot_table(grouped_df, index=['exp_grp'], columns=['pay_grp'], values=['avg_calls', 'avg_emails', 'avg_pushes'], aggfunc='mean')

# Reorder columns
avg_table = avg_table[['avg_calls', 'avg_emails', 'avg_pushes']].reorder_levels([1, 0], axis=1).sort_index(axis=1, level=0)
avg_table = avg_table[pay_grp_order]

# Display the modified table
print(avg_table)



import pandas as pd

# Define the desired order for 'pay_grp' and 'equ_grp'
pay_grp_order = ['high', 'med', 'low']
equ_grp_order = ['high', 'low']

# Convert 'pay_grp' and 'equ_grp' columns to categorical with desired order
vint2['pay_grp'] = pd.Categorical(vint2['pay_grp'], categories=pay_grp_order, ordered=True)
vint2['equ_grp'] = pd.Categorical(vint2['equ_grp'], categories=equ_grp_order, ordered=True)

# Group by 'exp_grp', 'pay_grp', and 'equ_grp', then aggregate
grouped_data = vint2.groupby(['exp_grp', 'pay_grp', 'equ_grp']).agg({'acct_nbr': 'count', 'move61': 'sum', 'move91': 'sum'}).reset_index()

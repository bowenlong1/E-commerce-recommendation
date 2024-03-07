
vint2.groupby(['exp_grp', 'pay_grp', 'equ_grp']).agg({'acct_nbr': 'count', 'move61': 'sum', 'move91': 'sum'}).reset_index()

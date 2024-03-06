vint2.groupby(['exp_grp','equ_pay_grp_vint']).agg({'acct_nbr': 'count', 'move61': 'sum', 'move91': 'sum'})

vint1 = vint.merge(df[['acct_nbr', 'day_nxt', 'equity', 'equ_grp', 'pay', 'pay_grp']], how = 'inner', left_on = ['acct_nbr', 'day_key'], right_on = ['acct_nbr', 'day_nxt'])

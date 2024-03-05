print(vint[vint.duplicated(['acct_nbr', 'day_key'], keep=False)])
print(df[df.duplicated(['acct_nbr', 'day_nxt'], keep=False)])

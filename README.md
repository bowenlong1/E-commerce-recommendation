df['equ_grp'] = df['equity'].apply(lambda x: 'low' if x is not None and x > -1500 else 'high')

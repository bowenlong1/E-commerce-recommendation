12
# equity 
df['equ_grp']=df['equity'].apply(lambda x: 'low' if x>-1500 and x else 'high')
TypeError: '>' not supported between instances of 'NoneType' and 'int'

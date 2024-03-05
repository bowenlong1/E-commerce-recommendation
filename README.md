# Assuming vint1 is your DataFrame containing the tgt_daykey column

# Convert tgt_daykey to datetime format
vint1['tgt_daykey'] = pd.to_datetime(vint1['tgt_daykey'], format='%Y%m%d')

# Subtract one day from tgt_daykey to get tgt_daykey_prev
vint1['tgt_daykey_prev'] = (vint1['tgt_daykey'] - pd.DateOffset(days=1)).dt.strftime('%Y%m%d').astype(int)


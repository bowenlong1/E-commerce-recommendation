import numpy as np

df['dpd_3week'] = df['dpd_3week'].replace({None: np.nan}).astype('float64').astype('Int64')
df['since_last_pmt_day_qty'] = df['since_last_pmt_day_qty'].replace({None: np.nan}).astype('float64').astype('Int64')
df['days_to_next_pmt'] = df['days_to_next_pmt'].replace({None: np.nan}).astype('float64').astype('Int64')
# Continue with the remaining columns...

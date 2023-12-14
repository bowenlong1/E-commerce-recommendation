hist.groupby('cat_freq_545_fnl')['freq_545_fnl'].agg(['min', 'max', lambda x: x.count(dropna=False)])



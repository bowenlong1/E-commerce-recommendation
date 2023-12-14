TypeError: '>=' not supported between instances of 'str' and 'float'
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
File <command-3429633109735330>, line 16
     13 breakpoints_dpd_5_mnth_max = [float('-inf'), 4, 15, 30, 45, 60, 75, float('inf')]
     14 breakpoints_dpd_2_mnth_max = [float('-inf'), 4, 15, 30, 45, 60, 75, float('inf')]
---> 16 hist = create_cat_column(hist, 'freq_545_fnl', breakpoints_freq_545_fnl, 'cat_freq_545_fnl')
     17 hist = create_cat_column(hist, 'days_to_next_pmt', breakpoints_days_to_next_pmt, 'cat_days_to_next_pmt')
     18 hist = create_cat_column(hist, 'dpd_6_mnth_max', breakpoints_dpd_6_mnth_max, 'cat_dpd_6_mnth_max')

File <command-3429633109735330>, line 5, in create_cat_column(df, column, breakpoints, col_name)
      3 for i in range(len(breakpoints) - 1):
      4     lower_bound, upper_bound = breakpoints[i], breakpoints[i + 1]
----> 5     mask = (df[column] >= lower_bound) & (df[column] < upper_bound)
      6     df.loc[mask, col_name] = f'[{lower_bound}, {upper_bound})'
      7 return df

File /databricks/python/lib/python3.10/site-packages/pandas/core/ops/common.py:70, in _unpack_zerodim_and_defer.<locals>.new_method(self, other)
     66             return NotImplemented
     68 other = item_from_zerodim(other)
---> 70 return method(self, other)


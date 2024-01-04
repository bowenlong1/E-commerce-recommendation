
df['dpd_3week'] = df['dpd_3week'].astype('int64')
df['since_last_pmt_day_qty'] = df['since_last_pmt_day_qty'].astype('int64')
df['days_to_next_pmt'] = df['days_to_next_pmt'].astype('int64')
df['total_pmt_3m'] = df['total_pmt_3m'].astype('float64')
df['past_due_amt'] = df['past_due_amt'].astype('float64')
df['dpd_7week'] = df['dpd_7week'].astype('int64')
df['days_since_last_ext'] = df['days_since_last_ext'].astype('int64')
df['days_since_ptp'] = df['days_since_ptp'].astype('int64')
df['da
TypeError: int() argument must be a string, a bytes-like object or a real number, not 'NoneType'
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
File <command-708663598832660>, line 1
----> 1 df['dpd_3week'] = df['dpd_3week'].astype('int64')
      2 df['since_last_pmt_day_qty'] = df['since_last_pmt_day_qty'].astype('int64')
      3 df['days_to_next_pmt'] = df['days_to_next_pmt'].astype('int64')

File /databricks/python/lib/python3.10/site-packages/pandas/core/generic.py:5912, in NDFrame.astype(self, dtype, copy, errors)
   5905     results = [
   5906         self.iloc[:, i].astype(dtype, copy=copy)
   5907         for i in range(len(self.columns))
   5908     ]
   5910 else:
   5911     # else, only a single dtype is given
-> 5912     new_data = self._mgr.astype(dtype=dtype, copy=copy, errors=errors)
   5913     return self._constructor(new_data).__finalize__(self, method="astype")
   5915 # GH 33113: handle empty frame or series

File /databricks/python/lib/python3.10/site-packages/pandas/core/internals/managers.py:419, in BaseBlockManager.astype(self, dtype, copy, errors)
    418 def astype(self: T, dtype, copy: bool = False, errors: str = "raise") -> T:
--> 419     return self.apply("astype", dtype=dtype, copy=copy, errors=errors)

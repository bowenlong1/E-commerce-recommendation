df['dpd'] = df['dpd'].astype('Int64')
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
File <command-708663598832668>, line 1
----> 1 df['dpd'] = df['dpd'].astype('Int64')

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

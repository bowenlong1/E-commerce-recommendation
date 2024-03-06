---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
File <command-669854423335525>, line 26
     23 days_to_add = [i + 1 for i in range(14)]
     25 for condition, days in zip(conditions, days_to_add):
---> 26     vint.loc[condition & pd.isnull(vint['tgt_dt']), 'tgt_dt'] = vint['dt'] + pd.DateOffset(days=days)

File /databricks/python/lib/python3.10/site-packages/pandas/core/ops/common.py:70, in _unpack_zerodim_and_defer.<locals>.new_method(self, other)
     66             return NotImplemented
     68 other = item_from_zerodim(other)
---> 70 return method(self, other)

File /databricks/python/lib/python3.10/site-packages/pandas/core/arraylike.py:100, in OpsMixin.__add__(self, other)
     98 @unpack_zerodim_and_defer("__add__")
     99 def __add__(self, other):
--> 100     return self._arith_method(other, operator.add)

File /databricks/python/lib/python3.10/site-packages/pandas/core/series.py:5639, in Series._arith_method(self, other, op)
   5637 def _arith_method(self, other, op):
   5638     self, other = ops.align_method_SERIES(self, other)
-> 5639     return base.IndexOpsMixin._arith_method(self, other, op)

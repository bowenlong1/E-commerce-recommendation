TypeError: '>' not supported between instances of 'NoneType' and 'int'
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
File <command-501241298297315>, line 2
      1 ## equity group
----> 2 df['equ_grp']=df['equity'].apply(lambda x: 'low' if x>-1500 else 'high')

File /databricks/python/lib/python3.10/site-packages/pandas/core/series.py:4433, in Series.apply(self, func, convert_dtype, args, **kwargs)
   4323 def apply(
   4324     self,
   4325     func: AggFuncType,
   (...)
   4328     **kwargs,
   4329 ) -> DataFrame | Series:
   4330     """
   4331     Invoke function on values of Series.
   4332 
   (...)
   4431     dtype: float64
   4432     """
-> 4433     return SeriesApply(self, func, convert_dtype, args, kwargs).apply()

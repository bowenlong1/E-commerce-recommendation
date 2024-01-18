TypeError: unsupported operand type(s) for +: 'object' and '<class 'int'>'
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
File <command-501241298317562>, line 3
      1 dist_acct['call7'] = (
      2     dist_acct.merge(call, how='left', left_on=['loan_acct_nbr'], right_on=['loan_acct_nbr'])
----> 3     .query('workload_dt >= contact_dt and workload_dt <= contact_dt + 7')
      4     .groupby(['loan_acct_nbr', 'contact_dt'])['sum_call']
      5     .sum()
      6     .fillna(0)
      7     .astype(int)
      8 )

File /databricks/python/lib/python3.10/site-packages/pandas/core/frame.py:4111, in DataFrame.query(self, expr, inplace, **kwargs)
   4109 kwargs["level"] = kwargs.pop("level", 0) + 1
   4110 kwargs["target"] = None
-> 4111 res = self.eval(expr, **kwargs)
   4113 try:
   4114     result = self.loc[res]

File /databricks/python/lib/python3.10/site-packages/pandas/core/frame.py:4240, in DataFrame.eval(self, expr, inplace, **kwargs)
   4237     kwargs["target"] = self

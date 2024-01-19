---------------------------------------------------------------------------
KeyError                                  Traceback (most recent call last)
File <command-501241298327030>, line 58
     55 significance_table = significance_table.reorder_levels([1, 0], axis=1).sort_index(axis=1, level=0)
     57 # Add a row for control group above test0, test1, test2
---> 58 control_row = significance_table.loc[['control']].iloc[0]
     59 significance_table = pd.concat([control_row, significance_table])
     61 # Add a column for statistical significance with control

File /databricks/python/lib/python3.10/site-packages/pandas/core/indexing.py:967, in _LocationIndexer.__getitem__(self, key)
    964 axis = self.axis or 0
    966 maybe_callable = com.apply_if_callable(key, self.obj)
--> 967 return self._getitem_axis(maybe_callable, axis=axis)

File /databricks/python/lib/python3.10/site-packages/pandas/core/indexing.py:1194, in _LocIndexer._getitem_axis(self, key, axis)
   1191     if hasattr(key, "ndim") and key.ndim > 1:
   1192         raise ValueError("Cannot index with multidimensional key")
-> 1194     return self._getitem_iterable(key, axis=axis)
   1196 # nested tuple slicing
   1197 if is_nested_tuple(key, labels):

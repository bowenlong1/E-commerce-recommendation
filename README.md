---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
File <command-3429633109745043>, line 16
     13 # Iterate over variables
     14 for i, var in enumerate(variables):
     15     # Calculate PSI and get actual/expected counts
---> 16     psi, actual_counts, expected_counts = calculate_psi(expected, actual, day_key_prior, day_key_after, var)
     18     # Plot actual and expected distributions
     19     sns.barplot(x=expected_counts.index, y=expected_counts, ax=axes[i], color='blue', label='Expected',alpha = 0.5)

File <command-3429633109745036>, line 5, in calculate_psi(expected, actual, day_key_prior, day_key_after, var)
      4 def calculate_psi(expected, actual, day_key_prior, day_key_after, var):
----> 5     expected_bins = expected[(day_key_prior <= expected.day_key) & (expected.day_key <= day_key_after)][var]
      6     count = expected[(day_key_prior <= expected.day_key) & (expected.day_key <= day_key_after)]['day_key'].nunique()
      8     actual_bins = actual[var]

File /databricks/python/lib/python3.10/site-packages/pandas/core/ops/common.py:70, in _unpack_zerodim_and_defer.<locals>.new_method(self, other)
     66             return NotImplemented
     68 other = item_from_zerodim(other)
---> 70 return method(self, other)


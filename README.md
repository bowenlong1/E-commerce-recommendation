TypeError: 'AxesSubplot' object is not subscriptable
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
File <command-3429633109745043>, line 19
     16 psi, actual_counts, expected_counts = calculate_psi(expected, actual, day_key_prior, day_key_after, var)
     18 # Plot actual and expected distributions
---> 19 sns.barplot(x=expected_counts.index, y=expected_counts, ax=axes[i], color='blue', label='Expected',alpha = 0.5)
     20 sns.barplot(x=actual_counts.index, y=actual_counts, ax=axes[i], color='orange', label='Actual', alpha = 0.5)
     22 axes[i].set_title(f'Variable: {var}, PSI: {psi:.4f}')

TypeError: 'AxesSubplot' object is not subscriptable

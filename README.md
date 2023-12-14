## benchmark days
day_key_prior = 20210601
day_key_after = 20210824

expected = hist.copy()
actual = hist[hist.day_key == 20210831]

# Variables to analyze
variables = ['cat_dpd_6_mnth_max', 'cat_dpd_5_mnth_max', 'cat_dpd_2_mnth_max']

# Create subplots for each variable
fig, axes = plt.subplots(nrows=len(variables), ncols=1, figsize=(8, 6 * len(variables)))

# Iterate over variables
for i, var in enumerate(variables):
    # Calculate PSI and get actual/expected counts
    psi, actual_counts, expected_counts = calculate_psi(expected, actual, day_key_prior, day_key_after, var)

    # Plot actual and expected distributions with adjusted transparency
    sns.barplot(x=expected_counts.index, y=expected_counts, ax=axes, color='blue', label='Expected', alpha=0.5)
    sns.barplot(x=actual_counts.index, y=actual_counts, ax=axes, color='orange', label='Actual', alpha=0.5)

    axes.set_title(f'Variable: {var}, PSI: {psi:.4f}')
    axes.legend()

plt.tight_layout()
plt.show()


AttributeError: 'numpy.ndarray' object has no attribute 'bar'
---------------------------------------------------------------------------
AttributeError                            Traceback (most recent call last)
File <command-3429633109745054>, line 20
     17 psi, actual_counts, expected_counts = calculate_psi(expected, actual, day_key_prior, day_key_after, var)
     19 # Plot actual and expected distributions with adjusted transparency
---> 20 sns.barplot(x=expected_counts.index, y=expected_counts, ax=axes, color='blue', label='Expected', alpha=0.5)
     21 sns.barplot(x=actual_counts.index, y=actual_counts, ax=axes, color='orange', label='Actual', alpha=0.5)
     23 axes.set_title(f'Variable: {var}, PSI: {psi:.4f}')

File /databricks/python/lib/python3.10/site-packages/seaborn/_decorators.py:46, in _deprecate_positional_args.<locals>.inner_f(*args, **kwargs)
     36     warnings.warn(
     37         "Pass the following variable{} as {}keyword arg{}: {}. "
     38         "From version 0.12, the only valid positional argument "
   (...)
     43         FutureWarning
     44     )
     45 kwargs.update({k: arg for k, arg in zip(sig.parameters, args)})
---> 46 return f(**kwargs)

File /databricks/python/lib/python3.10/site-packages/seaborn/categorical.py:3190, in barplot(x, y, hue, data, order, hue_order, estimator, ci, n_boot, units, seed, orient, color, palette, saturation, errcolor, errwidth, capsize, dodge, ax, **kwargs)
   3187 if ax is None:
   3188     ax = plt.gca()
-> 3190 plotter.plot(ax, kwargs)
   3191 return ax

File /databricks/python/lib/python3.10/site-packages/seaborn/categorical.py:1639, in _BarPlotter.plot(self, ax, bar_kws)
   1637 def plot(self, ax, bar_kws):
   1638     """Make the plot."""
-> 1639     self.draw_bars(ax, bar_kws)
   1640     self.annotate_axes(ax)
   1641     if self.orient == "h":

File /databricks/python/lib/python3.10/site-packages/seaborn/categorical.py:1598, in _BarPlotter.draw_bars(self, ax, kws)
   1596 """Draw the bars onto `ax`."""
   1597 # Get the right matplotlib function depending on the orientation
-> 1598 barfunc = ax.bar if self.orient == "v" else ax.barh
   1599 barpos = np.arange(len(self.statistic))
   1601 if self.plot_hues is None:
   1602 
   1603     # Draw the bars

AttributeError: 'numpy.ndarray' object has no attribute 'bar'
Command took 0.56 seconds -- by bowen.long@gmfinancial.com at 12/14/2023, 3:15:23 PM on Lon

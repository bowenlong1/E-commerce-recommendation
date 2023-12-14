# Variables to analyze
variables = ['cat_freq_545_fnl', 'cat_days_to_next_pmt', 'cat_dpd_6_mnth_max', 'cat_dpd_5_mnth_max', 'cat_dpd_2_mnth_max']

# Day keys
day_key_prior = 20231023
day_key_after = 20231121

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

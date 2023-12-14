import matplotlib.pyplot as plt
import seaborn as sns

def calculate_psi(expected, actual, day_key_prior, day_key_after, var):
    expected_bins = expected[(day_key_prior <= expected.day_key) & (expected.day_key <= day_key_after)][var]
    count = expected[(day_key_prior <= expected.day_key) & (expected.day_key <= day_key_after)]['day_key'].nunique()

    actual_bins = actual[var]

    expected_counts = expected_bins.value_counts(sort=False).sort_index() / count
    actual_counts = actual_bins.value_counts(sort=False).sort_index()

    # Calculate PSI for each bin
    psi_values = ((actual_counts - expected_counts) / expected_counts).replace({0: 1e-10})

    # Sum the PSI values
    psi = np.sum(psi_values * np.log(actual_counts / expected_counts))

    return psi, actual_counts, expected_counts

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

    # Plot actual and expected distributions
    sns.barplot(x=expected_counts.index, y=expected_counts, ax=axes[i], color='blue', label='Expected')
    sns.barplot(x=actual_counts.index, y=actual_counts, ax=axes[i], color='orange', label='Actual')

    axes[i].set_title(f'Variable: {var}, PSI: {psi:.4f}')
    axes[i].legend()

plt.tight_layout()
plt.show()


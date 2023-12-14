import pandas as pd
import numpy as np

def calculate_psi(expected, actual):
    # Use unique categories from 'expected' as bin edges
    bin_edges = pd.IntervalIndex.from_arrays(expected.cat.categories, expected.cat.categories, closed='left')

    # Bin the data
    expected_bins = pd.cut(expected, bins=bin_edges, include_lowest=True)
    actual_bins = pd.cut(actual, bins=bin_edges, include_lowest=True)

    # Calculate observed and expected frequencies
    expected_counts = expected_bins.value_counts(sort=False)
    actual_counts = actual_bins.value_counts(sort=False)

    # Calculate PSI for each bin
    psi_values = ((actual_counts - expected_counts) / expected_counts).replace({0: 1e-10})

    # Sum the PSI values
    psi = np.sum(psi_values * np.log(actual_counts / expected_counts))

    return psi

# Example usage
# psi_value = calculate_psi(acct['cat_freq_545_fnl'], hist['cat_freq_545_fnl'])
# print(f'PSI for cat_freq_545_fnl: {psi_value}')

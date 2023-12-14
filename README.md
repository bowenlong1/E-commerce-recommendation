def calculate_psi(expected, actual, day_key_prior, day_key_after, var):
    expected_bins = expected[(day_key_prior<=expected.day_key)&(expected.day_key<=day_key_after)][var]
    count = expected[(day_key_prior<=expected.day_key)&(expected.day_key<=day_key_after)]['day_key'].nunique()

    actual_bins = actual[var]

    expected_counts = expected_bins.value_counts(sort=False).sort_index()/count
    actual_counts = actual_bins.value_counts(sort=False).sort_index()

    # Calculate PSI for each bin
    psi_values = ((actual_counts - expected_counts) / expected_counts).replace({0: 1e-10})

    # Sum the PSI values
    psi = np.sum(psi_values * np.log(actual_counts / expected_counts))

    return psi


day_key_prior = 20231023
day_key_after = 20231121

expected = df.copy()
actual = df[df.day_key == 20231212]

var1 = 'cat_days_to_next_pmt'
var2 = 'cat_freq_545_fnl'

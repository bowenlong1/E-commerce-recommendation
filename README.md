from scipy.stats import wasserstein_distance

def wasserstein_distance_metric_numerical(df, col_name1, col_name2):
    # Extract the numerical values for the two columns
    values1 = df[col_name1].dropna().values
    values2 = df[col_name2].dropna().values
    
    # Calculate Wasserstein Distance
    wasserstein_dist = wasserstein_distance(values1, values2)

    return wasserstein_dist

# Example usage
wasserstein_distance_value = wasserstein_distance_metric_numerical(df, 'dpd_2_mnth_max', 'dpd_6_mnth_max')
print(f"Wasserstein Distance: {wasserstein_distance_value}")

from scipy.stats import entropy

def kl_divergence(df, col_name1, col_name2):
    # Extract the distributions for the two columns
    dist1 = df[col_name1].value_counts(normalize=True).sort_index()
    dist2 = df[col_name2].value_counts(normalize=True).sort_index()
    
    # Add missing categories if necessary
    all_categories = set(dist1.index) | set(dist2.index)
    dist1 = dist1.reindex(all_categories, fill_value=0)
    dist2 = dist2.reindex(all_categories, fill_value=0)
    
    # Calculate KL Divergence
    kl_div = entropy(dist1, dist2)
    
    return kl_div

# Example usage
kl_divergence_value = kl_divergence(df, 'cat_dpd_2_mnth_max', 'cat_dpd_6_mnth_max')
print(f"KL Divergence: {kl_divergence_value}")


import numpy as np
from scipy.stats import entropy

def jensen_shannon_divergence(df, col_name1, col_name2):
    # Extract the distributions for the two columns
    dist1 = df[col_name1].value_counts(normalize=True).sort_index()
    dist2 = df[col_name2].value_counts(normalize=True).sort_index()
    
    # Add missing categories if necessary
    all_categories = set(dist1.index) | set(dist2.index)
    dist1 = dist1.reindex(all_categories, fill_value=0)
    dist2 = dist2.reindex(all_categories, fill_value=0)
    
    # Calculate the average distribution M
    m = 0.5 * (dist1 + dist2)

    # Calculate KL Divergence for P and Q relative to M
    kl_div_p_m = entropy(dist1, m)
    kl_div_q_m = entropy(dist2, m)

    # Calculate Jensen-Shannon Divergence
    jsd = 0.5 * (kl_div_p_m + kl_div_q_m)

    return jsd

# Example usage
jsd_value = jensen_shannon_divergence(df, 'cat_dpd_2_mnth_max', 'cat_dpd_6_mnth_max')
print(f"Jensen-Shannon Divergence: {jsd_value}")



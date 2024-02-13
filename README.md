from sklearn.metrics import roc_auc_score

# Initialize a list to store metrics
metrics_by_group = []

# Iterate over each quantile combination
for idx, quantile_combo in enumerate(quantile_combinations):
    # Filter the DataFrame for the current quantile combination
    filtered_df = acct[
        (acct['dpd_3week_quantile'] == quantile_combo[0]) &
        (acct['since_last_pmt_day_qty_quantile'] == quantile_combo[1]) &
        (acct['days_to_next_pmt_quantile'] == quantile_combo[2])
    ]
    
    # Check if there are samples in the DataFrame
    if len(filtered_df) > 0:
        # Compute metrics
        accuracy = accuracy_score(filtered_df['result'], filtered_df['pred'])
        f1 = f1_score(filtered_df['result'], filtered_df['pred'])
        
        # Check if there are both positive and negative samples
        if len(filtered_df['result'].unique()) > 1:
            roc_auc = roc_auc_score(filtered_df['result'], filtered_df['pred'])
        else:
            roc_auc = 0.5  # Set ROC-AUC to 0.5 if there is only one class
        
        # Create a string to indicate the group
        group_indicator = '-'.join(['dpd{}'.format(quantile_combo[0] + 1),
                                    'last{}'.format(quantile_combo[1] + 1),
                                    'next{}'.format(quantile_combo[2] + 1)])
        
        # Store the metrics
        metrics_by_group.append({
            'Group': group_indicator,
            'Accuracy': accuracy,
            'F1 Score': f1,
            'ROC-AUC': roc_auc
        })

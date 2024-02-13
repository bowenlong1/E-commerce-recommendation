from itertools import product

# Create quantiles for each variable
acct['dpd_3week_quantile'] = pd.qcut(acct['dpd_3week'], q=3, labels=False, duplicates='drop')
acct['since_last_pmt_day_qty_quantile'] = pd.qcut(acct['since_last_pmt_day_qty'], q=3, labels=False, duplicates='drop')
acct['days_to_next_pmt_quantile'] = pd.qcut(acct['days_to_next_pmt'], q=3, labels=False, duplicates='drop')

# Generate combinations of quantiles
quantile_combinations = list(product(range(3), repeat=3))

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
        roc_auc = roc_auc_score(filtered_df['result'], filtered_df['pred'])
        
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

# Create a DataFrame from the metrics
metrics_df = pd.DataFrame(metrics_by_group)

# Sort the DataFrame by decreasing F1 score
metrics_df = metrics_df.sort_values(by='F1 Score', ascending=False)

# Create a plot
plt.figure(figsize=(10, 6))
sns.barplot(x='F1 Score', y='Group', data=metrics_df, palette='viridis')
plt.xlabel('F1 Score')
plt.ylabel('Group')
plt.title('F1 Score by Group')
plt.show()

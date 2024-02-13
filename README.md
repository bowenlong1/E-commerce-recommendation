import pandas as pd
import numpy as np
from sklearn.metrics import accuracy_score, f1_score, roc_auc_score

# Assuming 'acct' is your pandas DataFrame containing the actual and predicted values,
# as well as the continuous variables dpd_3week, since_last_pmt_day_qty, days_to_next_pmt, and past_due_amt

# Define the continuous variables
continuous_variables = ['dpd_3week', 'since_last_pmt_day_qty', 'days_to_next_pmt', 'past_due_amt']

# Define the quantiles
quantiles = [0, 0.25, 0.5, 0.75, 1]

# Calculate performance metrics for each continuous variable and each quantile
metrics_by_variable = []

for var in continuous_variables:
    # Calculate quantiles for the variable
    quantile_values = acct[var].quantile(quantiles)
    
    # Create buckets based on quantiles
    buckets = pd.cut(acct[var], bins=quantile_values, labels=[f'Q{i}' for i in range(1, len(quantiles))])
    
    # Calculate metrics for each bucket
    for bucket in buckets.unique():
        filtered_df = acct[buckets == bucket]
        
        # Calculate metrics
        accuracy = accuracy_score(filtered_df['result'], filtered_df['pred'])
        f1 = f1_score(filtered_df['result'], filtered_df['pred'])
        roc_auc = roc_auc_score(filtered_df['result'], filtered_df['pred'])
        
        # Store the metrics
        metrics_by_variable.append({
            'Variable': var,
            'Quantile': bucket,
            'Accuracy': accuracy,
            'F1 Score': f1,
            'ROC-AUC': roc_auc
        })

# Convert the list of dictionaries to a DataFrame
metrics_df = pd.DataFrame(metrics_by_variable)

# Print the performance metrics breakdown
print(metrics_df)

import matplotlib.pyplot as plt

# Iterate over each continuous variable
for var in continuous_variables:
    # Filter the metrics DataFrame for the current variable
    var_metrics = metrics_df[metrics_df['Variable'] == var]
    
    # Set up subplots
    fig, axes = plt.subplots(nrows=1, ncols=3, figsize=(15, 5))
    fig.suptitle(f'Performance Metrics Breakdown for {var}', fontsize=16)
    
    # Plot accuracy
    axes[0].bar(var_metrics['Quantile'], var_metrics['Accuracy'], color='skyblue')
    axes[0].set_title('Accuracy')
    axes[0].set_ylim(0, 1)
    
    # Plot F1 score
    axes[1].bar(var_metrics['Quantile'], var_metrics['F1 Score'], color='lightgreen')
    axes[1].set_title('F1 Score')
    axes[1].set_ylim(0, 1)
    
    # Plot ROC-AUC
    axes[2].bar(var_metrics['Quantile'], var_metrics['ROC-AUC'], color='salmon')
    axes[2].set_title('ROC-AUC')
    axes[2].set_ylim(0, 1)
    
    # Adjust layout
    plt.tight_layout()
    plt.show()

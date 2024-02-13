The error you're encountering suggests that the `roc_auc_score` function is encountering empty arrays or arrays with zero samples, which leads to division by zero errors and ill-defined F1 scores. This typically happens when there are no positive or negative samples in the data for a particular quantile.

To address this issue, you can add a check to ensure that there are samples in the data before computing the metrics. Here's how you can modify the code:

```python
from sklearn.metrics import accuracy_score, f1_score, roc_auc_score
import numpy as np

# Iterate over each continuous variable
for var in continuous_variables:
    # Filter the DataFrame for the current variable
    var_df = acct[acct[var].notnull()]
    
    # Compute quantiles
    quantiles = pd.qcut(var_df[var], q=4, labels=False, duplicates='drop')
    
    # Iterate over each quantile
    for quantile in range(4):
        # Filter the DataFrame for the current quantile
        quantile_df = var_df[quantiles == quantile]
        
        # Check if there are samples in the DataFrame
        if len(quantile_df) > 0:
            # Compute metrics
            accuracy = accuracy_score(quantile_df['result'], quantile_df['pred'])
            f1 = f1_score(quantile_df['result'], quantile_df['pred'])
            roc_auc = roc_auc_score(quantile_df['result'], quantile_df['pred'])
            
            # Store the metrics
            metrics_by_variable.append({
                'Variable': var,
                'Quantile': quantile,
                'Accuracy': accuracy,
                'F1 Score': f1,
                'ROC-AUC': roc_auc
            })
```

This modification ensures that the metrics are computed only if there are samples in the DataFrame for the current quantile, thus avoiding the division by zero errors and ill-defined F1 scores.

import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
from sklearn.metrics import accuracy_score, f1_score, roc_auc_score

# Assuming 'acct' is your pandas DataFrame containing the actual and predicted values,
# as well as the continuous variables dpd_3week, since_last_pmt_day_qty, days_to_next_pmt, and past_due_amt

# Calculate performance metrics for each continuous variable
metrics_by_variable = []

continuous_variables = ['dpd_3week', 'since_last_pmt_day_qty', 'days_to_next_pmt', 'past_due_amt']

for var in continuous_variables:
    performance = {}
    
    # Filter the dataframe for rows where the continuous variable is not null
    filtered_df = acct.dropna(subset=[var])
    
    # Calculate metrics
    accuracy = accuracy_score(filtered_df['result'], filtered_df['pred'])
    f1 = f1_score(filtered_df['result'], filtered_df['pred'])
    roc_auc = roc_auc_score(filtered_df['result'], filtered_df['pred'])
    
    # Store the metrics
    performance['Variable'] = var
    performance['Accuracy'] = accuracy
    performance['F1 Score'] = f1
    performance['ROC-AUC'] = roc_auc
    
    metrics_by_variable.append(performance)

# Convert the list of dictionaries to a DataFrame
metrics_df = pd.DataFrame(metrics_by_variable)

# Print the performance metrics breakdown
print(metrics_df)

# Visualize the breakdown using seaborn
sns.set(style="whitegrid")
plt.figure(figsize=(10, 6))
sns.barplot(x='Variable', y='Accuracy', data=metrics_df, color='skyblue')
plt.title('Accuracy by Continuous Variable')
plt.xlabel('Continuous Variable')
plt.ylabel('Accuracy')
plt.xticks(rotation=45)
plt.show()

plt.figure(figsize=(10, 6))
sns.barplot(x='Variable', y='F1 Score', data=metrics_df, color='lightgreen')
plt.title('F1 Score by Continuous Variable')
plt.xlabel('Continuous Variable')
plt.ylabel('F1 Score')
plt.xticks(rotation=45)
plt.show()

plt.figure(figsize=(10, 6))
sns.barplot(x='Variable', y='ROC-AUC', data=metrics_df, color='salmon')
plt.title('ROC-AUC by Continuous Variable')
plt.xlabel('Continuous Variable')
plt.ylabel('ROC-AUC')
plt.xticks(rotation=45)
plt.show()


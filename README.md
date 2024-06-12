import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Assuming df_notax is your DataFrame

# Define the binning categories
dpd_bins = [0, 30, 60, 90]
dpd_labels = ['1-30 DPD', '31-60 DPD', '61-90 DPD']

dsf_bins = [0, 30, 60, 90, float('inf')]
dsf_labels = ['21-30 DSF', '31-60 DSF', '61-90 DSF', '91+ DSF']

days_since_last_rpt_bins = [0, 7, 14, 21, 30, float('inf')]
days_since_last_rpt_labels = ['1 Week', '2 Weeks', '3 Weeks', '1 Month', '1 Month+']

precsn_score_bins = [0, 579, 669, 739, 799, float('inf')]
precsn_score_labels = ['Poor <=579', 'Fair 580-669', 'Good 670-739', 'Very Good 740-799', 'Exceptional >=800']

past_due_amt_bins = [0, 500, 1000, 2000, float('inf')]
past_due_amt_labels = ['<=$500', '$500-$1000', '$1000-$2000', '$2000+']

# Bin the data
df_notax['dpd_category'] = pd.cut(df_notax['dpd'], bins=dpd_bins, labels=dpd_labels, right=True)
df_notax['dsf_category'] = pd.cut(df_notax['dsf'], bins=dsf_bins, labels=dsf_labels, right=False)

# Bin the data with missing category for 'days_since_last_rpt' and 'precsn_score'
def add_missing_category(series, bins, labels):
    category = pd.cut(series, bins=bins, labels=labels, right=True)
    if series.isnull().any():
        category = category.cat.add_categories(['Missing'])
        category = category.fillna('Missing')
    return category

df_notax['days_since_last_rpt_category'] = add_missing_category(df_notax['days_since_last_rpt'], days_since_last_rpt_bins, days_since_last_rpt_labels)
df_notax['precsn_score_category'] = add_missing_category(df_notax['precsn_score'], precsn_score_bins, precsn_score_labels)

df_notax['past_due_amt_category'] = pd.cut(df_notax['past_due_amt'], bins=past_due_amt_bins, labels=past_due_amt_labels, right=True)

# Create bar plots
fig, axs = plt.subplots(7, 3, figsize=(30, 35))

# Plot for dpd_category
df_notax.groupby('dpd_category')['pay'].mean().plot(kind='bar', ax=axs[0, 0], color='skyblue', edgecolor='black')
axs[0, 0].set_title('Propensity by Days Past Due (DPD)')
axs[0, 0].set_xlabel('DPD Category')
axs[0, 0].set_ylabel('Propensity to Pay')

df_notax.groupby('dpd_category')['pay14'].sum().plot(kind='bar', ax=axs[0, 1], color='skyblue', edgecolor='black')
axs[0, 1].set_title('Actual Pay by Days Past Due (DPD)')
axs[0, 1].set_xlabel('DPD Category')
axs[0, 1].set_ylabel('Actual Pay Count')

df_notax['dpd_category'].value_counts().reindex(dpd_labels + ['Missing']).plot(kind='bar', ax=axs[0, 2], color='skyblue', edgecolor='black')
axs[0, 2].set_title('Count by Days Past Due (DPD)')
axs[0, 2].set_xlabel('DPD Category')
axs[0, 2].set_ylabel('Count')

# Plot for dsf_category
df_notax.groupby('dsf_category')['pay'].mean().plot(kind='bar', ax=axs[1, 0], color='lightgreen', edgecolor='black')
axs[1, 0].set_title('Propensity by Days Since Finalization (DSF)')
axs[1, 0].set_xlabel('DSF Category')
axs[1, 0].set_ylabel('Propensity to Pay')

df_notax.groupby('dsf_category')['pay14'].sum().plot(kind='bar', ax=axs[1, 1], color='lightgreen', edgecolor='black')
axs[1, 1].set_title('Actual Pay by Days Since Finalization (DSF)')
axs[1, 1].set_xlabel('DSF Category')
axs[1, 1].set_ylabel('Actual Pay Count')

df_notax['dsf_category'].value_counts().reindex(dsf_labels + ['Missing']).plot(kind='bar', ax=axs[1, 2], color='lightgreen', edgecolor='black')
axs[1, 2].set_title('Count by Days Since Finalization (DSF)')
axs[1, 2].set_xlabel('DSF Category')
axs[1, 2].set_ylabel('Count')

# Plot for days_since_last_rpt_category
df_notax.groupby('days_since_last_rpt_category')['pay'].mean().reindex(days_since_last_rpt_labels + ['Missing']).plot(kind='bar', ax=axs[2, 0], color='coral', edgecolor='black')
axs[2, 0].set_title('Propensity by Days Since Last Reporting')
axs[2, 0].set_xlabel('Days Since Last Reporting Category')
axs[2, 0].set_ylabel('Propensity to Pay')

df_notax.groupby('days_since_last_rpt_category')['pay14'].sum().reindex(days_since_last_rpt_labels + ['Missing']).plot(kind='bar', ax=axs[2, 1], color='coral', edgecolor='black')
axs[2, 1].set_title('Actual Pay by Days Since Last Reporting')
axs[2, 1].set_xlabel('Days Since Last Reporting Category')
axs[2, 1].set_ylabel('Actual Pay Count')

df_notax['days_since_last_rpt_category'].value_counts().reindex(days_since_last_rpt_labels + ['Missing']).plot(kind='bar', ax=axs[2, 2], color='coral', edgecolor='black')
axs[2, 2].set_title('Count by Days Since Last Reporting')
axs[2, 2].set_xlabel('Days Since Last Reporting Category')
axs[2, 2].set_ylabel('Count')

# Plot for precsn_score_category
df_notax.groupby('precsn_score_category')['pay'].mean().reindex(precsn_score_labels + ['Missing']).plot(kind='bar', ax=axs[3, 0], color='purple', edgecolor='black')
axs[3, 0].set_title('Propensity by FICO Score')
axs[3, 0].set_xlabel('FICO Score Category')
axs[3, 0].set_ylabel('Propensity to Pay')

df_notax.groupby('precsn_score_category')['pay14'].sum().reindex(precsn_score_labels + ['Missing']).plot(kind='bar', ax=axs[3, 1], color='purple', edgecolor='black')
axs[3, 1].set_title('Actual Pay by FICO Score')
axs[3, 1].set_xlabel('FICO Score Category')
axs[3, 1].set_ylabel('Actual Pay Count')

df_notax['precsn_score_category'].value_counts().reindex(precsn_score_labels + ['Missing']).plot(kind='bar', ax=axs[3, 2], color='purple', edgecolor='black')
axs[3, 2].set_title('Count by FICO Score')
axs[3, 2].set_xlabel('FICO Score Category')
axs[3, 2].set_ylabel('Count')

# Plot for past_due_amt_category
df_notax.groupby('past_due_amt_category')['pay'].mean().plot(kind='bar', ax=axs[4, 0], color='orange', edgecolor='black')
axs[4, 0].set_title('Propensity by Past Due Amount')
axs[4, 0].set_xlabel('Past Due Amount Category')
axs[4, 0].set_ylabel('Propensity to Pay')

df_notax.groupby('past_due_amt_category')['pay14'].sum().plot(kind='bar', ax=axs[4, 1], color='orange', edgecolor='black')
axs[4, 1].set_title('Actual Pay by Past Due Amount')
axs[4, 1].set_xlabel('Past Due Amount Category')
axs[4, 1].set_ylabel('Actual Pay Count')

df_notax['past_due_amt_category'].value_counts().reindex(past_due_amt_labels + ['Missing']).plot(kind='bar', ax=axs[4, 2], color='orange', edgecolor='black')
axs[4, 2].set_title('Count by Past Due Amount')
axs[4, 2].set_xlabel('Past Due Amount Category')
axs[4, 2].set_ylabel('Count')

# Plot for mil_only
df_notax.groupby('mil_only')['pay'].mean().plot(kind='bar', ax=axs[5, 0], color='blue', edgecolor='black')
axs[5, 0].set_title('Propensity by Excess Mileage Fee ONLY')
axs[5, 0].set_xlabel('Excess Mileage Fee Only')
axs[5, 0].set_ylabel('Propensity to Pay')
axs[5, 0].set_xticklabels(['No', 'Yes'])

df_notax.groupby('mil_only')['pay14'].sum().plot(kind='bar', ax=axs[5, 1], color='blue', edgecolor='black')
axs[5, 1].set_title('Actual Pay by Excess Mileage Fee ONLY')
axs[5, 1].set_xlabel('Excess Mileage Fee Only')
axs[5, 1].set_ylabel('Actual Pay Count')
axs[5, 1].set_xticklabels(['No', 'Yes'])

df_notax['mil_only'].value_counts().plot(kind='bar', ax=axs[5, 2], color='blue', edgecolor='black')
axs[5, 2].set_title('Count by Excess Mileage Fee ONLY')
axs[5, 2].set_xlabel('Excess Mileage Fee Only')
axs[5, 2].set_ylabel('Count')
axs[5, 2].set_xticklabels(['No', 'Yes'])

# Plot for ewt_only
df_notax.groupby('ewt_only')['pay'].mean().plot(kind='bar', ax=axs[6, 0], color='red', edgecolor='black')
axs[6, 0].set_title('Propensity by Excessive Wear and Tear Fee ONLY')
axs[6, 0].set_xlabel('Excessive Wear and Tear Fee Only')
axs[6, 0].set_ylabel('Propensity to Pay')
axs[6, 0].set_xticklabels(['No', 'Yes'])

df_notax.groupby('ewt_only')['pay14'].sum().plot(kind='bar', ax=axs[6, 1], color='red', edgecolor='black')
axs[6, 1].set_title('Actual Pay by Excessive Wear and Tear Fee ONLY')
axs[6, 1].set_xlabel('Excessive Wear and Tear Fee Only')
axs[6, 1].set_ylabel('Actual Pay Count')
axs[6, 1].set_xticklabels(['No', 'Yes'])

df_notax['ewt_only'].value_counts().plot(kind='bar', ax=axs[6, 2], color='red', edgecolor='black')
axs[6, 2].set_title('Count by Excessive Wear and Tear Fee ONLY')
axs[6, 2].set_xlabel('Excessive Wear and Tear Fee Only')
axs[6, 2].set_ylabel('Count')
axs[6, 2].set_xticklabels(['No', 'Yes'])

plt.tight_layout()
plt.show()

import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Assuming df_notax is your DataFrame

# Define the binning categories
dpd_bins = [0, 30, 60, 90, np.inf]
dpd_labels = ['1-30 DPD', '31-60 DPD', '61-90 DPD']

dsf_bins = [0, 30, 60, 90, np.inf]
dsf_labels = ['21-30 DSF', '31-60 DSF', '61-90 DSF', '91+ DSF']

days_since_last_rpt_bins = [0, 7, 14, 21, 30, np.inf]
days_since_last_rpt_labels = ['1 Week', '2 Weeks', '3 Weeks', '1 Month', '1 Month+']

precsn_score_bins = [0, 579, 669, 739, 799, np.inf]
precsn_score_labels = ['Poor <=579', 'Fair 580-669', 'Good 670-739', 'Very Good 740-799', 'Exceptional >=800']

past_due_amt_bins = [0, 500, 1000, 2000, np.inf]
past_due_amt_labels = ['<=$500', '$500-$1000', '$1000-$2000', '$2000+']

# Function to add 'Missing' category
def add_missing_category(series, bins, labels):
    category = pd.cut(series, bins=bins, labels=labels, right=True)
    if series.isnull().any():
        category = category.cat.add_categories(['Missing'])
        category = category.fillna('Missing')
    return category

# Bin the data with missing category
df_notax['dpd_category'] = add_missing_category(df_notax['dpd'], dpd_bins, dpd_labels)
df_notax['dsf_category'] = add_missing_category(df_notax['dsf'], dsf_bins, dsf_labels)
df_notax['days_since_last_rpt_category'] = add_missing_category(df_notax['days_since_last_rpt'], days_since_last_rpt_bins, days_since_last_rpt_labels)
df_notax['precsn_score_category'] = add_missing_category(df_notax['precsn_score'], precsn_score_bins, precsn_score_labels)
df_notax['past_due_amt_category'] = add_missing_category(df_notax['past_due_amt'], past_due_amt_bins, past_due_amt_labels)

# Create bar plots
fig, axs = plt.subplots(5, 1, figsize=(10, 25))

df_notax.groupby('dpd_category')['pay'].mean().reindex(dpd_labels + ['Missing']).plot(kind='bar', ax=axs[0], color='skyblue', edgecolor='black')
axs[0].set_title('Pay by Days Past Due (DPD)')
axs[0].set_xlabel('DPD Category')
axs[0].set_ylabel('Propensity to Pay')

df_notax.groupby('dsf_category')['pay'].mean().reindex(dsf_labels + ['Missing']).plot(kind='bar', ax=axs[1], color='lightgreen', edgecolor='black')
axs[1].set_title('Pay by Days Since Finalization (DSF)')
axs[1].set_xlabel('DSF Category')
axs[1].set_ylabel('Propensity to Pay')

df_notax.groupby('days_since_last_rpt_category')['pay'].mean().reindex(days_since_last_rpt_labels + ['Missing']).plot(kind='bar', ax=axs[2], color='coral', edgecolor='black')
axs[2].set_title('Pay by Days Since Last Reporting')
axs[2].set_xlabel('Days Since Last Reporting')
axs[2].set_ylabel('Propensity to Pay')

df_notax.groupby('precsn_score_category')['pay'].mean().reindex(precsn_score_labels + ['Missing']).plot(kind='bar', ax=axs[3], color='purple', edgecolor='black')
axs[3].set_title('Pay by FICO Score')
axs[3].set_xlabel('FICO Score Category')
axs[3].set_ylabel('Propensity to Pay')

df_notax.groupby('past_due_amt_category')['pay'].mean().reindex(past_due_amt_labels + ['Missing']).plot(kind='bar', ax=axs[4], color='orange', edgecolor='black')
axs[4].set_title('Pay by Past Due Amount')
axs[4].set_xlabel('Past Due Amount Category')
axs[4].set_ylabel('Propensity to Pay')

plt.tight_layout()
plt.show()

import pandas as pd

# Assuming you have a DataFrame named vint containing your data
vint['tgt_dt'] = pd.to_datetime(vint['dt'], format='%d%b%Y')  # Convert 'dt' column to datetime

dpd_threshold = 46
conditions = [(vint[f'dpd47'] <= dpd_threshold),
              (vint[f'dpd48'] <= dpd_threshold),
              (vint[f'dpd49'] <= dpd_threshold),
              (vint[f'dpd50'] <= dpd_threshold),
              (vint[f'dpd51'] <= dpd_threshold),
              (vint[f'dpd52'] <= dpd_threshold),
              (vint[f'dpd53'] <= dpd_threshold),
              (vint[f'dpd54'] <= dpd_threshold),
              (vint[f'dpd55'] <= dpd_threshold),
              (vint[f'dpd56'] <= dpd_threshold),
              (vint[f'dpd57'] <= dpd_threshold),
              (vint[f'dpd58'] <= dpd_threshold),
              (vint[f'dpd59'] <= dpd_threshold),
              (vint[f'dpd60'] <= dpd_threshold)]

# Corresponding days to add to 'tgt_dt'
days_to_add = [i + 1 for i in range(14)]

for condition, days in zip(conditions, days_to_add):
    vint.loc[condition & pd.isnull(vint['tgt_dt']), 'tgt_dt'] = vint['dt'] + pd.DateOffset(days=days)

# If 'dt' column is no longer needed, you can drop it using:
# vint.drop(columns=['dt'], inplace=True)

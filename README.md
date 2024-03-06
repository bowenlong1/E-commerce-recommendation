import pandas as pd

# Assuming you have a DataFrame named df containing your data
df['tgt_dt'] = pd.to_datetime(df['dt'], format='%d%b%Y')  # Convert 'dt' column to datetime

dpd_threshold = 46
conditions = [(df[f'dpd47'] <= dpd_threshold),
              (df[f'dpd48'] <= dpd_threshold),
              (df[f'dpd49'] <= dpd_threshold),
              (df[f'dpd50'] <= dpd_threshold),
              (df[f'dpd51'] <= dpd_threshold),
              (df[f'dpd52'] <= dpd_threshold),
              (df[f'dpd53'] <= dpd_threshold),
              (df[f'dpd54'] <= dpd_threshold),
              (df[f'dpd55'] <= dpd_threshold),
              (df[f'dpd56'] <= dpd_threshold),
              (df[f'dpd57'] <= dpd_threshold),
              (df[f'dpd58'] <= dpd_threshold),
              (df[f'dpd59'] <= dpd_threshold),
              (df[f'dpd60'] <= dpd_threshold)]

# Corresponding days to add to 'tgt_dt'
days_to_add = [i + 1 for i in range(14)]

for condition, days in zip(conditions, days_to_add):
    df.loc[condition & pd.isnull(df['tgt_dt']), 'tgt_dt'] = df['dt'] + pd.DateOffset(days=days)

# If 'dt' column is no longer needed, you can drop it using:
# df.drop(columns=['dt'], inplace=True)



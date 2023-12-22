def create_cat_column(df, column, breakpoints, col_name):
    df[col_name] = 'missing'
    for i in range(len(breakpoints) - 1):
        lower_bound, upper_bound = breakpoints[i], breakpoints[i + 1]
        
        # Convert the column to numeric, handling errors to set NaN for non-convertible values
        df[column] = pd.to_numeric(df[column], errors='coerce')
        
        mask = (df[column] >= lower_bound) & (df[column] < upper_bound)
        df.loc[mask, col_name] = f'[{lower_bound}, {upper_bound})'

    df.loc[df[column].isna(),col_name] = 'missing'
    return df

breakpoints_dpd_6_mnth_max = [float('-inf'), 4, 15, 30, 45, 60, 75, float('inf')]
breakpoints_dpd_5_mnth_max = [float('-inf'), 4, 15, 30, 45, 60, 75, float('inf')]
breakpoints_dpd_2_mnth_max = [float('-inf'), 4, 15, 30, 45, 60, 75, float('inf')]

acct = create_cat_column(acct, 'dpd_6_mnth_max', breakpoints_dpd_6_mnth_max, 'cat_dpd_6_mnth_max')
acct = create_cat_column(acct, 'dpd_5_mnth_max', breakpoints_dpd_5_mnth_max, 'cat_dpd_5_mnth_max')
acct = create_cat_column(acct, 'dpd_2_mnth_max', breakpoints_dpd_2_mnth_max, 'cat_dpd_2_mnth_max')

df = acct[acct.day_key!=20231115]


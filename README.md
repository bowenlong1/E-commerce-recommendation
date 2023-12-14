def create_cat_column(df, column, breakpoints, col_name):
    df[col_name] = 'missing'
    for i in range(len(breakpoints) - 1):
        lower_bound, upper_bound = breakpoints[i], breakpoints[i + 1]
        mask = (df[column] >= lower_bound) & (df[column] < upper_bound)
        df.loc[mask, col_name] = f'[{lower_bound}, {upper_bound})'
    return df

# Apply the function to create categorical variables
breakpoints_freq_545_fnl = [float('-inf'), 2, 6, 10, float('inf')]
breakpoints_days_to_next_pmt = [float('-inf'), 7, 10, 14, 17, float('inf')]
breakpoints_dpd_6_mnth_max = [float('-inf'), 4, 15, 30, 45, 60, 75, float('inf')]
breakpoints_dpd_5_mnth_max = [float('-inf'), 4, 15, 30, 45, 60, 75, float('inf')]
breakpoints_dpd_2_mnth_max = [float('-inf'), 4, 15, 30, 45, 60, 75, float('inf')]

hist = create_cat_column(hist, 'freq_545_fnl', breakpoints_freq_545_fnl, 'dq_cat_freq_545_fnl')
hist = create_cat_column(hist, 'days_to_next_pmt', breakpoints_days_to_next_pmt, 'dq_cat_days_to_next_pmt')
hist = create_cat_column(hist, 'dpd_6_mnth_max', breakpoints_dpd_6_mnth_max, 'dq_cat_dpd_6_mnth_max')
hist = create_cat_column(hist, 'dpd_5_mnth_max', breakpoints_dpd_5_mnth_max, 'dq_cat_dpd_5_mnth_max')
hist = create_cat_column(hist, 'dpd_2_mnth_max', breakpoints_dpd_2_mnth_max, 'dq_cat_dpd_2_mnth_max')



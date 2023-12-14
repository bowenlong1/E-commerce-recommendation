def create_cat_column(df, column, breakpoints, col_name):
    df[col_name] = 'missing'
    for i in range(len(breakpoints) - 1):
        lower_bound, upper_bound = breakpoints[i], breakpoints[i + 1]
        
        if isinstance(lower_bound, (int, float)) and isinstance(upper_bound, (int, float)):
            mask = (df[column] >= lower_bound) & (df[column] < upper_bound)
        else:
            mask = (df[column] == lower_bound) | (df[column] == upper_bound)

        df.loc[mask, col_name] = f'[{lower_bound}, {upper_bound})'
    return df

# Apply the function to create categorical variables
hist = create_cat_column(hist, 'freq_545_fnl', breakpoints_freq_545_fnl, 'cat_freq_545_fnl')
hist = create_cat_column(hist, 'days_to_next_pmt', breakpoints_days_to_next_pmt, 'cat_days_to_next_pmt')
hist = create_cat_column(hist, 'dpd_6_mnth_max', breakpoints_dpd_6_mnth_max, 'cat_dpd_6_mnth_max')
hist = create_cat_column(hist, 'dpd_5_mnth_max', breakpoints_dpd_5_mnth_max, 'cat_dpd_5_mnth_max')
hist = create_cat_column(hist, 'dpd_2_mnth_max', breakpoints_dpd_2_mnth_max, 'cat_dpd_2_mnth_max')



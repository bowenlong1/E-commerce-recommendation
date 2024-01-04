df['dpd'] = df['dpd'].replace({None: np.nan}).astype('float64').astype(pd.Int64Dtype())


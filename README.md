vint.loc[condition & pd.isnull(vint['tgt_dt']), 'tgt_dt'] = vint['dt'][condition & pd.isnull(vint['tgt_dt'])] + pd.DateOffset(days=days)

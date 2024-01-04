acct = df[(df['day_key'] != 20231115) & ((df['random_num'] >= 0) & (df['random_num'] <= 19) | ((df['random_num'] >= 50) & (df['random_num'] <= 99)))]



freq_545_fnl	['missing', 'low', 2, 6, 10, 'high']
days_to_next_pmt	['missing', 'low', 7, 10, 14, 17, 'high']
dpd_6_mnth_max	['missing', 'low', 4, 15, 30, 45, 60, 75, 'high']
dpd_5_mnth_max	['missing', 'low', 4, 15, 30, 45, 60, 75, 'high']
dpd_2_mnth_max	['missing', 'low', 4, 15, 30, 45, 60, 75, 'high']

hist['dq_cat'] = 'missing'
hist.loc[(~hist.freq_545_fnl.isna())&(hist.freq_545_fnl<2), 'dq_cat'] = '[low, 2)'
hist.loc[(hist.freq_545_fnl>=2)&(hist.freq_545_fnl<6), 'dq_cat'] = '[2, 6)'
hist.loc[(hist.freq_545_fnl>=6)&(hist.freq_545_fnl<10), 'dq_cat'] = '[6, 10)'
hist.loc[(hist.freq_545_fnl>=10), 'dq_cat'] = '[10, high)'

![image](https://github.com/bowenlong1/E-commerce-recommendation/assets/38050947/7005fcb3-880d-4975-80fb-303e30cd15e4)


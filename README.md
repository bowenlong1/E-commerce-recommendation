
    "precsn_score": 'float64',
    "dpd_5week": 'int64',
    "cur_apr": 'float64',
    "dpd_2_mnth_max": 'int64',
    "total_pmt_1m": 'float64',
    "cur_mnth_bill": 'float64'
})

TypeError: int() argument must be a string, a bytes-like object or a real number, not 'NoneType'
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
File <command-708663598832660>, line 1
----> 1 df[fet_lst_up] = df[fet_lst_up].astype({
      2     "dpd_3week": 'int64',
      3     "since_last_pmt_day_qty": 'int64',
      4     "days_to_next_pmt": 'int64',
      5     "total_pmt_3m": 'float64',
      6     "past_due_amt": 'float64',
      7     "dpd_7week": 'int64',
      8     "days_since_last_ext": 'int64',
      9     "days_since_ptp": 'int64',
     10     "days_in_call_queue_qty": 'int64',
     11     "dif_curdpd_maxdpd": 'float64',
     12     "days_since_last_contact": 'int64',
     13     "pti": 'float64',
     14     "last_pmt_amt": 'float64',
     15     "freq_545_fnl": 'float64',
     16     "total_pmt_1week": 'float64',
     17     "dpd_6_mnth_max": 'float64',
     18     "finc_amt": 'float64',

Hi Anil,
Per our conversation, I validated the new fields added for prop_tax_due, term_process_day_key, hld_dt_ind and bkrpt_status_cd using Jan 31st portfolio (portfolio day_key is 20240131) by comparing them with SAS DW. There are some mismatches:

There are 90 accounts in databricks have values for prop_tax_due, but in SAS DW it shows NULL.
There are 2510 accounts in databricks are missing values from term_process_day_key, hld_dt_ind and bkrpt_status_cd, but in SAS DW they have values.

Attached are the details by field. Please let me know if you have any questions.

Thanks,


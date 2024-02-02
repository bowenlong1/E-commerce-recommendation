## check acct
acct = spark.sql("""SELECT acct_nbr, partial_acct_nbr, acct_key, day_key, PROP_TAX_DUE_AMT FROM prsnt_svcng.acct_status_fact where day_key = '20240131' """)
acct.createOrReplaceTempView("acct") 

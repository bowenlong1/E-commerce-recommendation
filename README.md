day_key_variable = '20240131'  # Your variable representing the day key

# Using f-strings
acct = spark.sql(f"""
    SELECT acct_nbr, partial_acct_nbr, acct_key, day_key, PROP_TAX_DUE_AMT 
    FROM prsnt_svcng.acct_status_fact 
    WHERE day_key = '{day_key_variable}' 
""")
acct.createOrReplaceTempView("acct")


day_key_variable = '20240131'  # Your variable representing the day key

# Using Python string formatting
acct = spark.sql("""
    SELECT acct_nbr, partial_acct_nbr, acct_key, day_key, PROP_TAX_DUE_AMT 
    FROM prsnt_svcng.acct_status_fact 
    WHERE day_key = '{}' 
""".format(day_key_variable))
acct.createOrReplaceTempView("acct")

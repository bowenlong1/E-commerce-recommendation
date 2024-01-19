target = spark.sql("""
    SELECT distinct a.*, 
                    b.day_key AS day7, 
                    b.days_delinq_qty AS dpd7,
                    c.days_delinq_qty AS dpd15
    FROM mlops_work.contact_strategy_46_60_samp3_archive a
    LEFT JOIN prsnt_svcng.acct_status_fact b
    ON a.loan_acct_nbr = b.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 7) = to_date(cast(b.day_key as string), 'yyyyMMdd')
    LEFT JOIN prsnt_svcng.acct_status_fact c
    ON a.loan_acct_nbr = c.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 15) = to_date(cast(c.day_key as string), 'yyyyMMdd')
""")

# Save the result as a new table
target.createOrReplaceTempView("target")


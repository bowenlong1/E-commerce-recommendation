apr1 = spark.sql("""
    SELECT  a.*, 
                    b.days_delinq_qty AS dpd7,
                    c.days_delinq_qty AS dpd16
    FROM apr a
    LEFT JOIN prsnt_svcng.acct_status_fact b
    ON a.partial_acct_nbr = b.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 7) = to_date(cast(b.day_key as string), 'yyyyMMdd')
    LEFT JOIN prsnt_svcng.acct_status_fact c
    ON a.partial_acct_nbr = c.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 16) = to_date(cast(c.day_key as string), 'yyyyMMdd')
""")

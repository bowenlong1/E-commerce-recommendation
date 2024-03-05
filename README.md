target = spark.sql("""
    SELECT distinct a.*, 
                    a1.days_delinq_qty as dpd1,
a2.days_delinq_qty as dpd2,
a3.days_delinq_qty as dpd3,
a4.days_delinq_qty as dpd4,
a5.days_delinq_qty as dpd5,
a6.days_delinq_qty as dpd6,
a7.days_delinq_qty as dpd7,
a8.days_delinq_qty as dpd8,
a9.days_delinq_qty as dpd9,
a10.days_delinq_qty as dpd10,
a11.days_delinq_qty as dpd11,
a12.days_delinq_qty as dpd12,
a13.days_delinq_qty as dpd13,
a14.days_delinq_qty as dpd14,
a15.days_delinq_qty as dpd15,
a16.days_delinq_qty as dpd16,
a17.days_delinq_qty as dpd17,
a18.days_delinq_qty as dpd18,
a19.days_delinq_qty as dpd19,
a20.days_delinq_qty as dpd20,
a21.days_delinq_qty as dpd21,
a22.days_delinq_qty as dpd22,
a23.days_delinq_qty as dpd23,
a24.days_delinq_qty as dpd24,
a25.days_delinq_qty as dpd25,
a26.days_delinq_qty as dpd26,
a27.days_delinq_qty as dpd27,
a28.days_delinq_qty as dpd28,
a29.days_delinq_qty as dpd29,
a30.days_delinq_qty as dpd30,
a31.days_delinq_qty as dpd31,
a32.days_delinq_qty as dpd32,
a33.days_delinq_qty as dpd33,
a34.days_delinq_qty as dpd34,
a35.days_delinq_qty as dpd35,
a36.days_delinq_qty as dpd36,
a37.days_delinq_qty as dpd37,
a38.days_delinq_qty as dpd38,
a39.days_delinq_qty as dpd39,
a40.days_delinq_qty as dpd40,
a41.days_delinq_qty as dpd41,
a42.days_delinq_qty as dpd42,
a43.days_delinq_qty as dpd43,
a44.days_delinq_qty as dpd44,
a45.days_delinq_qty as dpd45
FROM mlops_work.contact_strategy_46_60_samp3_archive a
    LEFT JOIN prsnt_svcng.acct_status_fact a1
    ON a.loan_acct_nbr = a1.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 1) = to_date(cast(a1.day_key as string), 'yyyyMMdd')
    LEFT JOIN prsnt_svcng.acct_status_fact a2
    ON a.loan_acct_nbr = a2.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 2) = to_date(cast(a2.day_key as string), 'yyyyMMdd')
""")

# Save the result as a new table
target.createOrReplaceTempView("target")

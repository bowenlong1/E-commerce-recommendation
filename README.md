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
    LEFT JOIN prsnt_svcng.acct_status_fact a3
    ON a.loan_acct_nbr = a3.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 3) = to_date(cast(a3.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd4 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a4
    ON a.loan_acct_nbr = a4.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 4) = to_date(cast(a4.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd5 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a5
    ON a.loan_acct_nbr = a5.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 5) = to_date(cast(a5.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd6 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a6
    ON a.loan_acct_nbr = a6.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 6) = to_date(cast(a6.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd7 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a7
    ON a.loan_acct_nbr = a7.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 7) = to_date(cast(a7.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd8 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a8
    ON a.loan_acct_nbr = a8.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 8) = to_date(cast(a8.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd9 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a9
    ON a.loan_acct_nbr = a9.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 9) = to_date(cast(a9.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd10 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a10
    ON a.loan_acct_nbr = a10.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 10) = to_date(cast(a10.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd11 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a11
    ON a.loan_acct_nbr = a11.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 11) = to_date(cast(a11.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd12 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a12
    ON a.loan_acct_nbr = a12.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 12) = to_date(cast(a12.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd13 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a13
    ON a.loan_acct_nbr = a13.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 13) = to_date(cast(a13.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd14 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a14
    ON a.loan_acct_nbr = a14.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 14) = to_date(cast(a14.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd15 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a15
    ON a.loan_acct_nbr = a15.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 15) = to_date(cast(a15.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd16 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a16
    ON a.loan_acct_nbr = a16.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 16) = to_date(cast(a16.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd17 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a17
    ON a.loan_acct_nbr = a17.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 17) = to_date(cast(a17.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd18 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a18
    ON a.loan_acct_nbr = a18.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 18) = to_date(cast(a18.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd19 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a19
    ON a.loan_acct_nbr = a19.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 19) = to_date(cast(a19.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd20 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a20
    ON a.loan_acct_nbr = a20.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 20) = to_date(cast(a20.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd21 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a21
    ON a.loan_acct_nbr = a21.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 21) = to_date(cast(a21.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd22 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a22
    ON a.loan_acct_nbr = a22.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 22) = to_date(cast(a22.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd23 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a23
    ON a.loan_acct_nbr = a23.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 23) = to_date(cast(a23.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd24 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a24
    ON a.loan_acct_nbr = a24.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 24) = to_date(cast(a24.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd25 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a25
    ON a.loan_acct_nbr = a25.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 25) = to_date(cast(a25.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd26 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a26
    ON a.loan_acct_nbr = a26.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 26) = to_date(cast(a26.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd27 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a27
    ON a.loan_acct_nbr = a27.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 27) = to_date(cast(a27.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd28 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a28
    ON a.loan_acct_nbr = a28.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 28) = to_date(cast(a28.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd29 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a29
    ON a.loan_acct_nbr = a29.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 29) = to_date(cast(a29.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd30 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a30
    ON a.loan_acct_nbr = a30.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 30) = to_date(cast(a30.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd31 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a31
    ON a.loan_acct_nbr = a31.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 31) = to_date(cast(a31.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd32 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a32
    ON a.loan_acct_nbr = a32.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 32) = to_date(cast(a32.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd33 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a33
    ON a.loan_acct_nbr = a33.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 33) = to_date(cast(a33.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd34 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a34
    ON a.loan_acct_nbr = a34.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 34) = to_date(cast(a34.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd35 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a35
    ON a.loan_acct_nbr = a35.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 35) = to_date(cast(a35.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd36 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a36
    ON a.loan_acct_nbr = a36.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 36) = to_date(cast(a36.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd37 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a37
    ON a.loan_acct_nbr = a37.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 37) = to_date(cast(a37.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd38 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a38
    ON a.loan_acct_nbr = a38.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 38) = to_date(cast(a38.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd39 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a39
    ON a.loan_acct_nbr = a39.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 39) = to_date(cast(a39.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd40 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a40
    ON a.loan_acct_nbr = a40.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 40) = to_date(cast(a40.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd41 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a41
    ON a.loan_acct_nbr = a41.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 41) = to_date(cast(a41.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd42 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a42
    ON a.loan_acct_nbr = a42.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 42) = to_date(cast(a42.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd43 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a43
    ON a.loan_acct_nbr = a43.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 43) = to_date(cast(a43.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd44 to dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a44
    ON a.loan_acct_nbr = a44.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 44) = to_date(cast(a44.day_key as string), 'yyyyMMdd')
    -- continue left joins for dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact a45
    ON a.loan_acct_nbr = a45.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 45) = to_date(cast(a45.day_key as string), 'yyyyMMdd')
""")
# Save the result as a new table
target.createOrReplaceTempView("target")

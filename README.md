# Execute the query
apr_res = spark.sql(sql_query)

ParseException: 
[PARSE_SYNTAX_ERROR] Syntax error at or near 'JOIN'.(line 2, pos 9)

== SQL ==
SELECT a.*
    LEFT JOIN prsnt_svcng.acct_status_fact dpd1
---------^^^
    ON a.partial_acct_nbr = dpd1.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 1) = to_date(cast(dpd1.day_key as string), 'yyyyMMdd')
    , dpd1.days_delinq_qty AS dpd1
    LEFT JOIN prsnt_svcng.acct_status_fact dpd2
    ON a.partial_acct_nbr = dpd2.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 2) = to_date(cast(dpd2.day_key as string), 'yyyyMMdd')
    , dpd2.days_delinq_qty AS dpd2
    LEFT JOIN prsnt_svcng.acct_status_fact dpd3
    ON a.partial_acct_nbr = dpd3.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 3) = to_date(cast(dpd3.day_key as string), 'yyyyMMdd')
    , dpd3.days_delinq_qty AS dpd3
    LEFT JOIN prsnt_svcng.acct_status_fact dpd4
    ON a.partial_acct_nbr = dpd4.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 4) = to_date(cast(dpd4.day_key as string), 'yyyyMMdd')
    , dpd4.days_delinq_qty AS dpd4
    LEFT JOIN prsnt_svcng.acct_status_fact dpd5
    ON a.partial_acct_nbr = dpd5.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 5) = to_date(cast(dpd5.day_key as string), 'yyyyMMdd')
    , dpd5.days_delinq_qty AS dpd5
    LEFT JOIN prsnt_svcng.acct_status_fact dpd6
    ON a.partial_acct_nbr = dpd6.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 6) = to_date(cast(dpd6.day_key as string), 'yyyyMMdd')
    , dpd6.days_delinq_qty AS dpd6
    LEFT JOIN prsnt_svcng.acct_status_fact dpd7
    ON a.partial_acct_nbr = dpd7.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 7) = to_date(cast(dpd7.day_key as string), 'yyyyMMdd')
    , dpd7.days_delinq_qty AS dpd7
    LEFT JOIN prsnt_svcng.acct_status_fact dpd8
    ON a.partial_acct_nbr = dpd8.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 8) = to_date(cast(dpd8.day_key as string), 'yyyyMMdd')
    , dpd8.days_delinq_qty AS dpd8
    LEFT JOIN prsnt_svcng.acct_status_fact dpd9
    ON a.partial_acct_nbr = dpd9.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 9) = to_date(cast(dpd9.day_key as string), 'yyyyMMdd')
    , dpd9.days_delinq_qty AS dpd9
    LEFT JOIN prsnt_svcng.acct_status_fact dpd10
    ON a.partial_acct_nbr = dpd10.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 10) = to_date(cast(dpd10.day_key as string), 'yyyyMMdd')
    , dpd10.days_delinq_qty AS dpd10
    LEFT JOIN prsnt_svcng.acct_status_fact dpd11
    ON a.partial_acct_nbr = dpd11.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 11) = to_date(cast(dpd11.day_key as string), 'yyyyMMdd')
    , dpd11.days_delinq_qty AS dpd11
    LEFT JOIN prsnt_svcng.acct_status_fact dpd12
    ON a.partial_acct_nbr = dpd12.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 12) = to_date(cast(dpd12.day_key as string), 'yyyyMMdd')
    , dpd12.days_delinq_qty AS dpd12
    LEFT JOIN prsnt_svcng.acct_status_fact dpd13
    ON a.partial_acct_nbr = dpd13.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 13) = to_date(cast(dpd13.day_key as string), 'yyyyMMdd')
    , dpd13.days_delinq_qty AS dpd13
    LEFT JOIN prsnt_svcng.acct_status_fact dpd14
    ON a.partial_acct_nbr = dpd14.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 14) = to_date(cast(dpd14.day_key as string), 'yyyyMMdd')
    , dpd14.days_delinq_qty AS dpd14
    LEFT JOIN prsnt_svcng.acct_status_fact dpd15
    ON a.partial_acct_nbr = dpd15.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 15) = to_date(cast(dpd15.day_key as string), 'yyyyMMdd')
    , dpd15.days_delinq_qty AS dpd15
    LEFT JOIN prsnt_svcng.acct_status_fact dpd16
    ON a.partial_acct_nbr = dpd16.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 16) = to_date(cast(dpd16.day_key as string), 'yyyyMMdd')
    , dpd16.days_delinq_qty AS dpd16
    LEFT JOIN prsnt_svcng.acct_status_fact dpd17
    ON a.partial_acct_nbr = dpd17.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 17) = to_date(cast(dpd17.day_key as string), 'yyyyMMdd')
    , dpd17.days_delinq_qty AS dpd17
    LEFT JOIN prsnt_svcng.acct_status_fact dpd18
    ON a.partial_acct_nbr = dpd18.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 18) = to_date(cast(dpd18.day_key as string), 'yyyyMMdd')
    , dpd18.days_delinq_qty AS dpd18
    LEFT JOIN prsnt_svcng.acct_status_fact dpd19
    ON a.partial_acct_nbr = dpd19.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 19) = to_date(cast(dpd19.day_key as string), 'yyyyMMdd')
    , dpd19.days_delinq_qty AS dpd19
    LEFT JOIN prsnt_svcng.acct_status_fact dpd20
    ON a.partial_acct_nbr = dpd20.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 20) = to_date(cast(dpd20.day_key as string), 'yyyyMMdd')
    , dpd20.days_delinq_qty AS dpd20
    LEFT JOIN prsnt_svcng.acct_status_fact dpd21
    ON a.partial_acct_nbr = dpd21.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 21) = to_date(cast(dpd21.day_key as string), 'yyyyMMdd')
    , dpd21.days_delinq_qty AS dpd21
    LEFT JOIN prsnt_svcng.acct_status_fact dpd22
    ON a.partial_acct_nbr = dpd22.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 22) = to_date(cast(dpd22.day_key as string), 'yyyyMMdd')
    , dpd22.days_delinq_qty AS dpd22
    LEFT JOIN prsnt_svcng.acct_status_fact dpd23
    ON a.partial_acct_nbr = dpd23.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 23) = to_date(cast(dpd23.day_key as string), 'yyyyMMdd')
    , dpd23.days_delinq_qty AS dpd23
    LEFT JOIN prsnt_svcng.acct_status_fact dpd24
    ON a.partial_acct_nbr = dpd24.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 24) = to_date(cast(dpd24.day_key as string), 'yyyyMMdd')
    , dpd24.days_delinq_qty AS dpd24
    LEFT JOIN prsnt_svcng.acct_status_fact dpd25
    ON a.partial_acct_nbr = dpd25.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 25) = to_date(cast(dpd25.day_key as string), 'yyyyMMdd')
    , dpd25.days_delinq_qty AS dpd25
    LEFT JOIN prsnt_svcng.acct_status_fact dpd26
    ON a.partial_acct_nbr = dpd26.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 26) = to_date(cast(dpd26.day_key as string), 'yyyyMMdd')
    , dpd26.days_delinq_qty AS dpd26
    LEFT JOIN prsnt_svcng.acct_status_fact dpd27
    ON a.partial_acct_nbr = dpd27.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 27) = to_date(cast(dpd27.day_key as string), 'yyyyMMdd')
    , dpd27.days_delinq_qty AS dpd27
    LEFT JOIN prsnt_svcng.acct_status_fact dpd28
    ON a.partial_acct_nbr = dpd28.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 28) = to_date(cast(dpd28.day_key as string), 'yyyyMMdd')
    , dpd28.days_delinq_qty AS dpd28
    LEFT JOIN prsnt_svcng.acct_status_fact dpd29
    ON a.partial_acct_nbr = dpd29.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 29) = to_date(cast(dpd29.day_key as string), 'yyyyMMdd')
    , dpd29.days_delinq_qty AS dpd29
    LEFT JOIN prsnt_svcng.acct_status_fact dpd30
    ON a.partial_acct_nbr = dpd30.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 30) = to_date(cast(dpd30.day_key as string), 'yyyyMMdd')
    , dpd30.days_delinq_qty AS dpd30
    LEFT JOIN prsnt_svcng.acct_status_fact dpd31
    ON a.partial_acct_nbr = dpd31.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 31) = to_date(cast(dpd31.day_key as string), 'yyyyMMdd')
    , dpd31.days_delinq_qty AS dpd31
    LEFT JOIN prsnt_svcng.acct_status_fact dpd32
    ON a.partial_acct_nbr = dpd32.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 32) = to_date(cast(dpd32.day_key as string), 'yyyyMMdd')
    , dpd32.days_delinq_qty AS dpd32
    LEFT JOIN prsnt_svcng.acct_status_fact dpd33
    ON a.partial_acct_nbr = dpd33.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 33) = to_date(cast(dpd33.day_key as string), 'yyyyMMdd')
    , dpd33.days_delinq_qty AS dpd33
    LEFT JOIN prsnt_svcng.acct_status_fact dpd34
    ON a.partial_acct_nbr = dpd34.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 34) = to_date(cast(dpd34.day_key as string), 'yyyyMMdd')
    , dpd34.days_delinq_qty AS dpd34
    LEFT JOIN prsnt_svcng.acct_status_fact dpd35
    ON a.partial_acct_nbr = dpd35.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 35) = to_date(cast(dpd35.day_key as string), 'yyyyMMdd')
    , dpd35.days_delinq_qty AS dpd35
    LEFT JOIN prsnt_svcng.acct_status_fact dpd36
    ON a.partial_acct_nbr = dpd36.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 36) = to_date(cast(dpd36.day_key as string), 'yyyyMMdd')
    , dpd36.days_delinq_qty AS dpd36
    LEFT JOIN prsnt_svcng.acct_status_fact dpd37
    ON a.partial_acct_nbr = dpd37.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 37) = to_date(cast(dpd37.day_key as string), 'yyyyMMdd')
    , dpd37.days_delinq_qty AS dpd37
    LEFT JOIN prsnt_svcng.acct_status_fact dpd38
    ON a.partial_acct_nbr = dpd38.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 38) = to_date(cast(dpd38.day_key as string), 'yyyyMMdd')
    , dpd38.days_delinq_qty AS dpd38
    LEFT JOIN prsnt_svcng.acct_status_fact dpd39
    ON a.partial_acct_nbr = dpd39.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 39) = to_date(cast(dpd39.day_key as string), 'yyyyMMdd')
    , dpd39.days_delinq_qty AS dpd39
    LEFT JOIN prsnt_svcng.acct_status_fact dpd40
    ON a.partial_acct_nbr = dpd40.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 40) = to_date(cast(dpd40.day_key as string), 'yyyyMMdd')
    , dpd40.days_delinq_qty AS dpd40
    LEFT JOIN prsnt_svcng.acct_status_fact dpd41
    ON a.partial_acct_nbr = dpd41.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 41) = to_date(cast(dpd41.day_key as string), 'yyyyMMdd')
    , dpd41.days_delinq_qty AS dpd41
    LEFT JOIN prsnt_svcng.acct_status_fact dpd42
    ON a.partial_acct_nbr = dpd42.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 42) = to_date(cast(dpd42.day_key as string), 'yyyyMMdd')
    , dpd42.days_delinq_qty AS dpd42
    LEFT JOIN prsnt_svcng.acct_status_fact dpd43
    ON a.partial_acct_nbr = dpd43.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 43) = to_date(cast(dpd43.day_key as string), 'yyyyMMdd')
    , dpd43.days_delinq_qty AS dpd43
    LEFT JOIN prsnt_svcng.acct_status_fact dpd44
    ON a.partial_acct_nbr = dpd44.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 44) = to_date(cast(dpd44.day_key as string), 'yyyyMMdd')
    , dpd44.days_delinq_qty AS dpd44
    LEFT JOIN prsnt_svcng.acct_status_fact dpd45
    ON a.partial_acct_nbr = dpd45.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 45) = to_date(cast(dpd45.day_key as string), 'yyyyMMdd')
    , dpd45.days_delinq_qty AS dpd45
    LEFT JOIN prsnt_svcng.acct_status_fact dpd46
    ON a.partial_acct_nbr = dpd46.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 46) = to_date(cast(dpd46.day_key as string), 'yyyyMMdd')
    , dpd46.days_delinq_qty AS dpd46
    LEFT JOIN prsnt_svcng.acct_status_fact dpd47
    ON a.partial_acct_nbr = dpd47.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 47) = to_date(cast(dpd47.day_key as string), 'yyyyMMdd')
    , dpd47.days_delinq_qty AS dpd47
    LEFT JOIN prsnt_svcng.acct_status_fact dpd48
    ON a.partial_acct_nbr = dpd48.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 48) = to_date(cast(dpd48.day_key as string), 'yyyyMMdd')
    , dpd48.days_delinq_qty AS dpd48
    LEFT JOIN prsnt_svcng.acct_status_fact dpd49
    ON a.partial_acct_nbr = dpd49.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 49) = to_date(cast(dpd49.day_key as string), 'yyyyMMdd')
    , dpd49.days_delinq_qty AS dpd49
    LEFT JOIN prsnt_svcng.acct_status_fact dpd50
    ON a.partial_acct_nbr = dpd50.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 50) = to_date(cast(dpd50.day_key as string), 'yyyyMMdd')
    , dpd50.days_delinq_qty AS dpd50
    LEFT JOIN prsnt_svcng.acct_status_fact dpd51
    ON a.partial_acct_nbr = dpd51.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 51) = to_date(cast(dpd51.day_key as string), 'yyyyMMdd')
    , dpd51.days_delinq_qty AS dpd51
    LEFT JOIN prsnt_svcng.acct_status_fact dpd52
    ON a.partial_acct_nbr = dpd52.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 52) = to_date(cast(dpd52.day_key as string), 'yyyyMMdd')
    , dpd52.days_delinq_qty AS dpd52
    LEFT JOIN prsnt_svcng.acct_status_fact dpd53
    ON a.partial_acct_nbr = dpd53.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 53) = to_date(cast(dpd53.day_key as string), 'yyyyMMdd')
    , dpd53.days_delinq_qty AS dpd53
    LEFT JOIN prsnt_svcng.acct_status_fact dpd54
    ON a.partial_acct_nbr = dpd54.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 54) = to_date(cast(dpd54.day_key as string), 'yyyyMMdd')
    , dpd54.days_delinq_qty AS dpd54
    LEFT JOIN prsnt_svcng.acct_status_fact dpd55
    ON a.partial_acct_nbr = dpd55.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 55) = to_date(cast(dpd55.day_key as string), 'yyyyMMdd')
    , dpd55.days_delinq_qty AS dpd55
    LEFT JOIN prsnt_svcng.acct_status_fact dpd56
    ON a.partial_acct_nbr = dpd56.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 56) = to_date(cast(dpd56.day_key as string), 'yyyyMMdd')
    , dpd56.days_delinq_qty AS dpd56
    LEFT JOIN prsnt_svcng.acct_status_fact dpd57
    ON a.partial_acct_nbr = dpd57.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 57) = to_date(cast(dpd57.day_key as string), 'yyyyMMdd')
    , dpd57.days_delinq_qty AS dpd57
    LEFT JOIN prsnt_svcng.acct_status_fact dpd58
    ON a.partial_acct_nbr = dpd58.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 58) = to_date(cast(dpd58.day_key as string), 'yyyyMMdd')
    , dpd58.days_delinq_qty AS dpd58
    LEFT JOIN prsnt_svcng.acct_status_fact dpd59
    ON a.partial_acct_nbr = dpd59.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 59) = to_date(cast(dpd59.day_key as string), 'yyyyMMdd')
    , dpd59.days_delinq_qty AS dpd59
    LEFT JOIN prsnt_svcng.acct_status_fact dpd60
    ON a.partial_acct_nbr = dpd60.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 60) = to_date(cast(dpd60.day_key as string), 'yyyyMMdd')
    , dpd60.days_delinq_qty AS dpd60
    LEFT JOIN prsnt_svcng.acct_status_fact dpd61
    ON a.partial_acct_nbr = dpd61.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 61) = to_date(cast(dpd61.day_key as string), 'yyyyMMdd')
    , dpd61.days_delinq_qty AS dpd61
    LEFT JOIN prsnt_svcng.acct_status_fact dpd62
    ON a.partial_acct_nbr = dpd62.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 62) = to_date(cast(dpd62.day_key as string), 'yyyyMMdd')
    , dpd62.days_delinq_qty AS dpd62
    LEFT JOIN prsnt_svcng.acct_status_fact dpd63
    ON a.partial_acct_nbr = dpd63.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 63) = to_date(cast(dpd63.day_key as string), 'yyyyMMdd')
    , dpd63.days_delinq_qty AS dpd63
    LEFT JOIN prsnt_svcng.acct_status_fact dpd64
    ON a.partial_acct_nbr = dpd64.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 64) = to_date(cast(dpd64.day_key as string), 'yyyyMMdd')
    , dpd64.days_delinq_qty AS dpd64
    LEFT JOIN prsnt_svcng.acct_status_fact dpd65
    ON a.partial_acct_nbr = dpd65.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 65) = to_date(cast(dpd65.day_key as string), 'yyyyMMdd')
    , dpd65.days_delinq_qty AS dpd65
    LEFT JOIN prsnt_svcng.acct_status_fact dpd66
    ON a.partial_acct_nbr = dpd66.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 66) = to_date(cast(dpd66.day_key as string), 'yyyyMMdd')
    , dpd66.days_delinq_qty AS dpd66
    LEFT JOIN prsnt_svcng.acct_status_fact dpd67
    ON a.partial_acct_nbr = dpd67.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 67) = to_date(cast(dpd67.day_key as string), 'yyyyMMdd')
    , dpd67.days_delinq_qty AS dpd67
    LEFT JOIN prsnt_svcng.acct_status_fact dpd68
    ON a.partial_acct_nbr = dpd68.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 68) = to_date(cast(dpd68.day_key as string), 'yyyyMMdd')
    , dpd68.days_delinq_qty AS dpd68
    LEFT JOIN prsnt_svcng.acct_status_fact dpd69
    ON a.partial_acct_nbr = dpd69.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 69) = to_date(cast(dpd69.day_key as string), 'yyyyMMdd')
    , dpd69.days_delinq_qty AS dpd69
    LEFT JOIN prsnt_svcng.acct_status_fact dpd70
    ON a.partial_acct_nbr = dpd70.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 70) = to_date(cast(dpd70.day_key as string), 'yyyyMMdd')
    , dpd70.days_delinq_qty AS dpd70
    LEFT JOIN prsnt_svcng.acct_status_fact dpd71
    ON a.partial_acct_nbr = dpd71.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 71) = to_date(cast(dpd71.day_key as string), 'yyyyMMdd')
    , dpd71.days_delinq_qty AS dpd71
    LEFT JOIN prsnt_svcng.acct_status_fact dpd72
    ON a.partial_acct_nbr = dpd72.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 72) = to_date(cast(dpd72.day_key as string), 'yyyyMMdd')
    , dpd72.days_delinq_qty AS dpd72
    LEFT JOIN prsnt_svcng.acct_status_fact dpd73
    ON a.partial_acct_nbr = dpd73.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 73) = to_date(cast(dpd73.day_key as string), 'yyyyMMdd')
    , dpd73.days_delinq_qty AS dpd73
    LEFT JOIN prsnt_svcng.acct_status_fact dpd74
    ON a.partial_acct_nbr = dpd74.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 74) = to_date(cast(dpd74.day_key as string), 'yyyyMMdd')
    , dpd74.days_delinq_qty AS dpd74
    LEFT JOIN prsnt_svcng.acct_status_fact dpd75
    ON a.partial_acct_nbr = dpd75.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 75) = to_date(cast(dpd75.day_key as string), 'yyyyMMdd')
    , dpd75.days_delinq_qty AS dpd75
    LEFT JOIN prsnt_svcng.acct_status_fact dpd76
    ON a.partial_acct_nbr = dpd76.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 76) = to_date(cast(dpd76.day_key as string), 'yyyyMMdd')
    , dpd76.days_delinq_qty AS dpd76
    LEFT JOIN prsnt_svcng.acct_status_fact dpd77
    ON a.partial_acct_nbr = dpd77.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 77) = to_date(cast(dpd77.day_key as string), 'yyyyMMdd')
    , dpd77.days_delinq_qty AS dpd77
    LEFT JOIN prsnt_svcng.acct_status_fact dpd78
    ON a.partial_acct_nbr = dpd78.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 78) = to_date(cast(dpd78.day_key as string), 'yyyyMMdd')
    , dpd78.days_delinq_qty AS dpd78
    LEFT JOIN prsnt_svcng.acct_status_fact dpd79
    ON a.partial_acct_nbr = dpd79.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 79) = to_date(cast(dpd79.day_key as string), 'yyyyMMdd')
    , dpd79.days_delinq_qty AS dpd79
    LEFT JOIN prsnt_svcng.acct_status_fact dpd80
    ON a.partial_acct_nbr = dpd80.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 80) = to_date(cast(dpd80.day_key as string), 'yyyyMMdd')
    , dpd80.days_delinq_qty AS dpd80
    LEFT JOIN prsnt_svcng.acct_status_fact dpd81
    ON a.partial_acct_nbr = dpd81.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 81) = to_date(cast(dpd81.day_key as string), 'yyyyMMdd')
    , dpd81.days_delinq_qty AS dpd81
    LEFT JOIN prsnt_svcng.acct_status_fact dpd82
    ON a.partial_acct_nbr = dpd82.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 82) = to_date(cast(dpd82.day_key as string), 'yyyyMMdd')
    , dpd82.days_delinq_qty AS dpd82
    LEFT JOIN prsnt_svcng.acct_status_fact dpd83
    ON a.partial_acct_nbr = dpd83.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 83) = to_date(cast(dpd83.day_key as string), 'yyyyMMdd')
    , dpd83.days_delinq_qty AS dpd83
    LEFT JOIN prsnt_svcng.acct_status_fact dpd84
    ON a.partial_acct_nbr = dpd84.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 84) = to_date(cast(dpd84.day_key as string), 'yyyyMMdd')
    , dpd84.days_delinq_qty AS dpd84
    LEFT JOIN prsnt_svcng.acct_status_fact dpd85
    ON a.partial_acct_nbr = dpd85.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 85) = to_date(cast(dpd85.day_key as string), 'yyyyMMdd')
    , dpd85.days_delinq_qty AS dpd85
    LEFT JOIN prsnt_svcng.acct_status_fact dpd86
    ON a.partial_acct_nbr = dpd86.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 86) = to_date(cast(dpd86.day_key as string), 'yyyyMMdd')
    , dpd86.days_delinq_qty AS dpd86
    LEFT JOIN prsnt_svcng.acct_status_fact dpd87
    ON a.partial_acct_nbr = dpd87.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 87) = to_date(cast(dpd87.day_key as string), 'yyyyMMdd')
    , dpd87.days_delinq_qty AS dpd87
    LEFT JOIN prsnt_svcng.acct_status_fact dpd88
    ON a.partial_acct_nbr = dpd88.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 88) = to_date(cast(dpd88.day_key as string), 'yyyyMMdd')
    , dpd88.days_delinq_qty AS dpd88
    LEFT JOIN prsnt_svcng.acct_status_fact dpd89
    ON a.partial_acct_nbr = dpd89.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 89) = to_date(cast(dpd89.day_key as string), 'yyyyMMdd')
    , dpd89.days_delinq_qty AS dpd89
    LEFT JOIN prsnt_svcng.acct_status_fact dpd90
    ON a.partial_acct_nbr = dpd90.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 90) = to_date(cast(dpd90.day_key as string), 'yyyyMMdd')
    , dpd90.days_delinq_qty AS dpd90
    LEFT JOIN prsnt_svcng.acct_status_fact dpd91
    ON a.partial_acct_nbr = dpd91.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 91) = to_date(cast(dpd91.day_key as string), 'yyyyMMdd')
    , dpd91.days_delinq_qty AS dpd91
    LEFT JOIN prsnt_svcng.acct_status_fact dpd92
    ON a.partial_acct_nbr = dpd92.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 92) = to_date(cast(dpd92.day_key as string), 'yyyyMMdd')
    , dpd92.days_delinq_qty AS dpd92
    LEFT JOIN prsnt_svcng.acct_status_fact dpd93
    ON a.partial_acct_nbr = dpd93.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 93) = to_date(cast(dpd93.day_key as string), 'yyyyMMdd')
    , dpd93.days_delinq_qty AS dpd93
    LEFT JOIN prsnt_svcng.acct_status_fact dpd94
    ON a.partial_acct_nbr = dpd94.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 94) = to_date(cast(dpd94.day_key as string), 'yyyyMMdd')
    , dpd94.days_delinq_qty AS dpd94
    LEFT JOIN prsnt_svcng.acct_status_fact dpd95
    ON a.partial_acct_nbr = dpd95.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 95) = to_date(cast(dpd95.day_key as string), 'yyyyMMdd')
    , dpd95.days_delinq_qty AS dpd95
    LEFT JOIN prsnt_svcng.acct_status_fact dpd96
    ON a.partial_acct_nbr = dpd96.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 96) = to_date(cast(dpd96.day_key as string), 'yyyyMMdd')
    , dpd96.days_delinq_qty AS dpd96
    LEFT JOIN prsnt_svcng.acct_status_fact dpd97
    ON a.partial_acct_nbr = dpd97.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 97) = to_date(cast(dpd97.day_key as string), 'yyyyMMdd')
    , dpd97.days_delinq_qty AS dpd97
    LEFT JOIN prsnt_svcng.acct_status_fact dpd98
    ON a.partial_acct_nbr = dpd98.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 98) = to_date(cast(dpd98.day_key as string), 'yyyyMMdd')
    , dpd98.days_delinq_qty AS dpd98
    LEFT JOIN prsnt_svcng.acct_status_fact dpd99
    ON a.partial_acct_nbr = dpd99.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 99) = to_date(cast(dpd99.day_key as string), 'yyyyMMdd')
    , dpd99.days_delinq_qty AS dpd99
    LEFT JOIN prsnt_svcng.acct_status_fact dpd100
    ON a.partial_acct_nbr = dpd100.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 100) = to_date(cast(dpd100.day_key as string), 'yyyyMMdd')
    , dpd100.days_delinq_qty AS dpd100
    LEFT JOIN prsnt_svcng.acct_status_fact dpd101
    ON a.partial_acct_nbr = dpd101.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 101) = to_date(cast(dpd101.day_key as string), 'yyyyMMdd')
    , dpd101.days_delinq_qty AS dpd101
    LEFT JOIN prsnt_svcng.acct_status_fact dpd102
    ON a.partial_acct_nbr = dpd102.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 102) = to_date(cast(dpd102.day_key as string), 'yyyyMMdd')
    , dpd102.days_delinq_qty AS dpd102
    LEFT JOIN prsnt_svcng.acct_status_fact dpd103
    ON a.partial_acct_nbr = dpd103.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 103) = to_date(cast(dpd103.day_key as string), 'yyyyMMdd')
    , dpd103.days_delinq_qty AS dpd103
    LEFT JOIN prsnt_svcng.acct_status_fact dpd104
    ON a.partial_acct_nbr = dpd104.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 104) = to_date(cast(dpd104.day_key as string), 'yyyyMMdd')
    , dpd104.days_delinq_qty AS dpd104
    LEFT JOIN prsnt_svcng.acct_status_fact dpd105
    ON a.partial_acct_nbr = dpd105.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 105) = to_date(cast(dpd105.day_key as string), 'yyyyMMdd')
    , dpd105.days_delinq_qty AS dpd105
    LEFT JOIN prsnt_svcng.acct_status_fact dpd106
    ON a.partial_acct_nbr = dpd106.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 106) = to_date(cast(dpd106.day_key as string), 'yyyyMMdd')
    , dpd106.days_delinq_qty AS dpd106
    LEFT JOIN prsnt_svcng.acct_status_fact dpd107
    ON a.partial_acct_nbr = dpd107.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 107) = to_date(cast(dpd107.day_key as string), 'yyyyMMdd')
    , dpd107.days_delinq_qty AS dpd107
    LEFT JOIN prsnt_svcng.acct_status_fact dpd108
    ON a.partial_acct_nbr = dpd108.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 108) = to_date(cast(dpd108.day_key as string), 'yyyyMMdd')
    , dpd108.days_delinq_qty AS dpd108
    LEFT JOIN prsnt_svcng.acct_status_fact dpd109
    ON a.partial_acct_nbr = dpd109.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 109) = to_date(cast(dpd109.day_key as string), 'yyyyMMdd')
    , dpd109.days_delinq_qty AS dpd109
    LEFT JOIN prsnt_svcng.acct_status_fact dpd110
    ON a.partial_acct_nbr = dpd110.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 110) = to_date(cast(dpd110.day_key as string), 'yyyyMMdd')
    , dpd110.days_delinq_qty AS dpd110
    LEFT JOIN prsnt_svcng.acct_status_fact dpd111
    ON a.partial_acct_nbr = dpd111.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 111) = to_date(cast(dpd111.day_key as string), 'yyyyMMdd')
    , dpd111.days_delinq_qty AS dpd111
    LEFT JOIN prsnt_svcng.acct_status_fact dpd112
    ON a.partial_acct_nbr = dpd112.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 112) = to_date(cast(dpd112.day_key as string), 'yyyyMMdd')
    , dpd112.days_delinq_qty AS dpd112
    LEFT JOIN prsnt_svcng.acct_status_fact dpd113
    ON a.partial_acct_nbr = dpd113.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 113) = to_date(cast(dpd113.day_key as string), 'yyyyMMdd')
    , dpd113.days_delinq_qty AS dpd113
    LEFT JOIN prsnt_svcng.acct_status_fact dpd114
    ON a.partial_acct_nbr = dpd114.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 114) = to_date(cast(dpd114.day_key as string), 'yyyyMMdd')
    , dpd114.days_delinq_qty AS dpd114
    LEFT JOIN prsnt_svcng.acct_status_fact dpd115
    ON a.partial_acct_nbr = dpd115.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 115) = to_date(cast(dpd115.day_key as string), 'yyyyMMdd')
    , dpd115.days_delinq_qty AS dpd115
    LEFT JOIN prsnt_svcng.acct_status_fact dpd116
    ON a.partial_acct_nbr = dpd116.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 116) = to_date(cast(dpd116.day_key as string), 'yyyyMMdd')
    , dpd116.days_delinq_qty AS dpd116
    LEFT JOIN prsnt_svcng.acct_status_fact dpd117
    ON a.partial_acct_nbr = dpd117.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 117) = to_date(cast(dpd117.day_key as string), 'yyyyMMdd')
    , dpd117.days_delinq_qty AS dpd117
    LEFT JOIN prsnt_svcng.acct_status_fact dpd118
    ON a.partial_acct_nbr = dpd118.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 118) = to_date(cast(dpd118.day_key as string), 'yyyyMMdd')
    , dpd118.days_delinq_qty AS dpd118
    LEFT JOIN prsnt_svcng.acct_status_fact dpd119
    ON a.partial_acct_nbr = dpd119.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 119) = to_date(cast(dpd119.day_key as string), 'yyyyMMdd')
    , dpd119.days_delinq_qty AS dpd119
    LEFT JOIN prsnt_svcng.acct_status_fact dpd120
    ON a.partial_acct_nbr = dpd120.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), 120) = to_date(cast(dpd120.day_key as string), 'yyyyMMdd')
    , dpd120.days_delinq_qty AS dpd120 FROM apr a

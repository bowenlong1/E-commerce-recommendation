## check acct
acct = spark.sql("""SELECT acct_nbr, partial_acct_nbr, acct_key, day_key, PROP_TAX_DUE_AMT FROM prsnt_svcng.acct_status_fact where day_key = {day_key_today} """)
acct.createOrReplaceTempView("acct") 

ParseException: 
[PARSE_SYNTAX_ERROR] Syntax error at or near '}'.(line 1, pos 144)

== SQL ==
SELECT acct_nbr, partial_acct_nbr, acct_key, day_key, PROP_TAX_DUE_AMT FROM dpm_prod.prsnt_svcng.acct_status_fact where day_key = {day_key_today} 
------------------------------------------------------------------------------------------------------------------------------------------------^^^
---------------------------------------------------------------------------
ParseException                            Traceback (most recent call last)
File <command-3879728659668645>, line 2
      1 ## check acct
----> 2 acct = spark.sql("""SELECT acct_nbr, partial_acct_nbr, acct_key, day_key, PROP_TAX_DUE_AMT FROM dpm_prod.prsnt_svcng.acct_status_fact where day_key = {day_key_today} """)
      3 acct.createOrReplaceTempView("acct") 

File /databricks/spark/python/pyspark/instrumentation_utils.py:48, in _wrap_function.<locals>.wrapper(*args, **kwargs)
     46 start = time.perf_counter()
     47 try:
---> 48     res = func(*args, **kwargs)
     49     logger.log_success(
     50         module_name, class_name, function_name, time.perf_counter() - start, signature
     51     )
     52     return res

File /databricks/spark/python/pyspark/sql/session.py:1602, in SparkSession.sql(self, sqlQuery, args, **kwargs)
   1598         assert self._jvm is not None
   1599         litArgs = self._jvm.PythonUtils.toArray(
   1600             [_to_java_column(lit(v)) for v in (args or [])]

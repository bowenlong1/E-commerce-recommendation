from pyspark.sql import SparkSession

# Create a Spark session
spark = SparkSession.builder.appName("sas-to-pyspark").getOrCreate()

# Register the SAS tables as temporary SQL views
spark.sql("CREATE OR REPLACE TEMPORARY VIEW view_a AS SELECT * FROM mlops_work.contact_strategy_46_60_samp3_archive")
spark.sql("CREATE OR REPLACE TEMPORARY VIEW view_b AS SELECT * FROM prsnt_svcng.acct_status_fact")

# Perform the left join and select the required columns using Spark SQL
target = spark.sql("""
    SELECT a.*, b.day_key AS day7, b.days_delinq_qty AS dpd7
    FROM view_a a
    LEFT JOIN view_b b
    ON a.loan_acct_nbr = b.partial_acct_nbr
    AND CAST(TO_DATE(CAST(a.day_key AS STRING), 'yyyyMMdd') + INTERVAL 7 DAYS AS STRING) = b.day_key
""")

# Save the result as a new table
target.write.saveAsTable("default.target", mode="overwrite")

# Stop the Spark session
spark.stop()

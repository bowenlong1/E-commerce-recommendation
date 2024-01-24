from pyspark.sql import SparkSession
from pyspark.sql.functions import col, date_add

# Assuming you have a SparkSession named 'spark'
spark = SparkSession.builder.appName("YourAppName").getOrCreate()

# Original DataFrame 'apr'
apr = spark.table("your_apr_table_name")  # Replace with your actual table name

# Specify the range of dpd columns you want (1 to 120)
dpd_columns = range(1, 121)

# Initial SELECT statement for 'apr'
select_statement = "SELECT a.*"

# Loop to generate the LEFT JOIN conditions and dpd columns
for dpd in dpd_columns:
    join_condition = f"""
    LEFT JOIN prsnt_svcng.acct_status_fact dpd{dpd}
    ON a.partial_acct_nbr = dpd{dpd}.partial_acct_nbr
    AND date_add(to_date(cast(a.day_key as string), 'yyyyMMdd'), {dpd}) = to_date(cast(dpd{dpd}.day_key as string), 'yyyyMMdd')
    """
    dpd_column = f", dpd{dpd}.days_delinq_qty AS dpd{dpd}"
    
    select_statement += join_condition + dpd_column

# Complete the SQL query
sql_query = select_statement + " FROM apr a"

# Execute the query
result_df = spark.sql(sql_query)

# Show the result DataFrame
result_df.show()

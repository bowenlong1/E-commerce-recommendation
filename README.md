Hi Nivedita,

Here’s the logic in SAS to create the 'last contact date' filter. In the Databricks email pipeline, we would want to replace the '>7' filter with 'last contact date < today’s date - 7'.

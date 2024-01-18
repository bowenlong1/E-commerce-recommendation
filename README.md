ParserError: Unknown string format: 23OCT23:13:51:10
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
File /databricks/python/lib/python3.10/site-packages/pandas/core/arrays/datetimes.py:2236, in objects_to_datetime64ns(data, dayfirst, yearfirst, utc, errors, require_iso8601, allow_object, allow_mixed)
   2235 try:
-> 2236     values, tz_parsed = conversion.datetime_to_datetime64(data.ravel("K"))
   2237     # If tzaware, these values represent unix timestamps, so we
   2238     #  return them as i8 to distinguish from wall times

File /databricks/python/lib/python3.10/site-packages/pandas/_libs/tslibs/conversion.pyx:360, in pandas._libs.tslibs.conversion.datetime_to_datetime64()

TypeError: Unrecognized value type: <class 'str'>

During handling of the above exception, another exception occurred:

ParserError                               Traceback (most recent call last)
File <command-501241298318756>, line 1
----> 1 email0['workload_dt'] = pd.to_datetime(email0['event date']).dt.strftime('%Y-%m-%d')

File /databricks/python/lib/python3.10/site-packages/pandas/core/tools/datetimes.py:1047, in to_datetime(arg, errors, dayfirst, yearfirst, utc, format, exact, unit, infer_datetime_format, origin, cache)

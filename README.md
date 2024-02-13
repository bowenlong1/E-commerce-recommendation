---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
File <command-425309581680159>, line 28
     26 accuracy = accuracy_score(filtered_df['result'], filtered_df['pred'])
     27 f1 = f1_score(filtered_df['result'], filtered_df['pred'])
---> 28 roc_auc = roc_auc_score(filtered_df['result'], filtered_df['pred'])
     30 # Create a string to indicate the group
     31 group_indicator = '-'.join(['dpd{}'.format(quantile_combo[0] + 1),
     32                             'last{}'.format(quantile_combo[1] + 1),
     33                             'next{}'.format(quantile_combo[2] + 1)])

File /databricks/python/lib/python3.10/site-packages/mlflow/utils/autologging_utils/safety.py:552, in safe_patch.<locals>.safe_patch_function(*args, **kwargs)
    550     patch_function.call(call_original, *args, **kwargs)
    551 else:
--> 552     patch_function(call_original, *args, **kwargs)
    554 session.state = "succeeded"
    556 try_log_autologging_event(
    557     AutologgingEventLogger.get_logger().log_patch_function_success,
    558     session,
   (...)
    562     kwargs,

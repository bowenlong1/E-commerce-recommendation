Mean of empty slice.
invalid value encountered in double_scalars
F-score is ill-defined and being set to 0.0 due to no true nor predicted samples. Use `zero_division` parameter to control this behavior.
ValueError: Found array with 0 sample(s) (shape=(0,)) while a minimum of 1 is required.
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
File <command-425309581679927>, line 31
     29 accuracy = accuracy_score(filtered_df['result'], filtered_df['pred'])
     30 f1 = f1_score(filtered_df['result'], filtered_df['pred'])
---> 31 roc_auc = roc_auc_score(filtered_df['result'], filtered_df['pred'])
     33 # Store the metrics
     34 metrics_by_variable.append({
     35     'Variable': var,
     36     'Quantile': bucket,
   (...)
     39     'ROC-AUC': roc_auc
     40 })

File /databricks/python/lib/python3.10/site-packages/mlflow/utils/autologging_utils/safety.py:552, in safe_patch.<locals>.safe_patch_function(*args, **kwargs)
    550     patch_function.call(call_original, *args, **kwargs)
    551 else:
--> 552     patch_function(call_original, *args, **kwargs)
    554 session.state = "succeeded"
    556 try_log_autologging_event(
    557     AutologgingEventLogger.get_logger().log_patch_function_success,

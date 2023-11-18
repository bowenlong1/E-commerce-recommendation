
import shap
import matplotlib.pyplot as plt

# Assuming model is your trained model and X_test is the test data
explainer = shap.Explainer(loaded_model, X_test)
shap_values = explainer(X_test)

# Plot the SHAP values - you can use different types of plots available in SHAP
shap.summary_plot(shap_values, X_test, plot_type="bar")


TypeError: The passed model is not callable and cannot be analyzed directly with the given masker! Model: Pipeline(steps=[('column_selector',
                 ColumnSelector(cols=['oc_1m', 'days_since_last_contact',
                                      'net_fractn_auto_burdn_qty',
                                      'dpd_5mnth_begain', 'dpd_2_mnth_max',
                                      'CUSTOMER_STATE', 'msg_3m', 'oc_3m',
                                      'dpd_2mnth_begain',
                                      'SINCE_LAST_PMT_DAY_QTY',
                                      'days_since_last_rpt', 'days_to_next_pmt',
                                      'times_rpt', 'since_recent_auto_mnth_qty',
                                      'loan_age', 'last_6_mnth_late_30_trd_...
                                                   'contact_3m',
                                                   'msg_1week'])])),
                ('classifier',
                 LGBMClassifier(colsample_bytree=0.7931625999734807,
                                lambda_l1=0.17792982642623734,
                                lambda_l2=0.24025910561278496,
                                learning_rate=4.761139414247935, max_bin=340,
                                max_depth=9, min_child_samples=36,
                                n_estimators=1051, num_leaves=985,
                                path_smooth=99.08906929699528,
                                random_state=537209548,
                                subsample=0.5311797620466583))])

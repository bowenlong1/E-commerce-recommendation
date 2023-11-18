# Apply transformations of the pipeline
transformed_X_test = X_test
for step_name, step_process in model.steps[:-1]:
    transformed_X_test = step_process.transform(transformed_X_test)

# Get the final estimator
final_estimator = model.steps[-1][1]

# Now use SHAP on the final_estimator
explainer = shap.Explainer(final_estimator)
shap_values = explainer.shap_values(transformed_X_test)

# Plot SHAP values
shap.summary_plot(shap_values, transformed_X_test)

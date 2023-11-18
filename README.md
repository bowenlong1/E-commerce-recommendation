# Use KernelExplainer
explainer = shap.KernelExplainer(model.predict, X_test)
shap_values = explainer.shap_values(X_test, nsamples=100)  # Adjust nsamples as needed

# Plot SHAP values
shap.summary_plot(shap_values, X_test)

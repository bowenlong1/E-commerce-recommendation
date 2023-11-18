import shap
import matplotlib.pyplot as plt

# Assuming model is your trained model and X_test is the test data
explainer = shap.Explainer(model, X_test)
shap_values = explainer(X_test)

# Plot the SHAP values - you can use different types of plots available in SHAP
shap.summary_plot(shap_values, X_test, plot_type="bar")

# For more detailed plots, you can use:
# shap.summary_plot(shap_values, X_test)


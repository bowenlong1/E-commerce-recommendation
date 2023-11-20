import pandas as pd
from shap import summary_plot

# Assuming 'shap_values' is your DataFrame containing SHAP values
# The code for SHAP explanation you provided

# Calculate mean absolute SHAP values for each feature
mean_abs_shap_values = shap_values.abs().mean(axis=0)

# Sort feature names based on mean absolute SHAP values
sorted_feature_names = mean_abs_shap_values.sort_values(ascending=False).index.tolist()

# Display the sorted feature names
print(sorted_feature_names)

# Create the summary plot using the sorted feature names
summary_plot(shap_values, example, feature_names=sorted_feature_names, class_names=model.classes_)

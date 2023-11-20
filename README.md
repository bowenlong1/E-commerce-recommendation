import numpy as np
import pandas as pd
from shap import summary_plot

# Assuming 'shap_values' is your NumPy array containing SHAP values
# The code for SHAP explanation you provided

# Calculate mean absolute SHAP values for each feature
mean_abs_shap_values = np.abs(shap_values).mean(axis=0)

# Sort feature names based on mean absolute SHAP values
sorted_feature_names = mean_abs_shap_values.argsort()[::-1]

# Display the sorted feature names
print(sorted_feature_names)

# Create the summary plot using the sorted feature names
summary_plot(shap_values, example, feature_names=sorted_feature_names, class_names=model.classes_)

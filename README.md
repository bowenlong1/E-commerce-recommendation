def custom_summary_plot(shap_values, example, top_n=20):
    # Sum of SHAP values to get feature importance
    feature_importance = np.abs(shap_values).mean(axis=0)
    
    # Sort the features based on importance
    top_indices = np.argsort(feature_importance)[-top_n:]
    
    # Filter the top features
    top_shap_values = shap_values[:, top_indices]
    top_example = example.iloc[:, top_indices]
    
    # Show the summary plot for top features
    summary_plot(top_shap_values, top_example, class_names=model.classes_, plot_type="dot")
    
    # Bar plot to show top features with accurate color coding
    sorted_indices = np.argsort(-feature_importance)
    avg_shap_values = shap_values.mean(axis=0)
    plt.figure(figsize=(10, 5))
    plt.bar(range(top_n), feature_importance[sorted_indices[:top_n]],
            color=['red' if avg_shap_values[idx] > 0 else 'blue' for idx in sorted_indices[:top_n]])
    plt.xticks(range(top_n), example.columns[sorted_indices[:top_n]], rotation=90)
    plt.xlabel('Features')
    plt.ylabel('Mean Absolute SHAP Value')
    plt.title('Top {} Feature Importance with Impact Direction'.format(top_n))
    plt.show()

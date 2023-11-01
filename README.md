import matplotlib.pyplot as plt
import numpy as np

if shap_enabled:
    mlflow.autolog(disable=True)
    mlflow.sklearn.autolog(disable=True)
    from shap import KernelExplainer, summary_plot
    
    # SHAP cannot explain models using data with nulls.
    # To enable SHAP to succeed, both the background data and examples to explain are imputed with the mode (most frequent values).
    mode = X_train.mode().iloc[0]

    # Sample background data for SHAP Explainer. Increase the sample size to reduce variance.
    train_sample = X_train.sample(n=min(100, X_train.shape[0]), random_state=817465061).fillna(mode)

    # Sample some rows from the validation set to explain. Increase the sample size for more thorough results.
    example = X_val.sample(n=min(100, X_val.shape[0]), random_state=817465061).fillna(mode)

    # Use Kernel SHAP to explain feature importance on the sampled rows from the validation set.
    predict = lambda x: model.predict(pd.DataFrame(x, columns=X_train.columns))
    explainer = KernelExplainer(predict, train_sample, link="identity")
    shap_values = explainer.shap_values(example, l1_reg=False, nsamples=500)
    
    # Function to display top_n features
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
        
        # Bar plot to show top features
        sorted_indices = np.argsort(-feature_importance)
        plt.figure(figsize=(10, 5))
        plt.bar(range(top_n), feature_importance[sorted_indices[:top_n]],
                color=['red' if shap_values[0, idx] > 0 else 'blue' for idx in sorted_indices[:top_n]])
        plt.xticks(range(top_n), example.columns[sorted_indices[:top_n]], rotation=90)
        plt.xlabel('Features')
        plt.ylabel('Mean Absolute SHAP Value')
        plt.title('Top {} Feature Importance with Impact Direction'.format(top_n))
        plt.show()

    # Call the function to display top 20 features
    custom_summary_plot(shap_values, example, top_n=20)

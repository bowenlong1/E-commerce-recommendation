from sklearn.model_selection import GridSearchCV, TimeSeriesSplit, cross_validate
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
from xgboost import XGBClassifier
from lightgbm import LGBMClassifier
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, roc_auc_score, make_scorer
from sklearn.pipeline import Pipeline
import numpy as np

# Define models
models = {
    'Decision Tree': DecisionTreeClassifier(random_state=42),
    'Random Forest': RandomForestClassifier(random_state=42),
    'XGBoost': XGBClassifier(random_state=42),
    'LightGBM': LGBMClassifier(random_state=42)
}

# Hyperparameters for grid search
param_grids = {
    'Decision Tree': {
        'classifier__max_depth': [None, 10, 20, 30],
        'classifier__min_samples_split': [2, 5, 10]
    },
    'Random Forest': {
        'classifier__n_estimators': [50, 100, 200],
        'classifier__max_depth': [None, 10, 20, 30],
        'classifier__min_samples_split': [2, 5, 10],
        'classifier__class_weight': [None, 'balanced']
    },
    'XGBoost': {
        'classifier__learning_rate': [0.01, 0.05, 0.1],
        'classifier__n_estimators': [100, 200],
        'classifier__max_depth': [3, 5, 7],
        'classifier__scale_pos_weight': [1, 'balanced']
    },
    'LightGBM': {
        'classifier__learning_rate': [0.01, 0.05, 0.1],
        'classifier__n_estimators': [100, 200],
        'classifier__max_depth': [3, 5, 7],
        'classifier__class_weight': [None, 'balanced']
    }
}

# Scoring metrics
scoring = {
    'accuracy': make_scorer(accuracy_score),
    'precision': make_scorer(precision_score, average='weighted'),
    'recall': make_scorer(recall_score, average='weighted'),
    'f1': make_scorer(f1_score, average='weighted'),
    'roc_auc': make_scorer(roc_auc_score, multi_class='ovr', needs_proba=True)
}

# TimeSeriesSplit for time-based cross-validation
tscv = TimeSeriesSplit(n_splits=5)

# Iterate over models
for name, model in models.items():
    print(f"===== {name} =====")
    
    pipeline = Pipeline([
        ('classifier', model)
    ])
    
    # If the model has hyperparameters to tune, apply GridSearchCV
    if name in param_grids:
        grid_search = GridSearchCV(pipeline, param_grids[name], cv=tscv, n_jobs=-1, scoring=scoring, refit='accuracy')
        
        # Fit the model using the 'weight' column from X_train as sample_weight
        grid_search.fit(X_train[feature_pip], y_train, sample_weight=X_train['weight'])
        
        best_pipeline = grid_search.best_estimator_
        print(f"Best hyperparameters for {name}: {grid_search.best_params_}")
    else:
        # Fit the model without grid search (if no hyperparameter tuning required)
        best_pipeline = pipeline
        best_pipeline.fit(X_train[feature_pip], y_train, sample_weight=X_train['weight'])
    
    # Cross-validation metrics
    cv_results = cross_validate(best_pipeline, X_train[feature_pip], y_train, cv=tscv, scoring=scoring)
    
    for metric in scoring.keys():
        mean_metric = np.mean(cv_results[f'test_{metric}'])
        std_metric = np.std(cv_results[f'test_{metric}'])
        print(f"{metric.capitalize()}: {mean_metric:.4f} ± {std_metric:.4f}")

    print()


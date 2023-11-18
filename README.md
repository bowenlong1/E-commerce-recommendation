import mlflow

model_name =  "pay14_eot_notax"
model_version = 1

model_uri=f"models:/{model_name}/{model_version}"
loaded_model = mlflow.pyfunc.load_model(model_uri=model_uri)

'PyFuncModel' object has no attribute 'predict_proba'

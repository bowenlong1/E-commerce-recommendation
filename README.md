Your writing is clear and informative, but there are a few improvements that could be made for better clarity and organization:

Hi Nivedita,

Certainly! For the 2nd iteration model, we're currently using a 7-day prediction window to build the strategy, similar to the 1st iteration. Here's the training notebook: [link to notebook].

The model is saved using the following code:
```python
import mlflow

model_name = 'iter2_model_4660dpd'
model_version = 1

model_uri = f"models:/{model_name}/{model_version}"
loaded_model = mlflow.sklearn.load_model(model_uri=model_uri)
```

Additionally, we've also trained a model with a 14-day prediction window, although it's currently not utilized in our strategy design. Here's the training notebook for reference: [link to notebook].

The model is saved using the following code:
```python
import mlflow

model_name = "iter2_4660pd_14day"
model_version = 1

model_uri = f"models:/{model_name}/{model_version}"
loaded_model = mlflow.sklearn.load_model(model_uri=model_uri)
```

Please feel free to reach out if you have any questions.

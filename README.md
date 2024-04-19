Hi Nivedita,

Sure! For 2nd iteration model, we are currently still using 7-day prediction window to build the strategy just like 1st iteration. And here is training notebook:
https://adb-5993077223266823.3.azuredatabricks.net/?o=5993077223266823#notebook/2119004569609666

The model is saved here:
import mlflow
#import mflow.lightgbm

model_name =  'iter2_model_4660dpd'
model_version = 1

model_uri=f"models:/{model_name}/{model_version}"
loaded_model = mlflow.sklearn.load_model(model_uri=model_uri)


Just in case, we also trained a 14-day prediction window, which currently is not used in our strategy design. Here is the training notebook:
https://adb-5993077223266823.3.azuredatabricks.net/?o=5993077223266823#notebook/2119004569609666

The model is saved here
import mlflow
#import mflow.lightgbm

model_name =  "iter2_4660pd_14day"
model_version = 1

model_uri=f"models:/{model_name}/{model_version}"
loaded_model = mlflow.sklearn.load_model(model_uri=model_uri)

Please let me know if you have any questions.


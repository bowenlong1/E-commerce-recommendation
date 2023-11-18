## predict
from sklearn.model_selection import cross_val_score
from sklearn.model_selection import ParameterGrid
from sklearn.metrics import f1_score,average_precision_score, precision_recall_curve, precision_score, recall_score,roc_curve,roc_auc_score
# predict probabilities
from matplotlib import pyplot

X_test = df[fet_list_up]
y_test = df['pay14']
y_pred = model.predict(X_test[fet_list_up])

yhat = loaded_model.predict_proba(X_test[fet_list_up])
# retrieve just the probabilities for the positive class
pos_probs = yhat[:, 1]
# plot no skill roc curve
pyplot.plot([0, 1], [0, 1], linestyle='--', label='No Skill')
# calculate roc curve for model
fpr, tpr, _ = roc_curve(y_test, pos_probs)
# plot model roc curve
pyplot.plot(fpr, tpr, marker='.', label='Xgboost')
# axis labels
pyplot.xlabel('False Positive Rate')
pyplot.ylabel('True Positive Rate')
# show the legend
pyplot.title('ROC-AUC Curve')
pyplot.legend()
# show the plot

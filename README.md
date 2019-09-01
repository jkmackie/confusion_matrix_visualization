## Confusion Matrix Visualization
Multiclass confusion matrix in heatmap format.  Shows both counts and percentages.
***
We are tuning a multiclass model that predicts three possible results: ant, bird, or cat.  Suppose the model always predicts ants accurately, but is wrong classifying birds.  How do we measure this so we can tune our model?

**True versus Predicted Class**
![Alt text](images/Example-category-data.PNG)

The solutions is a multiclass confusion matrix.  Scikit Learn provides a [confusion_matrix](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html) tool.  For our scenario

## Confusion Matrix Visualization
*Easy-to-read Multiclass confusion matrix.  Shows color-coded counts and percentages.*
***
We are tuning a multiclass model that predicts three possible results: ant, bird, or cat.  Suppose the model always predicts ants accurately, but is wrong classifying birds.  How do we measure this so we can tune our model?

**True versus Predicted Class:**
![Alt text](images/Example-category-data.PNG)

The solution is a multiclass confusion matrix.  Scikit Learn provides a [confusion_matrix](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html) tool.  For our scenario, the matrix looks like this:

**sklearn confusion_matrix:**

![Alt text](images/sklearn-confusion-matrix.PNG)

But, how do we read and interpret this format?  The solution is my function, which converts the matrix to heatmaps with captions!


**Plot Confusion Matrix Function:**
![Alt text](images/cm-heatmap.PNG)

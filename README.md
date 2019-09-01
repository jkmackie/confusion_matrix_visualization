## Confusion Matrix Visualization
*Easy-to-read multiclass confusion matrix.  Shows color-coded counts and percentages.*
***
We are tuning a multiclass model that predicts three possible results: ant, bird, or cat.  Suppose the model always predicts ants accurately, but is wrong classifying birds.  How do we measure this so we can tune our model?

**True versus Predicted Class:**

![Alt text](images/Example-category-data.PNG)

The answer is a **multiclass confusion matrix**.  Scikit Learn provides a [confusion_matrix](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html) tool.  For our scenario, the matrix looks like this:

**sklearn confusion_matrix:**

![Alt text](images/sklearn-confusion-matrix.PNG)

But, how do we read and interpret this format?  The solution is my function, which converts the matrix to heatmaps with captions!  Both a regular matrix with counts and a "normalized" matrix with decimal percentages are plotted.
***

**Plot Confusion Matrix Function Output:**
![Alt text](images/cm-heatmap.PNG)


### Use the function as follows:

**`plot_confusion_matrix(confusion_matrix, class_names)`**

Where confusion matrix is the sklearn confusion matrix and class_names are the class labels we used for sklearn.

Optionally, set the figure size and font size.  Otherwise, the defaults are used.

* **figsize = (width, height)**    
* **fontsize = size_in_points**

*For example:  figsize = (15,6) and fontsize = 16.*

My function is different from existing solutions in three ways.  Redundant class pairs, which are zero, are hidden along with the unneeded color bar scale (may be revealed by editing function).  The function plots both count and percentage format by default.  The value alignment issue, where numbers appear outside the matrix, is fixed.

### Advanced Use Case:
Here is a scenario where we are predicting one of seven classes: [1,2,3,4,5,6,7].  The benefit of plotting percentages and counts side-by-side is illustrated.  In "Normalized", we see Class 6 predictions are less accurate than the first glance at "Counts".  Otherwise, we have to review the whole Class 6 row in "Counts" to realize accuracy is lower.

We also see the model is weak at successfully predicting Classes 1-3.  For example, The model often predicts Class 2 as Class 1.

**Confusion Matrix Shows Model Tuning Issues:**
![Alt text](images/seven-labels-circled.PNG)

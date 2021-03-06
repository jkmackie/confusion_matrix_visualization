## Confusion Matrix Visualization
*Easy-to-read multiclass confusion matrix.  Shows color-coded counts and percentages.*
***
Suppose we are tuning a multiclass model that predicts three possible results: ant, bird, or cat.  The model always predicts ants accurately, but is wrong classifying birds.  How do we measure this so we can tune our model?

<ins>**True versus Predicted Class:**</ins>

![Alt text](images/Example-category-data.PNG)

The answer is a **multiclass confusion matrix**.  Scikit Learn provides a [confusion_matrix](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html) tool.  It shows the count of True categories and where they were predicted to fall.  There are three true cats.  The model predicts two of the three are cats.  The third is predicted as an ant.

For our scenario, the matrix looks like this:

<ins>**sklearn confusion_matrix:**</ins>

![Alt text](images/sklearn-confusion-matrix.PNG)

But, how do we read and interpret this format?  The solution is my function, which converts the matrix to heatmaps with captions!  Both a regular matrix with counts and a "normalized" matrix with decimal percentages are plotted below.

<ins>**Plot Confusion Matrix Function Output:**</ins>
![Alt text](images/cm-heatmap.PNG)

In "Counts", sum the row to get the true number of a class.  There are three cats.  In "Normalized", sum the row to see the class percentages total 1.  A third of the cats are predicted to be ants; two-thirds of the cats are correctly labeled cats.
***
### Use the function as follows:

**`plot_confusion_matrix(confusion_matrix, class_names)`**

Where confusion matrix is the sklearn confusion matrix and class_names are the class labels we used for sklearn.

Optionally, keep errors only and set figure/font size.  Otherwise, the defaults are used.

* **`errors_only = True`** 
* **`figsize = (width, height)`** 
* **`fontsize = size_in_points`**

*For example:  figsize = (15,6) and fontsize = 16.  If errors_only = True causes a row total of zero, there will be
a divide-by-zero warning.*

My function is different from existing solutions.  Class pairs which are zero are hidden.  Keep errors only can be enabled.  The function plots both count and percentage format by default.  The value alignment issue, where numbers appear outside the matrix due to a Matplotlib 3.1.1 [bug](https://github.com/matplotlib/matplotlib/issues/14675), is fixed.

### Advanced Use Case:
Here is a scenario where we are predicting one of seven classes: [1,2,3,4,5,6,7].  The benefit of plotting percentages and counts side-by-side is illustrated.  In "Normalized", we see Class 6 predictions are less accurate than the first glance at "Counts".  Otherwise, we have to review the whole Class 6 row in "Counts" to realize accuracy is lower.

We also see the model is weak at successfully predicting Classes 1-3.  For example, the model often predicts  the true Class 2 is Class 1 and vice-versa.

<ins>**Confusion Matrix Shows Model Tuning Issues:**</ins>

![Alt text](images/seven-labels-circled.PNG)

### What about Unbalanced Class Labels?:
Imagine we are predicting "Fraud" or "NoFraud", like a credit card transaction.  These classes are called **unbalanced** because there is NoFraud most of the time.  In truth, there is 90% NoFraud or 18 out of 20 times.  The remaining 10% is fraud, occurring 2 times.  

<ins>**True Class Labels (Unbalanced):**</ins>

![Alt text](images/unbalanced-class-histog.PNG)


Below, the model correctly predicts one of the two Fraud transactions--everything else is labeled NoFraud.

<ins>**Unbalanced Class Labels - NoFraud and Fraud:**</ins>

![Alt text](images/unbalanced-classes.PNG)

We must carefully interpret our result.  "Counts" says we only misclassified once.  But, "Normalized" reveals we missed half the Fraud!  If our goal is to stop Fraud, tune the model to aggresively predict fraud, at the cost of flagging some NoFraud as Fraud.

This example was contrived for simplicity.  In reality, there might be 200,000 rather than 20 transactions.  The true fraud rate might be an even lower percentage.

Here is Confusion Matrix terminology illustrated with our fraud prediction scenario.
* **True Positives (TP) - Fraud *correctly* predicted**
* **False Positives (FP) - Fraud *wrongly* predicted**
* **True Negatives (TN) - NoFraud *correctly* predicted**
* **False Negatives (FN) - NoFraud *wrongly* predicted**

These terms communicate confusion matrix results.  The terms are also used in classification [metrics](https://towardsdatascience.com/beyond-accuracy-precision-and-recall-3da06bea9f6c) like precision, recall, and F1 score.

*Please email me with any feedback:  **jmackie "at" gmail "dot" com***

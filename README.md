Download Link: https://assignmentchef.com/product/solved-b555-project1-experiments-with-bayesian-linear-regression
<br>
Your goals in this assignment are (i) to investigate the effect of the number of examples, the number of features, and the regularization parameter on the performance of the corresponding algorithms, and (ii) to investigate two methods for model selection in linear regression (evidence maximization and cross validation). In all your experiments you should report the performance in terms of the mean square error

MSE =

where the number of examples in the corresponding dataset is <em>N</em>.

<h1>Data</h1>

Data for this assignment is provided in a zip file pp2data.zip on Canvas.

Each dataset comes in 4 files with the training set in train-name.csv the corresponding labels (regression values) in trainR-name.csv and similarly for test set. We have both artificial data and real data, with real data in the crime and wine datasets. Note that the train/test splits are fixed and we will not change them in the assignment (in order to save run time).

The files for the artificial data are named as NumExamples-NumFeatures for easy identification of training set characteristics. (NumExamples is the number of examples in the training set, not the test set). Specifically we have 3 variants with the combinations 100-10, 100-100, 1000-100. Note that the different artificial datasets have different underlying predictive functions (hidden vector <em>w</em>) so they should not be mixed together. The artificial data was generated using the regression model and is thus useful to test the algorithms when their assumptions hold.

For the artificial data you can compare the MSE results to the MSE of the hidden true functions generating the data that give 5.714 (for 100-10), 0.533 (for 100-100), and 0.557 (on 1000-100).

<h1>Task 1: Regularization</h1>

In this part we use regularized linear regression, i.e., given a dataset, the solution vector <em>w </em>is given by equation (3.28) of Bishop’s text.

For each of the 5 datasets plot the training set MSE and the test set MSE as a function of the regularization parameter <em>λ </em>(use integer values in the range 0 to 150). It is useful to put both curves on the same plot. In addition, compare these to the MSE of the true functions given above.

In your report provide the results/plots and discuss them: Why can’t the training set MSE be used to select <em>λ</em>? How does <em>λ </em>affect error on the test set? Does this differ for different datasets? How do you explain these variations?

<h1>Task 2: Learning Curves</h1>

Now pick three “representative” values of <em>λ </em>from the first part (“too small”, “just right”, and “too large”) for the dataset 1000-100. For each of these values plot a learning curve for the learned regularized linear regression on this dataset.

A learning curve plots the performance (in our case MSE) of the algorithm as a function of the size of the training set. To produce these curves you will need to draw random subsets of the training set (of increasing sizes) and record the performance (on the fixed test set) when training on these subsets. To get smooth curves approximating the mean performance you will need to repeat the above several times (at least 10 times) and average the results. Use enough training set sizes between 10 and 1000 samples to generate smooth curves.

In your report provide the plots and some numerical results and discuss them: What can you observe from the plots regarding the dependence of the error on <em>λ </em>and on the number of samples? Consider both the case of small training set sizes and large training set sizes. How do you explain these variations?

<h1>Task 3.1: Model Selection using Cross Validation</h1>

The previous experiments tell us which value of <em>λ </em>is best in every case <em>in hindsight</em>. That is, we need to see the test data and its labels in order to choose <em>λ</em>. This is clearly not a realistic setting and it does not give reliable error estimates. In this part and the next we investigate methods for choosing <em>λ </em>automatically without using the test set.

In this part we use 10 fold cross validation <em>on the training set </em>to pick the value of <em>λ </em>in the same range as above, then retrain on the entire train set and evaluate on the test set. To avoid confusion, the procedure for doing this is explained at the end of the assignment.

Implement this scheme, apply it to the 5 datasets and report the values of <em>λ </em>selected, associated MSE and the run time. How do the results compare to the best test-set results from part 1 both in terms of the choice of <em>λ </em>and test set MSE?

<h1>Task 3.2: Bayesian Model Selection</h1>

In this part we consider the formulation of Bayesian linear regression with the simple prior <em>w </em>∼

). Recall that the evidence function (and evidence approximation) gives a method to pick the parameters <em>α </em>and <em>β</em>. Referring to Bishop’s book, the solution is given in equations (3.91), (3.92), (3.95), where <em>m<sub>N </sub></em>and <em>S<sub>N </sub></em>are given in (3.53) and (3.54). These yield an iterative algorithm for selecting <em>α </em>and <em>β </em>using the training set. We can then calculate the MSE on the test set using the MAP (<em>m<sub>N</sub></em>) for prediction.

This scheme is pretty stable and converges in a reasonable number of iterations. You can initialize <em>α,β </em>to random values in the range [1<em>,</em>10]

Implement this scheme, apply it to the 5 datasets and report the values of <em>α,β</em>, the effective <em>λ </em>= <em>α/β</em>, the associated MSE and the run time. How do the results compare to the best test-set results from part 1 both in terms of the choice of <em>λ </em>and test set MSE?

<h1>Task 3.3: Comparison</h1>

How do the two model selection methods compare in terms of effective <em>λ</em>, test set MSE and run time? Do the results suggest conditions where one method is preferable to the other? Please try to think about the results obtained and discuss these questions even if you do not see an obvious trend.
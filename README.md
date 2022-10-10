# Machine-Learning-LAB
Perform Machine Learning using various models and analyzed for results.


# LAB 1 Proposal
### <data exploration & data preprocessing - without scaling & encoding>

The number of records is 699 ,but the unique value is 645. There is a record with overlapping IDs. Because the contents of the data in the overlapping ID are different, we do not remove the overlapping ID data. (We will drop ID feature)
Bare Muclei data contains missing data.('?')
-> So, Drop the whole feature OR Delete missing data only.

Q. Is there anything to drop for feature?

A. No. Even if it is concentrated on one side, it is because it is a disease search, so a small number of data can be important. Therefore, We think to save all data because a small number of data is likely to be important.


### <data preprocessing - scaling & encoding>

Scaling : We will use 5 different scaling methods. (MinMax, Robust, Standard, MaxAbs, Nomalizer)<br>
Encoding : dataset is all numerical type. So, Encoding is unnecessary.


### <Model building&gt;

Data split : test_size=0.3<br>
We use 4 modeling algorithms and each parameters.<br>
logistic regression : solver = {‘newton-cg’, ‘lbfgs’, ‘liblinear’, ‘sag’, ‘saga’}<br>
<br>DT (entropy) : criterion = entropy, max_features= {“auto”, “sqrt”, “log2”}<br>
DT (gini) : criterion = gini, max_features= {“auto”, “sqrt”, “log2”}<br>
SVC : kernel = {‘linear’, ‘poly’, ‘rbf’, ‘sigmoid’, ‘precomputed’}, gamma = {‘scale’, ‘auto’}, C = {0.01, 0.1, 1}<br>
In addition, in the case of model instances, it is collected separately in the array for score calculation in testing.


### <testing&gt;
Calculate the score by adjusting the k(Cross validataion paramater 3,5,7) value with the model instances stored in the array. Also, print the top 5 accuracy model.


### <Flowchart of simple code&gt;
```python
def do_classification()
  load_and_modification_dataset()
  for scaler in [scalers]:
    Scaling()
    DataSplit() ← test_size = {0.1, 0.2, 0.3}
    for model in [models]:
      Modeling()
      newArr ← saving model instance
    CrossValidation() ← k={3,5,7}
  top_5 = findTop5()
  return top_5

main(){
  top_5 = do_classification()
  print(top_5)
}
```

# LAB 1 Conclusion

<b>Index
1. Conclusion
2. Team member contribution
3. Source code
4. Output results
</b>

<br>
First, we checked the null value for dataset. Based on the experience, “ID” is determined as a column that is not necessary in this data analysis. After checking the dataset, “Bare Nuclears” is numeric data, but the type is object type. Also we found that some of the value is '?'. To preserve as much data as possible, '?' were replaced with the mean value of the corresponding column. <br>

Use Correlation to check the relationship between the target feature "class" and the rest of the features. We find that “Mitoses” is relatively less associated with “class” than other features. So, we decided to drop "Mitoses" column.<br>
![Corr Matrix](https://user-images.githubusercontent.com/69946205/194837456-2e6eeef9-bbd6-4f38-ab9d-9091a8e0a637.png)

When we print out all the results, we can see that svm has the highest accuracy. The next ranking is the logistic regression model, and the third is the decision tree model. Also, in svm, the kernel in the form of sigmoid was mainly high in accuracy.

<br>
Since linear svm is limited to two dimensions, it can be confirmed that the accuracy appears high in other types of kernels. And the difference in score for the criterion of the decision tree was very small.

<br>
C is a parameter that determines how many data samples are allowed to be placed in another class, and it can be seen that the C value shows high accuracy when it is 0.1. However, it should be noted that there is a risk of underfitting if the C value is too small and overfitting if it is high.(also in gamma). Also, in the SVM model, the score showed a big difference according to gamma and C parameters. (97%~30%)

<br>
In the case of the scaler, the standard scaler had the highest average value on average and the minmax was the lowest. (However, since this is an average that does not take into account other columns, it cannot be said to be an exact number, but it is a number that is somewhat consistent when directly checking the upper, middle, and lower ranks in accuracy. ) Also the score difference according to the scaling method was very small. <br>

![제목 없음](https://user-images.githubusercontent.com/69946205/194837945-ee350c16-0b1c-4cab-94ff-1419523efa1b.png)

SVM is a powerful model and works well on a variety of datasets. However, it should not always be concluded that SVM is powerful.

When the amount of samples is large, it often does not fit well. After all, it is also up to the user to decide this.<br>

![Contribution](https://user-images.githubusercontent.com/69946205/194838213-4a4e230a-36ee-4e1c-a974-85a304532aa0.png)

All team members wrote their own code from start to finish, had a meeting time to modify and integrate the code, and analyze it together.

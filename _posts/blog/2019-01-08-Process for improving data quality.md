---
layout: post
title: Process for Improving Data Quality for ML
date: 2019-01-08
categories: blog
---

ML is a process that can be roughly summarized into these steps:

**1. fill missing values**
- use df.dropna(); df.fillna(); df.dropna(subset=['total wealth']), which removes NA's only from a single column
- fill the na's with an average value if you don't want to drop the rows with NA

**2. make sure the data types are correct**
- many ML algorithms can't handle categorical variables. So, we need to turn them into numbers using
`df['wealth bracket'].map({'lower':0, 'upper':1,'higher':2})
`
- _important_: if there is a natural order to values we changed, then we can leave it as is. If not, and they are instead values like cat, dog, and rat, then we need to use sklearn's OneHotEncoder. Link to [OneHotEncoder tutorial](https://machinelearningmastery.com/how-to-one-hot-encode-sequence-data-in-python/)

**3. Make sure all values are scaled properly, or else the algorithm will read numbers in absolute terms**
- sklearn.preprocessing.StandardScaler will standardize the Data

**4. If the training accuracy is good and the testing accuracy sucks, maybe a variable in the data set is overfitting?**
- if this happens, try removing certain variables and see if the overfitting decreases
- you should remove variables that are highly correlated (multicollinearity is a problem)
- to quickly see multicollinearity, use a scatterplot on all the variables. If certain variables trend with each other very closely, it's time to remove the repeats
- apparently RandomForestClassifier can give us the importance of each feature. Remove the least important features

{% highlight python %}
my_importance_model = RandomForestClassifier(n_estimators=10000, random_state=0, n_jobs=-1)
my_importance_model.fit(independent_variables, dependent_variables)
print(my_importance_model.feature_importances_)
{% endhighlight %}

- tester
**5. Create new features from the existing ones**
- let's say you have month and day data. You can set seasonality as a column

----
****

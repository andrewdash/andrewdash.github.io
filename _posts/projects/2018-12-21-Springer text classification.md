---
layout: post
title: Machine Learning on Text Data
date: 2018-12-21
categories: projects
---
![](/assets/images/springerlogo.jpg){:height="240px" width="540px"}

I took a stab at machine learning in python as it applies to words and text data.

[Machine Learning on Text Data](/assets/files/final_project_for_site_v2_shortform.html)

Before introducing the data, I want to explain my reasoning for this project and why I chose a text data set

**My goals for doing this**
I wanted to explore different methods of machine learning, such as Random Forest, Linear Regression, SVC, etc. This was an incredible learning experience as I could compare the different methods and try essentially everything in ML.  


**Why did I choose this data set in particular?**
  1. Getting an amazing accuracy rate would be *very* challenging, meaning I could explore further into different ML methods (AI/deep learning) to see what works best.
  2. The data set had to be gathered, letting me learn how to pull from APIs so that I could have this skill moving forward (if I ever need it)

The idea is that, let's say we're given a bunch of observations (each row on an Excel sheet) that have some amount of sentences and text attached to it (column B of the Excel sheet), whom are split into 7 different groups (column C of the Excel sheet that has values ranging from 1-7). Now if we're handed some sentences and we're asked, "Which group 1-7 do these sentences represent?", how would we go about solving this? This is where machine learning comes in.

Thinking about the data in terms of an Excel sheet is a good mental model, but Python is where this analysis is going to happen (I don't think Excel can do this).

I looked at scientific paper data, gathering a list of scientific paper abstracts from the [Springer website](https://dev.springernature.com/), a popular publisher for scientific journals/articles.

*Here is the process in summary*
1. __identify inputs, outputs__
: inputs = scientific abstracts, about 100 words each
: outputs = scientific article name (such as BMC Infectious Diseases, BMC Public Health). We will want to predict these
2. __do exploratory data analysis__
: Found that there are 70+ publications named in the data set. Can't make good predictions with too many of these, so I only chose the top 7 most popular publications.
3. __transform the data so that calculations can happen on it__
: Text data by itself doesn't mean anything to a computer for this analysis. I'll convert each one of the scientific abstracts to a grid of numbers (called vectorization), use a : method that modifies these abstract-turned-numbers to value the words that are most unique to each publication.
4. __test different machine learning models__
: Tested models LinearSCV(), RandomForestClassifier(), KNeighborsClassifier(), LogisticRegression(), and MultinomailNB(). Used cross-validation to get a best estimate for each model. It's important to not assume that there is a "one classifier to rule them all," as [explained by some UPenn researchers](https://psb.stanford.edu/psb-online/proceedings/psb18/olson.pdf).
5. __tuned hyperparameters for the Logistic Regression (was best performing classifier here)__
: Used `RandomSearchCV` to find a couple different hyperparameter. Accuracy only went up 1% from hyperparameter (from 79%-80%), which doesn't mean much. Could be interesting to look into the technicals for why tuning hyperparameters didn't improve the accuracy a lot. Or, it could also be a good opportunity to check out other methods for text classification, like ai/deep learning.

6. __conclusions & reflection__
: Accuracy wasn't as high as I would have hoped it to be, but 80% is not bad for a quick, (somewhat rudimentary) ML model comparison.

Instead, this was a great project for me to...
- explore different ML classifiers
- learn how to tune the models to be even more accurate using hyperparameters
- see how some of the details on how text classification works
: ...while also giving me opportunity to dig into deeper fields for ways to analyze things (ai/deep learning, other machine learning methods)



[Machine Learning on Text Data (short-form)](/assets/files/final_project_for_site_v2_shortform.html)




For reference, here is the long-form analysis. This just goes into further description on how I came about creating the hypothesis, things that influenced that thought process, and other miscellaneous information.

[Machine Learning on Text Data (long-form analysis)](/assets/files/final_project_for_site_v2_longform.html)

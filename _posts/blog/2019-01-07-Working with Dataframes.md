---
layout: post
title: Working with Dataframes
date: 2019-01-07
categories: blog
---
<br/>
Learning how to manipulate data frames is the most important baseline for data analysis. Data comes in the form of tables, which we can think of as an Excel sheet. `Rows` represent each data point (one customer) and `columns` represent stuff that describes each of these data points.

You're limited on the kind of stuff you can do with the spreadsheet in Excel, so this is where Python comes in. Here are a couple helpful things that I've certainly come across multiple times working with data frames. I'll likely continue to update this post as I come across more data frame tips I want to jot down.

#### 2019-01-07
### How do you add a column to an existing data frame?
`df.join(new_column)`

- new_column needs to be the same length as the data frame or else you get an error
- new_column also cannot be a list. It must be a Series or data frame, or list of data Dataframes. If it is a Series, then it must have a name.
- new_column needs to have the same index as df. Solve this by using .reset_index(drop=True) to get all the indexes to start from 0


### How do you add new rows to the existing data frame?
`df.append(new_information)`

#### 2019-01-10
Multi-indexing and how to search through it. This [tutorial on multi-indexing by Data Camp](https://www.datacamp.com/community/tutorials/pandas-multi-index) was really helpful. I'm thinking of checking out more tutorials from here to learn from.

### How do you split numerical data in to different bins?
Here's an example with the titanic data. There's a column with `ages`, and we want to label them as child, teenager, adult, and elder.

```python
bins = [0,12,17,60,np.inf]
labels = ['child','teenager','adult','elder']
# pd.cut maps the passenger's ages to a label
age_groups = pd.cut(titanic.age, bin, labels=labels)
titanic['age_groups'] = age_groups


# find the counts for each groupings
groups = titanic.groupb(['age_group','alone'])
groups.size()

# percentages for each group's counts
groups.size() / len(titanic)

```
[tutorial on doing groupbys](https://tryolabs.com/blog/2017/03/16/pandas-seaborn-a-guide-to-handle-visualize-data-elegantly/#Groupby)

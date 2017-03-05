---
layout: post
title: "Book Review: Big Data and Social Science"
date: 2017-03-05
categories: bookreview
---

# **Overview**

TL;DR: Broad introduction to data science techniques: data collection, machine
learning, and validating conclusions. Read it with a concrete problem in mind
and really learn from the references. Look at [notebooks] for code examples.

Big Data and Social Science: A Practical Guide to Methods and Tools is a book
that seeks to give practical advice for applying data science techniques to
real-world problems.  The book provides a broad overview of a diverse set of
techniques in data science, so the book is best consumed with a particular problem in
mind.


# **Reactions**

Overall, I felt that the book was a good overview of a large variety of
techniques that come to bear on using data science to look at social issues.
One of the best features is that they have a set of ipython notebooks located
at [notebooks].  On the other hand, I felt that the book leaves you with little
depth in understanding any particular topic (e.g. machine learning is covered
in one chapter). I am not sure I have a practical suggestion as to how to
remedy this issue, since the book seeks to cover a very broad topic.
In retrospect, I think that reading this book would have been much
more useful if I had a particular application in mind.  That way I could have
used this book as a reference for techniques that I could have looked at in
more detail later.


# **More Detailed Summaries**

The book contains three major sections, Data
Capture and Curation, Modeling and Analysis, and Inference and Ethics.


- **Capture and Curation**

This section focuses on the different ways that one can obtain data and manage
that data.  The section starts out with a specific example of using web APIs to
get data. The next section discusses combining your raw data and matching
different records. This is a challenging and interesting problem because while
you want to identify if two pieces of data, for instance, correspond to the
same person. The section ends with a discussion of databases.

- **Modeling and Analysis**

This section starts with an overview of different machine learning methods,
text analysis, and network analysis. I already know a lot about these methods,
so I didn't get too much from this part of the book.

- **Inference and Ethics**

This section contains the chapter that I found to be most interesting:
Errors and Inference

Major issues:

Data generation process is often not created for the sake of generating valid
conclusions about the data, and can introduce systematic bias, which renders
future analysis useless.

Record linking can introduce either random or systematic error in the data.

When your number of features is large in your data, that can lead to spurious
correlations and overfitting in your statistical models.

While big data has been said to be useful for studying rare populations, small
errors in the data on these rare populations have large impacts on the
analyses that you might want to use (e.g. a classifier).

There are a variety of ways to attempt to mitigate errors. The first is to
create some rule that meshes with your experience, and to see if that trend is
present in your data.  This can help identify spurious errors in the data.
There are also systematic methods based on various machine learning techniques.
One particularly interesting method is called the tableplot. Basically, you
take your data and form a histogram for one variable, and then look at the
values of another variable in each of the chunks formed by your histogram. This
can help identify inconsistencies in those aggregates.


This section also had chapters on information visualization and privacy and
confidentiality.  A key point is that behavior at the tails of a distribution
is both the most interesting in many cases and can be most risky in terms of
privacy. I think one major gap in this chapter is addressing the issue that
researchers don't act rationally for a variety of reasons (e.g. taking on
implicit biases from culture, or being professionally invested in advancing a
particular theory).



# **Conclusion**

Data science seeks to address very challenging problems and as a result, the
methods used in data science form a hodgepodge of techniques from a wide
variety of different fields. A book on data science is going to reflect that.
While to book gives a good introduction to data science, I feel that it suffers
from the fact that it doesn't offer a decisive account of any particular
issues. Indeed, as data science as a field grows, this book will need
to be updated.

[notebooks]: https://github.com/BigDataSocialScience



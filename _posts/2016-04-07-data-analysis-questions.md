---
toc: true
layout: post
description: Recognizing the types of questions you are asking throughout a data analysis project.
categories: [data analysis]
title: Know your questions!
image: images/question_mark.png
---
# Know your questions!

<img style="float: left; height: 200px; margin-right: 7px" src= "{{site.baseurl}}/images/question_mark.png" alt="Question mark" title="Question mark">

Articulating precisely the question you are asking of the data gives clarity and focus to your data analysis.
A complication is that often a data analysis flows through different stages in a non-linear way: you have some preliminary assumptions, you explore the data,
you revise the assumptions, then notice a correlation between variables, go on a week-long deep-dive to investigate it until you realize it was
nothing, and so on and so forth. Another complication is that, as you work through the stages of the analysis, you sometimes must revise or completely change
the original, broader question based on what you are learning. Managing these challenges is essential to producing an impactful analysis that answers the right
question and abides by the best practices. 

Over the years I've found that being aware of the type of question I am asking at each stage of a data analysis helps me work through these  challenges. I've also found that being deliberate about noticing the stage transitions in a data analysis project helps
me avoid time-consuming detours and dead-ends. The key is to label each data analysis stage with the appropriate type of question. So, what are the types of questions? For a long time I did not have a crisp nomenclature to help me, so I followed my intuition and experience, with mixed success. Recently I came across the work of researchers [Roger Peng](http://www.biostat.jhsph.edu/~rpeng/), [Elizabeth Matsui](http://www.jhsph.edu/faculty/directory/profile/5586/elizabeth-matsui), and [Jeff Leek](http://jtleek.com) who have come up with a
crisp  list of six types of questions relevant to data analysis: *descriptive, exploratory, inferential, predictive, causal,
and mechanistic.* I now use their list to guide me through my data analyses. Below, I summarize the six types of
questions and riff on them a bit with my own observations from my data analysis experiences. 

## The Six Types of Questions, according to Peng, Matsui, and Leek. 
Peng, Matsui and Leek describe six types of questions for data analysis: 

### Descriptive
In a descriptive data analysis, all you do is describe the data. Typical outputs of these analyses are simple aggregations, like counts,
percentages, bar charts, probability density estimates, quantiles, maximum, minimum, and missing values. You do not attempt to explain or interpret these
summary statistics, or relate them to other sources of information. Dashboards are an example output of a descriptive data
analysis: they summarize the data and offer it up to human experts for interpretation.
 
Almost always, a descriptive analysis is my first step in a broader study/analysis. It gives me an idea of the data size,
distribution, and types, and helps me form a first guess at the types of analyses achievable with the given the data set. In fact
I would say that every data analysis should go through a descriptive stage, even if its scope is limited. If you jump straight to inference or prediction without describing the data, you may not be able to interpret your results, or, horrors, may draw the wrong conclusion. So do yourself a favor: describe your data first. There are even built-in tools in Python:  [pandas.DataFrame.describe()](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.describe.html) and Dato's [graphlab.SFrame.show()](https://dato.com/products/create/docs/generated/graphlab.SFrame.show.html#graphlab.SFrame.show) are good places to start, or fire up Tableau. There are no excuses! 


### Exploratory
Think of exploratory data analysis as the idea-generation phase of a study. During this phase you formulate hypotheses about the relationships
between subsets of the data. Perhaps you notice that shoppers tend to buy more hot dogs and beer on warm weekends; perhaps you notice an increased presence
of pleasure boats during the summer on a given waterway; or maybe you observe that some of the 1000s of time series in your data set could be grouped  into a
small number of clusters. Whatever the subject matter, I find the exploratory phase very fun because it gives me creative license
to free-associate, cut, slice, transform, and visualize the data, and formulate and quickly de-risk --sometimes improbable-- hypotheses. I experience a sense of excitement and of possibility that stimulates my creativity.

With all this excitement it's easy to get carried away and mistake a generated hypothesis for a conclusion. Don't do it! Instead, make a list of the hypotheses, and support each of them with charts and quick calculations. You can do this easily with the Jupyter notebook in Python or with Tableau. Then figure out which one to address further first, perhaps with the help of teammates or
subject matter experts. This is a perfect opportunity to share your hypotheses with your data analysis team, which may include other data
scientists, subject matter experts and business stakeholders. Careful though: make sure you manage the message if your audience is
not familiar with data analysis workflows. You are still at the rough draft stage of your overall analysis and you don't want your
preliminary hypotheses to be misconstrued as conclusions by an eager, but not data-savvy, manager.  


### Inferential
Remember those hypotheses you generated during the exploratory phase? In an inferential analysis you seek to validate a
hypothesis on a different data set, or infer that what you observed during the exploratory phase holds in general. Why would you want to do that? Well, think of polls and surveys. The available data are a subset collected from the overall population, but you are seeking to generalize what you learn from the sample to the entire population. Here's a made-up example. Say you discover that in your data set of 1000 adults, those who exercise at least 30 minutes a day enjoy a  10% decrease in the risk of heart disease. An inferential analysis would tell you if this result holds for the entire adult population, and typically it would also give you a 
bound on the uncertainty around the result, which captures how robustly the result generalizes to the overall population. 
  
### Predictive
Which customers are likely to churn out of a subscription over the next 60 days? Which offer is more likely to entice them to
renew their subscriptions? How many cargo vessels will enter the port of Seattle in June 2018? These are examples of predictive
questions, which arise in many fields and often underpin entire business models: data-driven startups live or die depending on
their ability to answer predictive questions. Sometimes it's easy to confuse a predictive question with and inferential one.
When I'm confused I remind myself that with inference I am testing how well a hypothesis generalizes to a larger, or distinct
data set, while with prediction I am attempting to identify the factors that predict an outcome. Here's another way to
remember this: with inference, you are making statements about  averages, or other aggregated statistics, over groups;
with prediction, you are attempting to predict an individual outcome.
    
 
### Causal
In a causal analysis, you seek to test a cause-effect relationship between variables. Causation is a stronger relationship than
correlation, which merely identifies a link between the variables. Often business problems are answered well enough by a
predictive analysis, but  sometimes you may be interested in the causes of the relationship between variables, especially when
you are attempting to interpret the results more deeply based on the subject matter (with the help of an expert). Just be mindful and
do not confuse a successful predictive analysis, which builds on correlations between inputs and outputs, with a causal one.   

### Mechanistic
A mechanistic question deals with the exact mechanisms involved in a phenomenon. For example, a chemical reaction can be explained
exactly and mechanistically in terms of molecular bonds breaking and forming. Other examples are post-hoc
reconstruction of events and root-cause analyses. It's difficult to answer mechanistic questions as part of a prediction or inference task
without data from very-well controlled experiments. Frankly, I have never come across a situation that called for a mechanistic data
analysis (except for debugging code ...), although this reflects my personal experience and is in no way a general statement about
data analysis. However, I did catch myself a few times attempting to explain in detail how a variable affected another one
even though the analysis did not call for a mechanistic explanation. So, recognize mechanistic thinking when it comes up,
and decide if it's appropriate for the particular stage of the analysis.


## Inference, Prediction, Training, and Testing
If you work with big data technologies, 
you may be able to describe, explore and predict directly on the entire population, without sampling. For example, in a customer
churn prediction task, you may have access to the entire customer base, numbering in the millions. 
So, perhaps you may be tempted to not bother with estimating how well your prediction applies to data outside of the available data set.
That would be a mistake. 
Even if you have access 
to the entire population at a particular time, the population will change: a customer base changes continuously, new customers arrive and
old ones churn out. 

Conversely, you may have access only to a very small sample of the overall data set, but need to ensure that your inference extends to
the entire population. For inference and prediction then, you need to estimate how well your models generalize. In addition to
specifying the sampling process,  the standard way to de-risk the generalization is to set
aside separate training and testing subsets from the available data. Design your model on the training set, and test it on the
testing set. Even better, if your model depends on hyper parameters, you should also have a separate cross-validation
data set. In fact, to gain confidence that your prediction will be robust, you should repeatedly and randomly select the
training and testing sets and assess the performance on each random split. 
If the results are consistent across the splits, you are on the right path.

I mention the issue of splitting the data into separate training and testing sets in the context of the types of data analysis questions
 because it's a pervasive issue no matter the type of question. It's possible to be clear about the type of analysis and yet
produce incorrect results, unless the data are properly separated in training and testing data. In fact, taking some time to 
design the training, testing, and cross validation procedures can help you clarify the type of data analysis question you are answering
and help you catch mistakes early on. If you are a software developer, a loose comparison to this concept could be test-driven
development: think about how you would test your conclusion first, then design your model.  

## Final remark
I typically find myself working on descriptive, exploratory, inferential, and predictive data analyses. The first two I consider  mandatory
components of broader data analysis projects, and doing a good job on them gives your project a solid foundation for the subsequent
inference and prediction tasks. The latter two require careful consideration of the interplay between the available data, the way
it was obtained, and the adopted models. If you are mindful of the type of question you are asking of the data at any one stage and think
early about testing your models, your overall data analysis will be better positioned to be correct, relevant, and impactful. 

## Resources

1. [What is the Question?](http://science.sciencemag.org/content/347/6228/1314) by  Jeff Leek and Roger Peng.
2. [The Art of Data Science](https://leanpub.com/artofdatascience) by Roger Peng and Elizabeth Matsui.
3. [The Elements of the Data Analytic Style](https://leanpub.com/datastyle) by Jeff Leek.









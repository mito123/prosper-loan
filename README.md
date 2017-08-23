# Data Analyst Nanodegree Project: Explore and Summarise Data

## About this Project

This is a project of the Data Analyst Nanodrgree from Udacity. In this project, the main task is using R to apply exploratory data analysis techniques in order to explore relationships from one variable to multiple variables and to explore a selected data set for distributions, outliers, and anomalies.

EDA (exploratory data analysis) is a very important step in the data analysis process, because it can lead to insights, which may uncover to other questions, and eventually predictive models. It also is an important “line of defense” against bad data and is an opportunity to notice that the assumptions or intuitions about a data set are violated.

**If you are interested in this project, you can read the detailed report [on my website](https://yajiez.me/en/2017/08/23/exploration-of-the-loan-data-from-prosper/).**

## Dataset Information

**Loan Data from Prosper**: Last updated 03/11/2014.

- **Data url**: [Link to Data](https://docs.google.com/document/d/1qEcwltBMlRYZT-l699-71TzInWfk4W9q5rTCSvDVMpc/pub?embedded=true)

This data set contains 113,937 loans with 81 variables on each loan, including loan amount, borrower rate (or interest rate), current loan status, borrower income, borrower employment status, borrower credit history, and the latest payment information.

![img](https://d33wubrfki0l68.cloudfront.net/4fc1665438f94c0400634ca5e293e8a2dfb63f63/7844e/post/2017-08-23-exploration-of-the-loan-data-from-prosper_files/figure-html/plot_three-1.png)

The plot above shows that there is an inverse relationship between ProsperScore and Default Rate, which is no surprise. Also, it shows that how these two indicators change over time.

An important finding is that as time goes by:

- the credit score of the borrowers keep going down;
- the default rate increased quickly from 2010 to 2011;
- the default rate maintained a higher ratio after 2011.

The conclusion is that the risk of the Prosper Loan Business had been higher than the days when it started, so investors should be prudent and thoughtful when they make new investments on this platform.

Read more [on my website](https://yajiez.me/en/2017/08/23/exploration-of-the-loan-data-from-prosper/).

## Reflection of the Analysis

After performed the exploration on this dataset, I found a lot of insights about the loan business. Most of the insights are just the confirmation of the knowledge we already have: such as better credit score and higher income lead to lower default ratio, and different states or different occupations have different default ratio, and so on.

Besides, I have found two interesting insights I haven’t known before:

1. For college students, after they entered into the college, more and more of them may choose to borrow money as time went by, and the higher the grade, the lower the default ratio, with exception for the sophomore students. So why the sophomore students have such a high default ratio? This is an interesting question and I would like to do some research about it in the future.
2. The risk of the Prosper Loan Business has become higher than the days when it started, which is evidenced by the higher default rate and lower ProsperScore than before.

Besides the exploration analysis and visualisation on this dataset, I also built two models to try to predict the default possibility of a certain loan based on the features of the borrower as well as the features of the loan itself.

However, the performance of the models were not good and the reasons are:

1. Feature selection and feature engineering were not performed yet, which play an important role for machine learning models. In fact, the selected features may have some collinearity, because we got the message `prediction from a rank-deficient fit may be misleading` from `predict.lm(object, newdata, se.fit, scale = 1, ...` (perhaps we can also try deep learning to make the feature engineering process automatically);
2. Model parameters were not tuning to achieve the potential highest performance of the model, and other models such as GBRT and Random Forest should be tested as well.

Also, there are sereval issues that should be addressed in the future:

1. In the model training part, I randomly chose 80% of the data as train data and use the left 20% of the data as test data, which seems reasonably at first. However, if we think about our target problem carefully, we may notice that once we have a model we need use it to predict the future outcome of the currently unfinished loans. So, we are forecasting the future. And for this kind of the problem, the test daatset should be the recent part and the train dataset should be the older part of the whole dataset. We can also use the moving time window technique to generate the train and test dataset;
2. Predict whether a loan will default or not is really a difficult task because this is predicting the future, and the future is definitely full of the uncertainty. For example, even a borrower with low income may repay his(her) debt on time if he has be abitily to clear the debt when it matures, conversely, even a borrower with high income may defualt on his(her) loan if he(she) has some financial difficulties when the debt matures. In addition, even for the same borrower, the default possibility may be different for different loans just because the consequence of default are different for different loans (ie. mortgage loan vs. credit card).
3. From final plot 3 we see that the default ratio for all the loans changes over time, which means besides the features of the borrower and the features of the loan itself there are some other time-related features have impact on the defualt possibility: the Macroeconomic Condition and Currency Policy of differnent time periods. Therefore, if we really want to build a model which can be used in the real world, we should take the Macroeconomic Condition and Currency Policy into consideration as well as the features about the borrowers and the loan.

## References

- https://www.udacity.com
- https://udacity.github.io/git-styleguide/
- https://briatte.github.io/ggcorr/#controlling-the-coefficient-labels
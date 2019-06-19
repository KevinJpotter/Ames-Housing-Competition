# Ames Housing Kaggle Competition

Problem Statement:

As part of my Data Science Immersive course I was given one week to work with the Ames housing dataset and go through the full data science process. The task was to clean the data, remove columns with null values, and create a model using only linear regression to predict the sale price of a home. 

Feature engineering and slection were the main focuses of the exercise. I was allowed up to 10 submission to kaggle per day for the week, final class rankings were released at the end of the week. The following notebooks outline the steps I took, tools I used, and thought process behind completing the task.

### Data Cleaning

To clean the data I created several simple functions so the process could be completeed easily on the holdout dataset as well. The first step was to find a drop the columns with null values. This was part of the rules of the competition for our cohert. 


There were a number of columns that needed to be converted from strings to floats. To do this I used two methods, for columns where an ordinal scale could be used, I replaced the values to scaler from 0 - n (number of outcomes). For columns where there was no discernable scale, I created dummy columns.

###  Modeling

To compare models and improve upon performance I created a class to be able to evaluate and tune my models. The class takes in the X and y to be tested at instantiation, then the parameter grid to tune over when the model is called. 

Before the model is ran through the gridsearch it is put into a pipeline where the features are standard scaled and polynomial features are created. When gridsearching the optimiazation metric is mean squared error (metric the contest is being judged on).

The class stores an optimal model for both Lasso and Ridge so it can be used on holdout data and submitted to kaggle. The model prints the following metrics to judge performence, root mean squared error, and the r2 for both training and test data.


### Feature Engineering & Selection

To improve model performance I had to reduce existing number of featrues and creat new ones. The process I chose for reducing the number of featrues was to look at correlation to sale price. I created a function that takes in the dataframe and a correlcation coefficeient and outputs a list of columns with an absolute value above the input. After moving the coeffieceitn aroun I found .3 to provide me with the optimal model.

In creating new features I intuitivley and at random multiplited and divided features then tested them against my baseline. I would not use the feature unless the resulting feature had a correlation greater then its parts.

### Dependencies

- [Pandas](https://pandas.pydata.org/)
- [Scikit-learn](https://scikit-learn.org/stable/)
- [Numpy](http://www.numpy.org/)
- [Seaborn](https://seaborn.pydata.org/)
- [Matplotlib](https://matplotlib.org/)

Helpful links:
- [EDA Notebook](https://github.com/KevinJpotter/Ames-Housing-Competition/blob/master/code_data/01-EDA.ipynb)
- [Modeling Notebook](https://github.com/KevinJpotter/Ames-Housing-Competition/blob/master/code_data/02-Modeling.ipynb)
- [Slide Deck](https://github.com/KevinJpotter/Ames-Housing-Competition/blob/master/slide_deck/ames_slides.pdf)

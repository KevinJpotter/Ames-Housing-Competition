
# Modeling Housing Data to predict Price


Create a model from various features of a home to predict the price it would sell for. 


The data used was on houses in Ames Iowa, the first step was to load in the data set and do exploratory data analysis. I eliminated any column containing a null value so , linear regression could be used to create the model. I looked at the distribution within each column and also got rid of each column with no variability within the distribution. The rule I used was any column with over half of the houses containing the same feature, I would exclude the column. 


To create features, I used one hot coding for features that could not otherwise be converted to an ordinal scale. I then applied a correlation mask comparing the correlation of each column to price starting at an absolute value of .3 or greater. I then began combining features with a mix of intuition and some at random to see how the result would correlate. If the result had a correlation greater than each of the starting two on their own I would use the new created column. The result was three characteristics using interaction. I checked the resulting columns against the originals for correlation and decided to remove the originals from the model to avoid issues of collinearity.


For the model I created a pipeline applying a standard scaler to the columns and polynomial features to expand the breadth of the model. I used primarily ridge and lasso regression to fit the data comparing both on each change to the model to maximize performance. I also used a grid search on the parameters of alpha for the regressor, and degree for the polynomial features transformer. I started with a model with one feature added and subtracted features using the process outlined above and checking the model and scoring it with mean squared error and r2.  

The resulting model used a correlation mask of .3. It contained fifteen features, three of which were engineered with interaction. The optimal used a ridge regressor, I applied a standard scaler to the columns, polynomial features transformed to the second degree, and an alpha of 498. The model had a root mean squared error of $ 31,598 which means on average the model was off by this amount when predicting price with my test data. It also had a mean absolute error of $ 14,827 leading me to believe the model would perform quite well with actual data. The r2 score of .85 for both my test and training data says that 85%of the variability of the data can be explained through the model and the model performs well on unseen data. The features with the highest coefficients were Overall quality of the home, square footage of the living area, and bathrooms.


In conclusion I believe this model could be use din practice but, would like fully complete data on the garage to potentially use to improve future versions of the model.

slides:
https://docs.google.com/presentation/d/1_nBvQvYTeRRWAhNNXLgJzCjgf4EgABPDwoYZ9-P5hRU/edit?usp=sharing

data
./datasets/sample_sub_reg.csv
./datasets/test.csv
./datasets/train.csv
./datasets/finished_model_.csv



```python

```

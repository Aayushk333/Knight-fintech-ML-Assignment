# Knight-fintech-ML-Assignment


# 1. Dataset Description 

The dataset is divided into 2 parts training csv file and test csv file.The training set contains 82657 training examples while the test set contains 20665 testing examples. There are a total of 12 features for all the training examples. The different features in the dataset are as follows : 

* user_name - user_name of the reviewer
* country -The country that the wine is from.
* review_title - The title of the wine review, which often contains the vintage.
* review_description - A verbose review of the wine.
* designation - The vineyard within the winery where the grapes that made the wine are from.
* points - ratings given by the user. The ratings are between 0 -100.
* price - The cost for a bottle of the wine
* province - The province or state that the wine is from.
* region_1 - The wine-growing area in a province or state (ie Napa).
* region_2 - Sometimes there are more specific regions specified within a wine-growing area (ie Rutherford inside the Napa        Valley), but this value can sometimes be blank.
* winery - The winery that made the wine
* variety - The type of grapes used to make the wine. Dependent variable for task 2 of the assignment


# 2. My Insights

Some actionable insights from the Data provided are : 

1. It is a supervised learning problem as the dataset is labelled and we need to predict the variety of wines(target            variable) using the input variables given in the dataset.
2. The review_description feature can be used to predict the variety of wines using Text classification approach i.e            sequential models can be used.
3. If we take the review descriptions as the input and the variety of wine as the output , then we can observe that there is    a many-to-one relationship as the input are a sequence of words and output is a single class or label. 
4. It is a multi-class text classification problem as there are a total of 28 categories of wine. 
5. By visualizing data with the help of bar graphs, it was observed that the maximum training examples belong to the ‘Pinot    Noir’ class of the wine variety and the minimum belong to the ‘Gamay’ class of the wine variety.
6. Some attributes of the dataset contains NaN or Null values. But our input variable i.e. review_description  contains no      NULL entries. 
7. The review_title feature can be used to extract the vintages. Thereafter we can create a new feature as vintage in the      dataset. Also there are some review titles which do not have a vintage specified. 
8. The country attribute can be converted into a 3-letter or 2-letter country code which can further be assigned a numeric      value to be used as an input variable for predicting the output. (Although I have not used it in this case)

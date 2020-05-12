# Knight-fintech-ML-Assignment


## 1. Dataset Description 

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


## 2. My Insights

Some actionable insights from the Data provided are : 

1. It is a supervised learning problem as the dataset is labelled and we need to predict the variety of wines(target            variable) using the input variables given in the dataset.
2. The review_description feature can be used to predict the variety of wines using Text classification approach i.e            sequential models can be used.
3. If we take the review descriptions as the input and the variety of wine as the output , then we can observe that there is    a many-to-one relationship as the input are a sequence of words and output is a single class or label. 
4. It is a multi-class text classification problem as there are a total of 28 categories of wine. 
5. By visualizing data with the help of bar graphs, it was observed that the maximum training examples belong to the ‘Pinot    Noir’ class of the wine variety and the minimum belong to the ‘Gamay’ class of the wine variety.
6. Some attributes of the dataset contains NaN or Null values. But our input variable i.e. review_description  contains no      NULL entries. 
7. The review_title feature can be used to extract the vintages. Thereafter we can create a new feature as vintage in the      dataset. Also there are some review titles which do not have a vintage specified. 
8. The country attribute can be converted into a 3-letter or 2-letter country code which can further be assigned a numeric      value to be used as an input variable for predicting the output. (Although I have not used it in this case)

## 3. Summary and Model Used 

Neural networks can only learn to find patterns in numerical data and so, before we feed a review description into a        neural network as input, we have to convert each word into a numerical value. This process is often called word encoding or tokenization. The encoding process that I have followed is given below :

* For all of the text data—in this case, the review description—I have recorded each of the unique words that appear in the training set and recorded these as the vocabulary of our model.
* I have encoded each vocabulary word as a unique integer, called a token. Often, these tokens are assigned based on the frequency of occurrence of a word in the dataset. So, the word that appears most frequently throughout the dataset, will have the associated token: 0.
* This word-token association is represented in a dictionary that maps each unique word to their token, integer value.
* Finally, after assigning these tokens to individual words, I have then tokenized the entire corpus.

__Please Note__ : The word tokenized as 1 is not necessary any more similar to the word tokenized as 2 than it is with a word tokenized as 1000. Typical notions of numeric distance do not tell us anything about the relationships between individual words.

So, I have used another encoding step;  one that represents the relationships between words. One such representation is a learned word vector, known as an __*embedding*__. Word embeddings are vectors of a specified length, typically on the order of 100, and each vector of 100 or so values, represents one word. The values in each column represent the features of a word, rather than any specific word. Words that have similar contexts will tend to have embeddings that point in the same direction.

* These word embeddings have been used as an input to a __Convolution Neural Network__ (CNN).
*Convolutional layers are most commonly designed to find spatial patterns in an image by sliding a small kernel window over an image. In the case of text classification, a convolutional kernel is still a sliding window, only its job is to look at embeddings for multiple words, rather than small areas of pixels in an image. To look at sequences of word embeddings, I have taken a window(filter) to look at multiple word embeddings in a sequence. The kernel or filter is a rectangle with dimensions 3*256, where 256 is the embedding length. The CNNs are able to recognise the general patterns in text effectively because :

* similar words have similar embeddings and a convolution operation is just a linear operation on these vectors. So, when a convolutional kernel is applied to different sets of similar words, it produces a similar output value!


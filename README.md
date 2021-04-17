# Tag-Generation

Tag Generation is one of the major applications of Natural Language Processing. There are many possible approaches for same. Our options to solve this problem increase as we move on to Deep Learning solutions. In the given task, I have employed Machine Learning and basic NLP to find an optimal and quick solution. 

My analysis of the problem : 
There were two possible approaches on basis of ML :
1)Not Used : Using the concept of Topic Modelling (algorithms such as LDA) to find the key words. Setting the parameter to a certain amount i.e. if a word occurs around this range. It can possibly be a keyword. However, due to uncertain nature of the case statements, it is fairly possible that is approach would produce a lot of unnecessary words.
2)Used : The Multi-class classification - I utilized this approach to form a unique list of tags used in training set. Vectorized the values in training data set and trained a model to automatically predict values from the existing list for any given statement.

Approaches or attempts that were not successful/feasible :

1)Simple Random Forest Classifier algorithm or OnevsRest Classifier without much hyper-parameter tuning. These algorithms were not predicting any values.
2)Using Bag of Words to vectorize the values in data set
3)Converting the case statements into a string or list and running a loop to find possible matches between the list of tags and the given case statement. 
4)Using hyper-parameter tuned RandomizedSearchCV with Random Forest Classifier or XGBClassifier as base estimator since the model was taking more than an hour to train and was not efficient.

Approach employed :
1)Converted the .txt files into .csv using command prompt.
2)Formulating a data set where tags for each case statement are present in list form.
3)Quick data analysis of tags to find number of overall occurrences of the tags in data set.
4)Cleaning the case statements and removing the stop words.
5)Using Multilabel Binarizer to convert tag values into a multi-class classification problem.
6)Using Tf-Idf vectorization for case statements.
7)Splitting data into Training and Validation data set. (Test size = 0.025 or 2/80)
8)Training a model with RandomSearchCV algorithm which used OneVsRestClassifier as base estimator, f1_micro scoring, l1 and l2 penalty.
9)Testing it on validation data set.
10)Importing the test data set. Creating and implementing a function to clean, vectorize and predict tags based on the model. Saving it to a .csv file.

What can be improved in this approach/Methods that can be tried : 
1)Since, there are only 80 case statements and 1322 unique tags, the training isn’t that efficient. Often, few values are missing from training data set during fitting or excessive tags are predicted (300-400). To resolve this problem, a much bigger corpus can be used and tags can be reduced, so that machine learning can be done more efficiently.
2)Using Word2Vec for vectorization. Employing RNN, sequence models for tag generation. Maybe utilization of ANN with TensorFlow - Keras libraries can improve results. 
3)Testing more variations of hyperparameters can help one train the model better.

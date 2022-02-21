# neural_network_charity_analysis
## Overview  
Given data from a charity that funds various organiztions, the purpose here is to design a binary classifier to predict whether organizations applying for funding will ultimately be successful in the use of those funds to accomplish said goals.  The dataset contains application data from 34000 organizations, including features such as the organization name, asking amount, available income, usage data etc. Furthermore the dataset contains information on whether or not the organization was successful with the funds.  

## Data Preprocessing  
* Target Variable(s):  IS_SUCCESSFUL column  
* Feature Variables(s): NAME, APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, INCOME_AMT, and ASK_AMT columns  
* Variable(s) that should be removed: EIN, SPECIAL_CONSIDERATIONS, and STATUS columns  

## Compiling, Training and Evaluating the Model  
This model utilizes two activation functions, leaky_ReLU for the input and hidden layers, and sigmoid for the output layer since we are training a binary classifier. There are two hidden layers with 120 neurons and an output layer with one unit (22,681 trainable parameters).  The large number of input dimensions following OneHotEncoding necessitates a larger number of neurons in each dense layer (roughly 2x the amount of resulting features).  Additional layers or fewers neurons were found to decrease accuracy due to either to overfitting or insufficient parameters which decreased performance.  

A target performance of at least 75% was desireable based on the dataset and was achieved by making modifications to the input features:   


![accuracy](https://user-images.githubusercontent.com/60231630/154877131-e3f3cfbf-8de4-4762-9ddc-08e7802d8dc7.png)   

Modifications included binning the various features to remove values with outlier frequencies and grouping said categorical counts into a single category. Additional steps including dropping neurons during the training steps to minimize overfitting.  Also, utilized batch normalization and used the he_normal initializer which draws sample random weights from a normal distribution centered at mean 0 for the layers.  

Summary  
In summary the model behaved as expected achieving at least 75% accuracy on the testing dataset although additional methods for improvement still might be beneficial. Of interest would be whether a non-neural network machine learning model might also work here such as RandomForest classifier since our data is tabular and relatively low complexity. A sufficiently deep RandomForest classifier would likely perform as well here.


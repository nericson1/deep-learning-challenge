# deep-learning-challenge

## Overview

Multiple files are contained within this repository that all contribute toward the goal of creating a binary classifier that can be used to predict whether applicants for a nonprofit foundation will be successful. A CSV file, provided by the foundation, is read into a Pandas DataFrame, after which data preprocessing was performed in order to compile, train, evaluate, and optimize a neural network model. 

The ipynb file titled `deep_learning_challenge` is the file containing my initial code which results in a neural network model performing at 73.03% accuracy on the testing dataset. I duplicated this file and renamed it `deep_learning_challenge_optimization` in an effort to continue working on the model to improve it's accuracy, while preserving the highest success rate thus far. On this duplicated model, I tried many methods to optimize it's learning and generate a better accuracy score. After much trial and error, the optimization ipynb results in the best performing model with an accuracy of 73.17% on the testing dataset. Below you can find more details on the data and the optimization methods I tried.

## Results
### Data Preprocessing

- The target variable for this model is whether or not the applicant is successful - represented by the `IS_SUCCESSFUL` column
- The feature variabls for this model are as follows: `APPLICATION_TYPE`, `AFFILIATION`, `CLASSIFICATION`, `USE_CASE`,  `ORGANIZATION`, `STATUS`, `INCOME_AMT`, `SPECIAL_CONSIDERATIONS`, AND `ASK_AMT`.
- The original dataset contains columns `NAME` and `EIN` which were dropped from the initial DataFrame because they are neither targets nor features.
  
<img width="581" alt="Screenshot 2023-11-09 at 5 31 23 PM" src="https://github.com/nericson1/deep-learning-challenge/assets/133588043/599d5a32-cefc-4bde-9ef2-cfc8743ba5b3">

### Compiling, Training, and Evaluating the Model

- In the model with the highest performance, an accuracy score of 73.17%, I used 4 total layers. The first layer contains 43 input features with 45 neurons and relu activation function, hidden layer #2 contains 5 neurons with a sigmoid activation function, hidden layer #3 contains 15 neurons with a sigmoid activation function, and the output layer contains 1 neuron with a sigmoid activation function. It took much trial and error to come to these numbers. I trialed anything between 3 and 10 layers, as well as up to 300 neurons in a given layer or down to 2 neurons in a given layer. I tested various combinations of activation functions, as well as an equation meant to help identify the optimal number of neurons in a model given information about the dataset, yet none of these adjustments brought my accuracy score above the target of 75%.
- In this challenge, I was unable to achieve the target accuracy score of 75% on the testing data.
- After spending many hours trying methods such as dropping various columns (`AFFILIATION`, `USE_CASE`, `ORGANIZATION`, `SPECIAL_CONSIDERATIONS`), increasing and decreasing existing bin sizes for `APPLICATION_TYPE`, `CLASSIFICATION`, and `INCOME_AMT`, creating and removing addition bins in other features, adding and removing neuron quantities, adding and removing hidden layers, using different activation functions, and changing the number of epochs, the best accuracy score I was able to achieve was 73.17%. The image below displays the final model structure.

<img width="617" alt="Screenshot 2023-11-09 at 5 33 02 PM" src="https://github.com/nericson1/deep-learning-challenge/assets/133588043/34f8f2c1-a26a-407f-a9e5-93d52bbfcc4a">

### Summary

Overall, my neural network model did not achieve the level of success that I was striving for. I think that given more time to conduct research and continue the trial and error process, I could have met the 75% success benchmark. What the current model does show is that when given 75% of the whole dataset for training, the model can 'learn' from that data and use the network developed to predict with 73% accuracy if the applicant will be successful or not. These predictions are made on the remaining 25% of the dataset used for testing. Creating this model involved the use of Pandas, SKLearn, and Tensorflow - specifically the keras libary.

I believe a Logistic Regression model may be a good option for solving this classification prediction scenario with a higher level of accuracy than I was able to attain with this neural network. A logistic regression model only generates a binary outcome which is all that is needed by the foundation providing the dataset. We must consider the reason for creating a model which is to create a binary classifier that can predict whether an applicant will be successful, and because of this I believe that a logistic regression approach has potential for success.

## References

While creating this model I wanted a way to generate checkpoints and track what the hightest accuracy score was through the epochs. I used the link below in my code prior to training the model. This generates a model checkpoint h5 file as well as prints whether or not the accuracy improved from the previous epoch.

Link: https://medium.com/@italojs/saving-your-weights-for-each-epoch-keras-callbacks-b494d9648202

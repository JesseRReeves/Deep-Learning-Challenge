                                    --Overview--
    
    The purpose of this analysis is to create a tool for a nonprofit foundation called Alphabet
Soup that predicts which applicants will be successful if funded. We are given a CSV file containing more than 34,000 organizations that have received funding from Alphabet Soup over the years.  Within this dataset there are a number of columns that capture metadata about each organization.  Using this information we are making a machine learning model using neural networks that can predict accurately whether or not an organization will be successful if funded.

Target Variable:
-IS_SUCCESSFUL—Was the money used effectively:  This is what we want our predictive output for our model to be.

Feature Variables:
-APPLICATION_TYPE—Alphabet Soup application type
-AFFILIATION—Affiliated sector of industry
-CLASSIFICATION—Government organization classification
-USE_CASE—Use case for funding
-ORGANIZATION—Organization type
-STATUS—Active status
-INCOME_AMT—Income classification
-SPECIAL_CONSIDERATIONS—Special considerations for application
-ASK_AMT—Funding amount requested

Variables Removed from Model:
-EIN and NAME—Identification columns

                        --Compiling, Training, and Evaluating the Model--


** Model One:  I ran a kerastuner to find out the best model to run.
-neurons: 34
-Layers: 6
-Activation Function: Relu 
![Snippet of Code](Screenshot (121).png)
Function: Relu.  The keras tuner model said this was the optimal Function to use.

Model Two:
-Layers: Three.  I decided to test my model using more hidden layers and nodes, to see how this would effect the accuracy score.
-Hidden Layer: 



NOTE: I started by using Google Colab.  However, halfway through my work it gave me messages saying I used all available RAM and had to upgrade to Google Colab pro.  So I switched to Jupyter Notebook.

    I was able to achieve the target model performance by my third model.  The first training test
used 8 nodes for hidden layer one, and five nodes for hidden layer two.  I ran keras tuner to figure out the optimal number of hidden layers and neurons.  Also, the columns EIN and NAME were dropped, and columns CLASSIFICATION and APPLICATION_TYPE were binned.  This model had an accuracy score of 73%, so this model did not meet the criteria of 75% accuracy.  On the second model, I added a third hidden layer with six nodes and increased the amount of nodes on layer two to six.  This was done to see how the model would work with more nodes.  This resulted in only a 72% accuracy.  Realizing more nodes didn't equal better outputs with the dataset available, I decided to add more data into our inputs, by adding back in the column NAME to our dataframe.  I also got rid of the third hidden layer and changed my nodes on hidden layer two back to five.  I had to add regularizers to both hidden layers to avoid overfitting, as well as a Dropout(0.02) to the output.  This resulted in a predictive accuracy of 78%.  Thus I had a model that was above 75%.

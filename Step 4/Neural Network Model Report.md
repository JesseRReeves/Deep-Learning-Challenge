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
-neurons: 34.  This was the optimal amount of nodes to use according to my kerastuner test.
-Layers: 6  This was the optimal amount of layers to use according to my kerastune test.
-Activation Function: Relu.  The keras tuner model said this was the optimal Function to use.
![alt text](Step 4/Screenshot (121).png)

** Model Two:
-Neurons: 20.  I decided to use less nodes to test how this would effect the accuracy score.
-Layers: 3.  I decided to test my model using less hidden layers to see how this would effect the accuracy score.
Activation Function: Relu. The keras tuner model said this was the optimal Function to use.
![alt text](Step 4/Screenshot (125).png)  ![alt text](Step 4/Screenshot (123).png)
** Model Three:
Neurons: 13.  Since more nodes did not mean much difference in accuracy, I decided to lower the amount even more.
Layers: 2.  Since more layers did not mean much difference in accuracy, I decided to have only two layers.
Activation Function: Relu.  I decided to use Relu since my keras tuner test had decided this was the optimal Function to use.
![alt text](Step 4/Screenshot (124).png)  ![alt text](Step 4/Screenshot (125).png)



NOTE: I started by using Google Colab.  However, halfway through my work it gave me messages saying I used all available RAM and had to upgrade to Google Colab pro.  So I switched to Jupyter Notebook.

--Summary--


    I was able to achieve the target model performance by my third model.  The first training test
used 7 nodes for hidden layer one, and 3 nodes for hidden layer two, 5 nodes for layer three, 5 nodes for layer four, 5 nodes for layer 5, and 9 nodes for layer 6.  I ran keras tuner to figure out the optimal number of hidden layers and neurons.  Also, the columns EIN and NAME were dropped, and columns CLASSIFICATION and APPLICATION_TYPE were binned.  This model had an accuracy score of 72.24%, so this model did not meet the criteria of 75% accuracy.  On the second model, I had three hidden layers.  The first layer had 8 nodes, the second layer had 6 nodes, and the third layer had 6 nodes.  This was done to see how the model would work with less layers and less nodes.  This resulted in only a 72% accuracy.  Realizing less nodes didn't equal better outputs with the dataset available, I decided to add more data into our inputs, by adding back in the column NAME to our dataframe.  I also got rid of the third hidden layer and changed my nodes on hidden layer one to 8, and hidden layer two to 5.  I had to add regularizers to both hidden layers to avoid overfitting, as well as a Dropout(0.02) to the output.  This resulted in a predictive accuracy of 78.5%.  Thus I had a model that was above 75%.  A recommendation for a different model that could solve this classification problem would be Random Forest.  It is known for its high accuracy, scalability, and ability to handle large datasets with high dimensionality.  Random Forest could be a better choice for larger datasets with complex relationships between features.

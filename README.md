# Cryptocurrencies and Unsupervised machine learning

Accountability Accounting, a prominent investment bank, is interested in offering a new cryptocurrency investment portfolio for its customers.In this project we will create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.Since the data is not ideal,it will need to be processed to fit the machine learning models.There is no known output we are  looking for,so we will use unsupervised learning.To group the cryptocurrencies we will use a clustering algorithm and visualize the data.

## Result
### A. Preprocessing the Data for PCA

The following tasks are performed to prepprocess the data
#### 1. All cryptocurrencies that are not being traded are removed.
#### 2. All cryptocurrencies that do not have a defined algorithm are removed. 
#### 3. The IsTrading column is dropped .
#### 4. All the rows that have at least one null value are removed .
#### 5. All the rows that do not have coins being mined are removed.
#### 6. Creating a new DataFrame that holds only the cryptocurrency names, and use the crypto_df DataFrame index as the index for this new DataFrame.
#### 7. Removing the CoinName column from the crypto_df DataFrame since it's not going to be used on the clustering algorithm.
#### 8. A new DataFrame is created that stores all cryptocurrency names from the CoinName column and retains the index from the crypto_df DataFrame.
#### 9. The get_dummies() method is used to create variables for the text features, which are then stored in a new DataFrame, X
#### 10. The features from the X DataFrame have been standardized using the StandardScaler fit_transform() function.

### B. Reducing Data Dimensions Using PCA
Using the Principal Component Analysis (PCA) algorithm, we will reduce the dimensions of the X DataFrame to three principal components and place these dimensions in a new DataFrame.
The following code was executed.
![](https://github.com/Akshaya-Kamble/Cryptocurrencies/blob/main/Reference%20images/new%20dataframe.PNG)

### C. Clustering Cryptocurrencies Using K-means
Using the K-means algorithm,we will create an elbow curve using hvPlot to find the best value for K from the pcs_df DataFrame created above. Then, we will run the K-means algorithm to predict the K clusters for the cryptocurrencies data.

#### 1. An elbow curve is created using hvPlot to find the best value for K 
![](https://github.com/Akshaya-Kamble/Cryptocurrencies/blob/main/Reference%20images/elbow.PNG)

#### 2. Predictions are made on the K clusters of the cryptocurrencies data 
![](https://github.com/Akshaya-Kamble/Cryptocurrencies/blob/main/Reference%20images/predictions.PNG)

#### 3. A new DataFrame is created with the same index as the crypto_df DataFrame and has the following columns: Algorithm, ProofType, TotalCoinsMined, 	TotalCoinSupply, PC 1, PC 2, PC 3, CoinName, and Class 
![](https://github.com/Akshaya-Kamble/Cryptocurrencies/blob/main/Reference%20images/delv%202.PNG)

### D. Visualizing Cryptocurrencies Results
Using scatter plots with Plotly Express and hvplot, we have visualized the distinct groups that correspond to the three principal components created in previous steps.then we will create a table with all the currently tradable cryptocurrencies using the hvplot.table() function.

#### 1. The clusters are plotted using a 3D scatter plot, and each data point shows the CoinName and Algorithm on hover
![](https://github.com/Akshaya-Kamble/Cryptocurrencies/blob/main/Reference%20images/3d%20scatter.PNG)

#### 2. A table with tradable cryptocurrencies is created using the hvplot.table() function. 

#### 3. This gives 532 tradable cryptocurrencies.

#### 4. A DataFrame is created that contains the clustered_df DataFrame index, the scaled data, and the CoinName and Class columns 

#### 5. A hvplot scatter plot is created where the X-axis is "TotalCoinsMined", the Y-axis is "TotalCoinSupply", the data is ordered by "Class", and it 	shows the CoinName when you hover over the data point 
![](https://github.com/Akshaya-Kamble/Cryptocurrencies/blob/main/Reference%20images/hvplot.PNG)

## Summary
With the help of Principal Component Analysis (PCA) algorithm and k means algorithm we are able to visualize data and determine the most tradable cryptocurrencies.We were able to find 532 tradable cryptocurrencies which could be a a good potential addition to the investment portfolio. Hence with the help of the unsupervised machine learning algorithms we were able to conclude our findings.

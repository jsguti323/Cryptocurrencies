# Cryptocurrencies

## Overview
Accountability Accounting, a prominent investment bank, is interested in offering a new cryptocurrency investment portfolio for its customers. We have been asked to create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment. To do so, we will preprocess the data for analysis, apply the Principal Component Analysis (PCA) algorithm to reduce the dimensions of the DataFrame, apply the K-means algorithm to predict the K clusters for the cryptocurrencies’ data, then finally visualize the distinct groups that correspond to our  principal components.

## Results

### Preprocessing the Data for PCA
![original_crypto_df](https://user-images.githubusercontent.com/99751636/177620366-25e8668e-a579-47a7-9f62-1dc2d2b2bd3c.png)

* We read the crypto_data.csv file into a Pandas DataFrame.
* Original DataFrame had 1252 rows and 6 columns.

![preprocessed_crypto_df](https://user-images.githubusercontent.com/99751636/177620591-15982b11-31c7-416e-bb5c-70c1f3b73b48.png)

* All cyrptocurrencies that weren't being traded were removed.
* Only cryptocurrencies that had a working algorithm were kept.
* Rows with null values were removed.
* Only rows where cryptocurrency were mined were kept.
* "Coin Name" column was put into separate DataFrame and dropped from current one.
* Preprocessed DataFrame had 532 rows and 5 columns.

![standardized_crypto_object](https://user-images.githubusercontent.com/99751636/177621301-301430e6-8f48-4388-935b-9582006256fb.png)

* Text features in the DataFrame were converted to integers using get_dummies(), raising the column count from 5 to 98.
* Data was standardized using StandardScaler(). 
* The above array is the first object in the DataFrame, as the 98 entries correspond to the 98 coulmns.

### Reducing Data Dimensions Using PCA

![PCA_crypto_df](https://user-images.githubusercontent.com/99751636/177622027-46c95119-e21b-4451-97e4-2b391a71807e.png)

* Principal Component Analysis (PCA) reduced the dimensions from 98 to 3.

### Clustering Crytocurrencies Using K-Means

![elbow_curve](https://user-images.githubusercontent.com/99751636/177622484-bcd6812a-0546-4984-8adc-b7a91ab2839c.png)

* Elbow curve was created to find the ideal value for of K clusters, which appears to be K = 4.

![clustered_df](https://user-images.githubusercontent.com/99751636/177623162-f9d42997-10f3-4be1-96d6-69fd25035d8e.png)

* New DataFrame was formed from concatenating preprocessed crypto DataFrame with the PCA DataFrame, then added the "Coin Name" and "Class" columns.

### Visualizing Cryptocurrencies Results

![3D_scatter](https://user-images.githubusercontent.com/99751636/177623518-19ae51b6-833e-4017-ad93-30336249d9ef.png)

* A 3D-Scatter was created using the PCA data and the clusters

![crypto_table](https://user-images.githubusercontent.com/99751636/177623644-6b876658-570d-4a27-9fbf-9527cfb47236.png)

* A table was created that allows the user to sort by Algorithm, Proof Type, Total Coin Supply, Total Coins Mined, and Class. 
* The "Class" column refers to one of the four clusters this prticular coin has been placed into by the K-means algorithm.

![scatter](https://user-images.githubusercontent.com/99751636/177624303-84eaf5c3-3f25-46d4-bc04-fc811f80333f.png)

* Scatter plot was created where the X-axis is "TotalCoinsMined", the Y-axis is "TotalCoinSupply", the data is ordered by "Class", and it shows the CoinName when you hover over the data point

# Analysis of Value of Bank Customers

I had two datasets:   
First dataset: 
- Date 
- Account ID Number
- Opening Date of Account
- Account Status: Active or Close
- Account Type
- Account Balance at the end of the day     

Second dataset:  
- Account ID Number
- Transaction Amount
- Transaction Category
- Transaction Time  

# Data Primary Analysis
I found one null value, I dropped it since it had no information. 

Feature Introduction:
I introduced 6 features based on my knowledge of bank transactions. 

- Feature 1: The total number of transactions for each account in these three months.
- Feature 2: The amount average of each transaction.
- Feature 3: The variance of amount of the transaction for each customer.
- Feature 4: The average of amount of account balance at end of each day. 
- Feature 5: Account balance variance
- Feature 6: The duration of the account activity, which includes two parts: from the day of account opening to the beginning of the dataset, plus the active dates of accounts in the dataset.  I should convert system date from Gregorian to Jalali to make dataset dates and opening dates of the same type.  

# Scaling 
I scaled financial features using log function and min-max scaling. (I test the model without the scaling I realized that scaling ends in a better clustering)
I scaled active time duration using min-max scaling.   

# Concatenating All Features
I made a dataframe from all features.  
Then, I used scatter_matrix to visualize the features.   

![image](https://user-images.githubusercontent.com/67642255/142835359-83dadd65-ed2f-4d70-a99c-1e94ca6350ee.png)  

# Drop Outliers

I used box plot to show the existence of outliers:  

![image](https://user-images.githubusercontent.com/67642255/142835591-535eb0b4-175a-4ee8-b448-530637ba9aaa.png)   

I used a standard score. Then I dropped those data that correspond to standard scores greater than 3. 
Then, the boxplot become:  

![image](https://user-images.githubusercontent.com/67642255/142836023-69d453f4-1500-4108-bb14-7e6745c716b9.png)   

# Kmean
I used the elbow curve of inertia, to specify the number of clusters: 

![image](https://user-images.githubusercontent.com/67642255/142836468-bd1a4f2b-50c4-4854-887f-aa28b39a1b72.png)
  
  
For clustering kmeans with n=6, we clustered the data. I used the scatter matrix to visualize it: 

![image](https://user-images.githubusercontent.com/67642255/142836735-8b8e65a3-2e29-4a32-958a-981845b2a4fd.png)   


clusters correspond the label=5,6 reperesnt cusstomers, with :
- longer active time
- bigger account balance
- bigger amount of transaction 
- greater number of transaction. 






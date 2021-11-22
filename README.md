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









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

![image](https://user-images.githubusercontent.com/67642255/142855233-7a43cdfa-5f66-4413-b74d-349533669999.png) 

# Drop Outliers

I used box plot to show the existence of outliers:  

![image](https://user-images.githubusercontent.com/67642255/142855346-de9ca099-2255-451b-a0ca-b44f2ca59613.png)   

I used a standard score. Then I dropped those data that correspond to standard scores greater than 3. 
Then, the boxplot become:  

![image](https://user-images.githubusercontent.com/67642255/142855428-670b78ee-2b44-4ecc-9470-3ccbf1b5929f.png)   

# Kmean
I used the elbow curve of inertia, to specify the number of clusters: 

![image](https://user-images.githubusercontent.com/67642255/142855497-b40d0a8f-c873-49b3-8184-7f5a4aa07f75.png)
  
  
For clustering kmeans with n=6, we clustered the data. I used the scatter matrix to visualize it: 

![image](https://user-images.githubusercontent.com/67642255/142855678-125a28ba-399f-4140-9138-1a93377a2f28.png)     


clusters correspond the label=5,6 reperesnt cusstomers, with :
- longer active time
- bigger account balance
- bigger amount of transaction 
- greater number of transaction. 

![image](https://user-images.githubusercontent.com/67642255/142855600-25f42098-e2cf-40e2-b0c8-4143b00668a0.png)  


# Second Kmeans
I did a second kmeans on clusters with label=5,6.
Using Elbow curve, I consider n=3.   

![image](https://user-images.githubusercontent.com/67642255/142856337-00a21841-aa81-435b-b9d3-468f8c1567af.png)    

Then, as we see in this clustering, the cluster with label=2 corresponds, to customers with:   

- bigger account balance
- bigger amount of transaction 

![image](https://user-images.githubusercontent.com/67642255/142857178-206ce98b-d6cc-4c83-8b87-c1b8536a00b1.png)  


# DBSCAN
As a second method, I used DBSCAN. 
I used KNN to specify the value of epsilon:  

![image](https://user-images.githubusercontent.com/67642255/142857063-cd4557a6-a030-4515-aea1-0c157baea075.png)  

DBSCAN on datas resulted in following clustering:

![image](https://user-images.githubusercontent.com/67642255/142857340-0fa13c12-c09d-42f6-aa05-167cb0bb33d6.png)  

Clustering wasn't successful in this method. 







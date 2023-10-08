[⏪ Back to Portfolio](./)
# Business Problem Statement

Customer churn, also known as customer attrition, is a critical metric for businesses in various sectors, especially in the telecom industry. Retaining existing customers is often more cost-effective than acquiring new ones. Therefore, identifying customers who are at risk of churning and taking proactive measures to retain them becomes paramount.

In the telecom industry, where services are often similar across providers, customers tend to switch to another operator quickly. The reasons can range from better price offers, more benefits, better customer service, or even reasons related to handset and network coverage.

In this project, we aim to predict customer churn in the telecom industry using historical data. By leveraging machine learning techniques, we hope to identify patterns and characteristics of customers who are likely to churn. This will enable the telecom operator to take targeted actions and offer incentives to retain these high-risk customers, ultimately reducing customer attrition and maintaining revenue streams.

## Understanding and Defining Churn:

Churn can be defined in various ways, such as revenue-based churn or usage-based churn.
For this project, we will use the usage-based definition to define churn.


```
import pandas as pd

# Load the dataset
telecom_data = pd.read_csv('telecom_churn_data.csv')

# Display the first few rows of the dataset
telecom_data.head()
```



### Checking Missing Values


```
# Calculate the percentage of missing values for each column
missing_percentage = (telecom_data.isnull().sum() / len(telecom_data)) * 100
missing_percentage = missing_percentage[missing_percentage > 0].sort_values(ascending=False)

# Display columns with missing values and their missing percentage
missing_percentage
```



### Handling Missing Values


```
# Drop columns with more than 70% missing values
columns_to_drop = missing_percentage[missing_percentage > 70].index
telecom_data.drop(columns_to_drop, axis=1, inplace=True)

# For numerical columns, impute missing values with the median
numerical_columns = telecom_data.select_dtypes(include=['float64', 'int64']).columns
for col in numerical_columns:
    telecom_data[col].fillna(telecom_data[col].median(), inplace=True)

# For categorical columns, impute missing values with the mode
categorical_columns = telecom_data.select_dtypes(include=['object']).columns
for col in categorical_columns:
    telecom_data[col].fillna(telecom_data[col].mode()[0], inplace=True)

# Check if there are any missing values left
telecom_data.isnull().sum().sum()
```




    0




```
import matplotlib.pyplot as plt
import seaborn as sns

# Set the style of the visualization
sns.set(style='whitegrid')

# Draw a bar plot of 'arpu_6', 'arpu_7', and 'arpu_8' (Average Revenue Per User for months 6, 7, and 8)
plt.figure(figsize=(15, 7))
for month in ['6', '7', '8']:
    sns.kdeplot(telecom_data['arpu_' + month], label='Month ' + month)

plt.title('Distribution of Average Revenue Per User (ARPU) Over Months 6, 7, and 8')
plt.xlabel('Average Revenue Per User (ARPU)')
plt.ylabel('Density')
plt.legend()
plt.show()
```


    
![png](churn_files/churn_7_0.png)
    



```
# Derive new features capturing the change in usage patterns
for col in ['arpu', 'onnet_mou', 'offnet_mou', 'total_og_mou', 'total_ic_mou', 'vol_2g_mb', 'vol_3g_mb']:
    telecom_data[col + '_diff'] = telecom_data[col + '_8'] - ((telecom_data[col + '_6'] + telecom_data[col + '_7']) / 2)

# Display the first few rows of the dataset with the new features
telecom_data[['arpu_diff', 'onnet_mou_diff', 'offnet_mou_diff', 'total_og_mou_diff', 'total_ic_mou_diff', 'vol_2g_mb_diff', 'vol_3g_mb_diff']].head()
```




```
# Calculate the total revenue for the 6th and 7th months
telecom_data['total_revenue_6_7'] = telecom_data['arpu_6'] + telecom_data['arpu_7']

# Determine the 80th percentile value
high_value_threshold = telecom_data['total_revenue_6_7'].quantile(0.8)

# Filter high-value customers
high_value_customers = telecom_data[telecom_data['total_revenue_6_7'] > high_value_threshold]

# Display the shape of the high-value customers dataset
high_value_customers.shape
```




    (20000, 194)




```
# Tag churners based on the given criteria
high_value_customers['churn'] = ((high_value_customers['total_ic_mou_8'] == 0) &
                                (high_value_customers['total_og_mou_8'] == 0) &
                                (high_value_customers['vol_2g_mb_8'] == 0) &
                                (high_value_customers['vol_3g_mb_8'] == 0)).astype(int)

# Display the distribution of churn
high_value_customers['churn'].value_counts(normalize=True)
```




```
from sklearn.preprocessing import StandardScaler, LabelEncoder

# Encoding categorical variables
for col in high_value_customers.select_dtypes(include=['object']).columns:
    le = LabelEncoder()
    high_value_customers[col] = le.fit_transform(high_value_customers[col])

# Scaling numerical features
scaler = StandardScaler()
scaled_features = scaler.fit_transform(high_value_customers.drop('churn', axis=1))
X = pd.DataFrame(scaled_features, columns=high_value_customers.columns[:-1])
y = high_value_customers['churn']

# Display the first few rows of the scaled dataset
X.head()
```




```
from sklearn.preprocessing import StandardScaler, LabelEncoder

# Encoding categorical variables
for col in high_value_customers.select_dtypes(include=['object']).columns:
    le = LabelEncoder()
    high_value_customers[col] = le.fit_transform(high_value_customers[col])

# Scaling numerical features
scaler = StandardScaler()
scaled_features = scaler.fit_transform(high_value_customers.drop('churn', axis=1))
X = pd.DataFrame(scaled_features, columns=high_value_customers.columns[:-1])
y = high_value_customers['churn']

# Display the first few rows of the scaled dataset
X.head()
```



## Model Building

Now that our data is prepared, we'll proceed with building predictive models to identify potential churners. We'll start with a simple logistic regression model as a baseline. Logistic regression is a linear model that predicts the probability of a binary outcome. It's a good starting point for binary classification problems like churn prediction.

After establishing the baseline with logistic regression, we can explore more complex models if needed. Let's begin by splitting the data into training and testing sets and then training a logistic regression model.


```
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import classification_report, confusion_matrix, roc_auc_score

# Splitting the data into training and testing sets (80% train, 20% test)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Initialize the logistic regression model
logreg = LogisticRegression(max_iter=1000, random_state=42)

# Train the model
logreg.fit(X_train, y_train)

# Predict on the test set
y_pred = logreg.predict(X_test)

# Evaluate the model
classification_rep = classification_report(y_test, y_pred)
roc_auc = roc_auc_score(y_test, y_pred)
classification_rep, roc_auc
```




    ('              precision    recall  f1-score   support\n\n           0       1.00      0.99      1.00      3764\n           1       0.89      0.97      0.93       236\n\n    accuracy                           0.99      4000\n   macro avg       0.94      0.98      0.96      4000\nweighted avg       0.99      0.99      0.99      4000\n',
     0.9793314000612404)




```
from sklearn.ensemble import RandomForestClassifier, GradientBoostingClassifier
from sklearn.svm import SVC
from sklearn.metrics import accuracy_score, classification_report

# Initialize the models
rf = RandomForestClassifier(random_state=42)
gb = GradientBoostingClassifier(random_state=42)
svm = SVC(random_state=42)

models = {'Random Forest': rf, 'Gradient Boosting': gb, 'SVM': svm}
results = {}

# Train and evaluate each model
for name, model in models.items():
    model.fit(X_train, y_train)
    y_pred = model.predict(X_test)
    accuracy = accuracy_score(y_test, y_pred)
    results[name] = accuracy
    print(f'{name} Accuracy: {accuracy:.4f}')
    print(classification_report(y_test, y_pred))
    print('---------------------------------------------')

results
```

    Random Forest Accuracy: 0.9990
                  precision    recall  f1-score   support
    
               0       1.00      1.00      1.00      3764
               1       0.98      1.00      0.99       236
    
        accuracy                           1.00      4000
       macro avg       0.99      1.00      1.00      4000
    weighted avg       1.00      1.00      1.00      4000
    
    ---------------------------------------------
    Gradient Boosting Accuracy: 0.9998
                  precision    recall  f1-score   support
    
               0       1.00      1.00      1.00      3764
               1       1.00      1.00      1.00       236
    
        accuracy                           1.00      4000
       macro avg       1.00      1.00      1.00      4000
    weighted avg       1.00      1.00      1.00      4000
    
    ---------------------------------------------
    SVM Accuracy: 0.9760
                  precision    recall  f1-score   support
    
               0       0.99      0.99      0.99      3764
               1       0.79      0.81      0.80       236
    
        accuracy                           0.98      4000
       macro avg       0.89      0.90      0.89      4000
    weighted avg       0.98      0.98      0.98      4000
    
    ---------------------------------------------





    {'Random Forest': 0.999, 'Gradient Boosting': 0.99975, 'SVM': 0.976}




```
from sklearn.metrics import roc_auc_score, precision_score, recall_score

# Predict probabilities for Gradient Boosting model
y_prob_gb = gb.predict_proba(X_test)[:, 1]

# Compute AUC-ROC
auc_roc_gb = roc_auc_score(y_test, y_prob_gb)

# Predict class labels for Gradient Boosting model
y_pred_gb = gb.predict(X_test)

# Compute Precision and Recall
precision_gb = precision_score(y_test, y_pred_gb)
recall_gb = recall_score(y_test, y_pred_gb)

auc_roc_gb, precision_gb, recall_gb
```




    (0.9999279525928061, 0.9957805907172996, 1.0)




```
# Extracting feature importances from the Gradient Boosting model
feature_importances = gb.feature_importances_
features = list(X_train.columns)

# Creating a DataFrame to display feature importances
importance_df = pd.DataFrame({'Feature': features, 'Importance': feature_importances})
importance_df = importance_df.sort_values(by='Importance', ascending=False)

# Displaying the top 10 most important features
importance_df.head(10)
```



## Model Comparison and Feature Importance Analysis

After training multiple models, we compared their performance based on various metrics. Here are the results:

- **Gradient Boosting Model**:
  - **Accuracy**: 99.98%
  - **AUC-ROC**: 99.99%
  - **Precision**: 99.58%
  - **Recall**: 100%

The Gradient Boosting model outperformed the regression model in terms of AUC-ROC, precision, and recall. Given these results, it is recommended to use the Gradient Boosting model for predicting customer churn in this dataset.

Next, we analyzed the feature importance of the Gradient Boosting model to understand which features are most influential in predicting customer churn. The top features provide valuable insights that can be used for decision-making and developing strategies to reduce churn.

## Recommendations Based on Feature Importance

Based on the feature importance analysis from the Gradient Boosting model, here are the top influential features (assuming the previously displayed features are the most influential):

1. **Feature A**: This feature has a high influence on customer churn. (Note: Replace 'Feature A' with the actual feature name once we have the results.)
2. **Feature B**: This feature also plays a significant role in determining churn.
3. **Feature C**: Customers with specific values in this feature are more likely to churn.
... and so on for other top features.

### Actionable Insights:

1. **For Feature A**: Investigate the reasons why this feature has a high influence on churn. Implement strategies to address the specific issues related to this feature.
2. **For Feature B**: Engage with customers to understand their concerns related to this feature. Offer promotions or incentives to retain customers.
3. **For Feature C**: Monitor and analyze customer behavior related to this feature. Provide targeted offers or support to customers who are at risk of churning.
... and similar insights for other top features.

By addressing the concerns related to these top influential features, the company can implement strategies to reduce customer churn and improve customer retention.


```
from sklearn.metrics import f1_score, confusion_matrix

# Compute F1-Score for Gradient Boosting model
f1_gb = f1_score(y_test, y_pred_gb)

# Compute Confusion Matrix for Gradient Boosting model
confusion_gb = confusion_matrix(y_test, y_pred_gb)

f1_gb, confusion_gb
```




    (0.9978858350951374,
     array([[3763,    1],
            [   0,  236]]))




```
# Extracting the top 5 most important features
top_features = importance_df.head(5)
top_features
```



## Recommendations Based on Important Features:

1. **total_og_mou**:
   - Monitor customers with a sudden decrease in outgoing minutes of usage, as they might be at risk of churning.
   - Offer special call packages or discounts to encourage customers to make more outgoing calls.

2. **vol_2g_mb** and **vol_3g_mb**:
   - Customers with a significant drop in 2G or 3G data usage might be dissatisfied with the data services. Investigate potential issues with data speed or coverage.
   - Introduce data booster packs or promotional offers to incentivize customers to use more data.
   - Consider upgrading the network infrastructure to improve data speeds and coverage.

3. **total_ic_mou**:
   - A decrease in incoming minutes of usage might indicate that the customer is using another service more frequently. Engage with such customers to understand their preferences and offer tailored call packages.
   - Ensure call quality is optimal to avoid customers switching to other networks for incoming calls.

4. **monthly_3g**:
   - Customers who have changed their 3G plan might be looking for better data offers. Introduce competitive 3G plans to retain such customers.
   - Consider offering bundled packages that combine call and data benefits to provide better value to customers.

By focusing on these important features and implementing the above recommendations, the company can take proactive measures to address the key factors influencing customer churn and improve customer retention.

[⏪ Back to Portfolio](./)

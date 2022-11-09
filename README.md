# All ino One Place

Create a loyalty program to high-value customers by clustering.

<div align="center">
<img src="https://github.com/smbaptistag/All-in-One-Place/blob/main/images/logo.png" width="400px" border="10px">
</div>
</br>


# 1. BUSINESS PROBLEM.
A UK-based online retail store has captured sales data for different products for the period of one year (November 2016 to December 2017). The organization sells gifts mainly on the online platform. Customers who make a purchase consume directly for themselves. There are small businesses that buy in bulk and sell to other customers through the retail channel.

Find significant customers for the business who make high purchases of their favourite products. The organization wants to roll out a loyalty program to the high-value customers after identification of segments.

# 2. BUSINESS ASSUMPTIONS.

  - Purchases that have unit prices less than 0.04 have been removed from the dataset.
  - The customer's revenue considered takes into account the amount of returned products. The amount of returned products was deducted from revenue.


# 3. SOLUTION STRATEGY

The strategy adopted was the following:

**Step 01. Data Description:** Renaming columns, checking data types, searching for missing values and preliminary statistical description.

**Step 02. Feature Engineering:** Creating new features to improve the dataset for clustering

**Step 03. Data Filtering:** Data containing inputs which does not match to the scope of the project were removed.

**Step 04. Exploratory Data Analysis:** Analyzing the created features and checking the possibility of making a cleaner dataframe for clustering. Creating study spaces with PCA, t-SNE, UMAP and tree-based embedding (supervised model) with a dimensional reducer (UMAP).

**Step 05. Data Preparation:** Rescaling the data for inputing to machine learning model. This step has already been used to process the data used in the study spaces.

**Step 06. Feature Selection:** Not Applied

**Step 07. Hyperparameter Fine Tunning:** Identifying the best k for the cluster taking into account the metric silhouette score. It was used k-Means, GMM (Gaussian Mixture Model) and Hierarchical Clustering.

**Step 08. Machine Learning Modelling:** Training the final model chosen, taking into account the Silhouette Score for a number of clusters that was acceptable for the business (k=10).

**Step 09. Cluster Analysis:** With 10 clusters created, the "Cluster Insiders" it was chosen with the best average revenue and it is represented by 503 customers.

**Step 10. Exploratory Data Analysis for "Cluster Insiders":** The business problem questions were answered in this step.

# 4. TOP 3 DATA INSIGHTS

  - 31% of the dataset is represeted by new customers or customers that just made one order since the registration (this consideration take into account the new ID's that were created for the NA values in the CustomerID feature).
  - Most of customers are from UK and Europe (up to 90%).
  - 503 customers indicated in the insiders cluster represent 28% of annual revenue.

# 5. MACHINE LEARNING MODEL APPLIED

The following machine learning algorithms were used to predict sales:

  - k-Means;
  - Gaussian Mixture Models (GMM);
  - Hierarchical Clustering;


# 6. MACHINE LEARNING MODELO PERFORMANCE
The silhouette score for each model by study space is indicated bellow:

<div align="center">
<img src="https://github.com/smbaptistag/All-in-One-Place/blob/main/images/results_models.png" width="400px" border="10px">
</div>
</br>

As we can see, the best results are found in the models that ran on the UMAP embedding space used on the supervised Random Forest Regressor model. In the supervised model (Random Forest Regressor) the target used was Gross Revenue.

The k-Means of the first table was considered as the final model for a number k = 10. This number of clusters is not the one that presents the best result, but it is considered the best to suit the business problem in question, not showing much difference in terms of Silhouette Score for the best result.

# 7. DEPLOYMENT
It was used AWS plataform (S3, EC2 and RDS) to deploy this project. The following schema was used to deploy this project.

<div align="center">
<img src="https://github.com/smbaptistag/All-in-One-Place/blob/main/images/schema_deploy.png" width="400px" border="10px">
</div>
</br>

# 8. CONCLUSIONS
Clusters represent a great starting point for creating a marketing strategy to improve revenue. Customers that are not included in the “cluster insiders” must be analyzed and it is important to create some trigger to pull them into the “cluster insiders”. With regard to customers who are in the "cluster insiders", strategies should be created in order to increase the volume of their purchases.

# 9. LESSONS LEARNED / NEXT STEPS TO IMPROVE
Clustering problems are an unsupervised problem that doesn't have the right answer. At this point, the best result was selected that should be improved by exploring new features from existing data.

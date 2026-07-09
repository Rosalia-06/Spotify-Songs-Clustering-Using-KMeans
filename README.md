# Spotify-Songs-Clustering-Using-KMeans
K-Means clustering on Spotify songs using audio features to discover meaningful music groups through unsupervised machine learning.



Title -
Spotify Songs Clustering Using K-Means 

Problem statement -
Spotify contains thousand of songs each with different musical characteristics. Grouping these songs according to their characteristics would be very difficult nd also time consuming. The aim of this project is to use the K-Means clustering algorithm to automatically group similar songs together based on their audio features. 
The dataset chosen does not contain any labels so I will usse unsupervised learning for this

Dataset description -
The dataset used in this project is the Spotify Songs Dataset obtained from Kaggle. It contains information about Spotify songs along with various numerical nd categorical features.
Dataset Details:
Total rows before preprocessing: 32,833
Total rows after preprocessing: 32,828
Total columns: 23
Some important features present in the dataset are:
Danceability
Energy
Loudness
Speechiness
Acousticness
Instrumentalness
Liveness
Valence
Tempo
Duration_ms
Track Name
Track Artist
Track Album Name
Playlist Name
Track Popularity
For clustering, only the numerical audio features were selected because K-Means works on numerical data using Euclidean distance.
The following features were removed before clustering:
Track Popularity – It represents how popular a song is rather than its musical characteristics.
Key – Although stored as numbers, it represents musical categories.
Mode – It represents only two categories (Major nd Minor), so it is categorical in nature.
The final features used for clustering were:
Danceability
Energy
Loudness
Speechiness
Acousticness
Instrumentalness
Liveness
Valence
Tempo
Duration_ms
Data preprocessing steps-
The first step is to explore the dataset using functions like head(), info(), describe(), shape etc nd get to know how many features are there, what type of features are present, which are important, nd which features we can neglect, nd also the data types of the observations.
Also, check for the duplicate rows present or any null values present in they dataset.
After applying this, I get it contains 0 duplicate rows nd 5 null values. The dataset contains 32k rows nd dropping 5 rows doesn’t create much difference so I will choose to drop them instead of filling them up. Selected only meaningful numerical audio features for clustering. Removed Track Popularity, Key nd Mode because they were not suitable for clustering. Applied StandardScaler() to standardize all numerical features so that every feature contributes equally during distance calculation.

Exploratory data analysis -
Exploratory Data Analysis (EDA) was performed to understand the dataset before building the clustering model.
The following analyses were performed:
Studied the distribution of numerical features using histogram
Observed whether the data was normally distributed, skewed or contained outliers.
Created a correlation heatmap to understand relationships between all teh numerical features
Identify highly correlated features that could provide similar information.
Verified that there were no duplicate records.
Confirmed that the dataset contained only a very small number of missing values, which were removed.
EDA helped in understanding the characteristics of the dataset nd it was ensure that the data was ready for clustering.

Model used-
So the datset used here is not labelled nd therefore I have to use an unsupervised model for this. So I am using K-Means which is an unsupervised machine learning algorithm which does not need lebelled data. It forms clusters of those observations having similar characteristics or are correlated with each other.
We start by calculating K-Means for different values in the range 1 to 10 nd picking up the best which suits my datstet best.
The algorithm starts by randomly selecting K centroids. Each observation is assigned to its nearest centroid. After that, the centroid positions are updated by calculating the mean of all observations assigned to each cluster. This process continues until the centroid positions stop changing significantly. 
The optimal value of K was determined using both the ‘Elbow Method’ nd the ‘Silhouette Score’, nd by these 2 methods the optimal value of K is calculated as 5.

Training process -
The training process involved fitting the K-Means model on the standardized dataset. Firstly, different values of K were tested using the Elbow Method to observe how inertia changed as the number of clusters increased. As the curve shows a gradual decrease nd smooth curve, I used another method called Sillhoutte method to solve this issue nd get the best value of K. The Silhouette Score was calculated for different values of K to evaluate the quality of clustering.
Although the highest Silhouette Score was obtained at K = 2, the Elbow Method suggested around K = 5. Choosing only two clusters would produce very broad groups, which are less useful nd not a very practical approach for understanding different song characteristics nd grouping different songs according to its characteristics or making a playlist.
Therefore, K = 5 was selected as it provided a better balance between model performance nd practical interpretation.
The final K-Means model was trained using K = 5, nd cluster labels were assigned to every song in the dataset.
To visualize the clusters, Principal Component Analysis (PCA) was applied to reduce the data from 10 dimensions to 2 dimensions.
Evaluation matrices nd results -
Two evaluation methods were used in this project.
Elbow Method-
The Elbow Method was used to identify an appropriate number of clusters by plotting inertia against different values of K.
The graph showed a gradual decrease in inertia, with the curve beginning to flatten around K=5, which indicates that increasing the number of clusters beyond this point resulted in smaller improvements.
Silhouette Score -
The Silhouette Score measures how well-separated nd compact the clusters are.
The highest Silhouette Score was obtained at K = 2. However, using only two clusters would not provide enough meaningful segmentation for a dataset containing more than 32,000 songs.
Therefore, considering both evaluation methods nd the interpretability of the clusters, K = 5 was selected.
After training the final model, five different song groups were obtained.
The clusters were interpreted as:
Cluster 0 – Speech & Rap Tracks
Cluster 1 – Acoustic & Chill Songs
Cluster 2 – High Energy Workout Songs
Cluster 3 – Instrumental Tracks
Cluster 4 – Happy Dance Hits
These clusters showed clear differences in features such as danceability, energy, acousticness, instrumentalness, speechiness nd valence.
Conclusion-
In this project, the Spotify Songs dataset was successfully clustered using the K-Means algorithm.
The dataset was first cleaned, explored nd standardized before applying the clustering algorithm. The Ebow Method nd Silhouette Score were used to determine an appropriate number of clusters. A final model with K = 5 was trained, nd each song was assigned to one of the five clusters.
PCA was used to visualize the clusters in two dimensions, making it easier to understand the grouping of songs. Finally, each cluster was interpreted based on its average feature values, allowing meaningful song categories to be identified.
Overall, this project demonstrated how unsupervised learning can be used to discover hidden patterns in data without using predefined labels.
References -
Spotify Songs Dataset – Kaggle
Scikit-learn Documentation
Pandas Documentation
NumPy Documentation
Matplotlib Documentation
Seaborn Documentation

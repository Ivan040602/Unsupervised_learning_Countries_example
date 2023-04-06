# Unsupervised Learning «Countries dataset»

### Explanatory data analysis:

This dataset is a data set consisting of various characteristics of the countries forming its socio-economic situation. Accordingly, for this dataset, I needed to determine a certain number of country classes according to the criteria corresponding to the "Most developed countries", "Developed countries", "Developing countries" and "Undeveloped countries".
The dataset consists of the following components:
- <b>country</b> - Name of the country
- <b>child_mort</b> - Death of children under 5 years of age per 1000 live births. 
- <b>exports</b> - Exports of goods and services per capital.
- <b>health</b> - Total health spending per capita.
- <b>imports</b> - Imports of goods and services per capita.
- <b>income</b> - Net income per person
- <b>inflation</b> - The measurement of the annual growth rate of the Total GDP life_expec - The average number of years a new born child would live if the current mortality patterns are to remain the same
- <b>total_fe</b>r - The number of children that would be born to each woman if the current age-fertility rates remain the same.
- <b>gdpp - The GDP per capita. <br />

Next, let's look at the dependencies (correlation) between variables using the constructed correlation matrix.<br /> 
The greatest positive correlation can be traced between the variables <b>"income" / "gdpp" </b>and <b>"child_mort" / "total_fer".</b> <br />
This is quite logical because of course the average earnings of the population affects the GDP.
<br/>
<img src="https://imgur.com/owKa8HI.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />
Similarly, infant mortality at an early age, the indicator of which is indicated in this dataset directly depends on the indicator of fertility and fertility, because it is closely related to the institution of the family and its form.
### Principal component analysis:

One may wonder why do we need PCA and why it should be used in this case. <br />

In this case, we need PCA in order to display and reflect patterns by generalising certain parameters.<br /> 
We see that the dataset consists of 9 significant components (all data characteristics except the name of the country). <br />Obviously, it is impossible to visually display such a number of criteria, because the dimension of more than 3 is irresistible visually. 

So the <b>PCA</b> (Principal Component Analysis) in this case is used to reduce the dimensionality of the data.<br /> 
Summing up, we say that this algorithm identifies the main components (here and after PCA - the i-th main component) -<br />  a normalised linear combination of the original variables and sorts them according
to their ability to explain the variance of the original data.<br /> 

In order to analyse the PCA, I have derived a graph that shows how significant the various parameters are for the generalised parameters.
Based on the graph, we can conclude that the following parameters have the least value:

- inflation
- life_expec
- total_fer 
- gdpp<br />

With the help of PCA, I managed to generalise the information into classes fairly accurately, but this algorithm does not imply a high-quality display of information and the creation of its visualisation. That is why we have to apply the K-means algorithm, with the help of which we will be able to visually display the resulting generalised classes for their subsequent division into different clusters.

### K-means clustering:
To begin with, we should remember what the K-means algorithm is. <br /> 
The main idea of this algorithm is that at each iteration, the center of mass for each cluster obtained in the previous step is recalculated, then the vectors are
divided into clusters again according to which of the new centers turned out to be closer according to the chosen metric.<br /> 

Based on this, the question arises how exactly to choose the initial number of clusters that must be specified in this algorithm for this, you can use the leverage method combined with the <b>K-Means</b> fitted algorithm to our data. <br /> 

From the graph, we see that the shortest distance between the two curves and, accordingly, the best distortion score, which determines the required number of separation clusters, occurs when the number of groups is equal to four.
After we have successfully applied the leverage method and predicted classes for each country using algorithms, we see that the model has divided our data into 4 clusters, each of which reflects the received categories of countries according to their level of socio-economic development.<br /> 
<br/>
<img src="https://imgur.com/ePxPJtg.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />
### Hierarchical Clustering / DBscan Clustering:
In order to make sure that the resulting partitioning into clusters is correct, we can apply the hierarchy algorithm reflected using a dendrogram. <br /> 
This algorithm consists in the ordering of data aimed at creating a hierarchy of a tree, nested clusters. 
There are two types of hierarchical separation algorithms: Agglomerative(bottom->up) and Divisive (top->down). <br /> 
In our case, it is more convenient for us to use Divisive Hierarchical Clustering, since this method initially forms one large cluster with all the data and already. Then it splits it into sub-clusters with similar characteristics.
<br/>
<img src="https://imgur.com/42OZgiO.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />
Unlike the previous method, this algorithm divided the dataset into only three classes of countries, and therefore we have an alternative division into clusters.<br /> 

Next, we need to use the third DBscan clustering method. It is a density-based clustering non-parametric algorithm: given a set of points in some space, it groups together points that are closely packed together.
However, this clustering method has divided our data into 2 different classes.<br /> 

In order to understand which clustering method is most applicable to our data and how the source dataset is divided into clusters, it is necessary to use metrics such as <b>Silhouette Score</b> and <b>Davies Bouldin Score</b>.<br /> 

The silhouette score is a measure of how well each data point in a cluster is separated from other clusters. 
This score ranges from -1 to 1, where:<br />   
- -1 indicates that the data point is probably in the wrong cluster, <br /> 
- 0 indicates that the data point is close to the boundary between two clusters, <br /> 
- 1 indicates that the data point is well within its own cluster.<br /> 

The Davies-Bouldin score is a method for evaluating the performance of clustering algorithms.<br /> 
The score is calculated by finding the ratio of the average distance between points in a cluster to the average distance between points in different clusters.<br /> 
<b>The lower the score, the better the clustering result.</b>
As follows our aim was to find the case with the greatest Silhouette score and the lowest Davies-Bouldin score.<br /> 

### Result:<br /> 

As a result, I calculated that such a case is the K-means algorithm. <br /> 
Accordingly, the dataset will be divided into 4 clusters, which respectively represent the folloeing groups:
- "Most developed countries", 
- "Developed countries", 
- "Developing countries", 
- "Undeveloped countries».

### **Project Summary:**

Startup to provide ML solutions in the European Banking Market. Require leveraging information from **call center data** to develop ML models so we can improve success rate for calls to customers for products our clients offer. Design a ML product that offers high success outcomes while offerring interpretability for clients to make informed decisions.

#### **Data available:**

Marketing campaign data of calls made to customers, often multiple times to ensure product subscription, i.e., term deposit. These are short term deposits with maturities from 1 month to a few years, customer cannot withdraw funds without incurring penalties, unless the term has ended. All personal customer information is removed for privacy concerns.

**Attributes:** 
* age: Customer's age (numeric)
* job: Type of job (categorical)
* marital: Marital status (categorical)
* education: Education level (categorical)
* default: Has credit in default? (binary)
* balance: Average yearly balance in euros (numeric)
* housing: Has a housing loan? (binary)
* loan: Has a personal loan? (binary)
* contact: Contact communication type (categorical)
* day: Last contact day of the month (numeric)
* month: Last contact month of the year (categorical)
* duration: Last contact duration in seconds (numeric)
* campaign: Number of contacts performed during this campaign for this client (numeric, includes last contact)

Label to predict: Has client subscribed to term deposit?

Based on data, we will also identify customer segments who are likely to buy the investment product & also what makes the customer buy, what featues are key to focus on?

#### **Problem Breakdown**

3-layered problem: Classification, Supervised & Unsupervised.
- <u>1st Layer</u>: Identify which customers we should make calls to, not related to campaigns.
- <u>2nd Layer</u>: Another ML model, which focus on predicting which customers to keep calling alongside retaining a lot of potential subscribers.
- <u>3rd Layer</u>: Who are our subscribers, only use this data to do customer segmentation.

#### **Success Metrics**

- 1st Model: Recall for Class 1
- 2nd Model: Precision for Class 1


### Project Results:

*  Layer 1: Subscriber Identification
We employed a Bernoulli Naive Bayes model to identify potential subscribers. The model achieved a recall score of 62% for the subscriber class although our F1-score was severly low (~16%), effectively identifying a significant portion of potential subscribers. By focusing on 18,849 customers instead of the entire 40,000, the model enables a reduction of approximately 1,500 hours in call time.

*  Layer 2: Refining Subscriber Predictions
To balance precision and recall, we developed a second model using XGBoost, achieving the following metrics for the subscriber class:

     * Recall: 78%
     * Precision: 48%
     * F1 Score: 59%
     * F2 Score: 69% (emphasizing recall)
     
     * This balance ensures the model identifies a large number of subscribers without overlooking potential customers, while maintaining reasonable confidence in its predictions. Additionally, the non-subscriber precision was 98%, allowing the model to confidently exclude non-subscribers, further optimizing resource allocation.

*   Layer 3: Customer Segmentation
We applied clustering techniques such as K-Means and Hierarchical Agglomerative Clustering (HAC) to segment subscribers and uncover common characteristics. Dimensionality reduction and metrics like the elbow method, silhouette score, and inertia score helped determine the optimal number of clusters.

<u>Key Findings</u>:
 
1. K-Means Clustering:

    1. Cluster 1: Predominantly managerial-level individuals with tertiary education and no prior credit defaults.
    2. Cluster 2: Individuals with secondary education, blue-collar jobs, and more variability in their credit history.
    
    
2. HAC Clustering:

A unique cluster consisting primarily of retired individuals who are generally married, possess secondary education, have no credit defaults, and primarily use mobile communication. This segment represents a significant target demographic.
These insights highlight distinct customer segments, such as managerial-level individuals with high yearly balances and retired individuals with different financial behaviors. However, further refinement of clusters may provide deeper insights.

<b><u>Future Work:</u></b>
To enhance 
the model and segmentation:

    Alternative Clustering Methods: 
    
    Experiment with algorithms like DBSCAN or Gaussian Mixture Models (GMM) to improve cluster separation and discover more nuanced customer segments.
    Enhanced Dimensionality Reduction: Explore advanced techniques for dimensionality reduction to improve clustering performance.
    Integration of Insights: Combine insights from all layers to refine customer targeting strategies.


<b>Conclusion:</b>

Our analysis demonstrates significant time and resource savings for the client by leveraging predictive modeling and clustering. By integrating insights from Layers 1 and 2 with the segmentation findings from Layer 3, the client can focus their efforts on high-value customer segments, increasing efficiency and effectiveness in targeting potential subscribers. Future advancements in clustering and bias correction will further enhance the results.




# Classification_Online_Retail_Customers

<h1> 1. Project Background </h1>

### Overview
- The [dataset](https://archive.ics.uci.edu/dataset/502/online+retail+ii) of this project belongs to a UK-based and registered, non-store online retail company that mainly sells unique all-occasion gift-ware. Many customers of the company are wholesalers. <br>
- The company has significant amounts of data on its customers's sales data that has been previously underutilized. This project applies KMeans clustering to uncover distinct customer segments based on Recency, Frequency, and Monetary Value (RFM). The goal is to support personalized marketing strategies and improve customer retention.

Insights and recommendations are provided on the following key areas:
<ul>
  <li> <strong> Data Cleaning & EDA: </strong> Initial preprocessing to ensure that segmentation is based solely on valid, behavior-linked transactions.
  <li> <strong> Outlier Detection: </strong> Isolation of high-value or anomalous customers whose behavior significantly deviates from typical patterns, with recommendations for individualized follow-up or separate analysis. </li> 
  <li> <strong> Customer Segmentation Analysis: </strong> Identification of distinct customer groups using RFM metrics (Recency, Frequency, Monetary), enabling targeted marketing strategies and personalized engagement. </li>
</ul>

### Project Structure
<ol>
  <li> <code>online_retail_EDA_Cleaning</code>: main script for loading, preprocessing, EDA </li>
  <li><code>unusual_stockcodes</code>: a list contains product codes that were filtered out during data cleaning </li>
  <li> <code>cleaned_df.xlxs</code>: A cleaned dataset after EDA process </li>
  <li> <code>online_retail_Customer_Clustering</code>: main script for featureing engineering, KMmean-Clustering, customer segmentation analysis, and strategy recommendations </li>
</ol>

### Technologies Used: 
<ul>
<li> Python (pandas, seaborn, matplotlib, scikit-learn) </li>
<li> Jupyter Notebook </li>
<li> GitHub for version control and documentation </li>
</ul>

<h1> 2. Dataset Structure </h1>
<p> The company's database structure as seen below consists of a single table with a total row count of 525,460 </p>
<table>
  <tr>
    <th> Columns </th>
    <th> Type </th>
    <th> Description </th>
  </tr>
  <tr>
    <td> <strong> InvoiceNo </strong> </td>
    <td> Nominal </td>
    <td> A 6-digit integral number uniquely assigned to each transaction. If this code starts with the letter 'c', it indicates a cancellation. </li> </td>
  </tr>
  <tr>
    <td> <strong> StockCode </strong> </td>
    <td> Nominal </td>
    <td> A 5-digit integral number uniquely assigned to each distinct product </td>
  </tr> 
  <tr>
    <td> <strong> Quantity </strong> </td>
    <td> Numeric </td>
    <td> The quantities of each product (item) per transaction </td>
  </tr>
  <tr>
    <td> <strong> InvoiceDate </strong> </td>
    <td> Numeric </td>
    <td> The day and time when a transaction was generated </td>
  </tr>
  <tr>
    <td> <strong> UnitPrice </strong> </td>
    <td> Numeric </td>
    <td>  Product price per unit in sterling </td>
  </tr>
  <tr>
    <td> <strong> CustomerID </strong> </td>
    <td> Numeric </td>
    <td> A 5-digit integral number uniquely assigned to each customer </td>
  </tr>
  <tr>
    <td> <strong> Country </strong> </td>
    <td> Nominal </td>
    <td> The name of the country where a customer resides </td>
  </tr>
</table>

<h1> 3. Executive Summary </h1>
<h3> Overview of Findings </h3>

Our customer segmentation analysis identified seven distinct groups based on recency, frequency, and monetary value, revealing critical insights into current business performance.

The largest segment, NURTURE, customers with low overall monetary value and limited purchase history but recent activity, comprises nearly half of our customer base. This suggests strong acquisition but low conversion, highlighting a need for targeted onboarding and engagement strategies.

High-value segments such as DELIGHT, REWARD, and PAMPER, though smaller in size, contribute disproportionately to revenue.

<ul><li>DELIGHT: customers with high recency and frequency, and moderate spend. </li>
<li>REWARD: customers with high recency, frequency, and monetary value, </li>
<li>PAMPER: customers with low frequency but high monetary value and recent activity </li></ul>

These groups should be prioritized for retention efforts, VIP experiences, and personalized loyalty strategies to maximize lifetime value.

Meanwhile, the RE-ENGAGE segment shows signs of low engagement and declining activity, presenting a clear opportunity for reactivation campaigns and win-back messaging.

The following sections will provide a deeper breakdown of each customer segment and outline tailored marketing strategies to maximize lifetime value across the portfolio.

Below is the overview visualization of each cluster performance: 

<br>
<img width="1189" height="989" alt="image" src="https://github.com/user-attachments/assets/04d7462e-9232-4da9-b387-5171b1f6d71f" />

<h1> 4. Insights Deep Dive & Recommendations </h1>
<h3> Data Cleaning & EDA </h3>
Before conducting segmentation, I applied rigorous data cleaning to ensure analytical integrity and removed <strong>~23%</strong> of records from the original dataset due to
</ul>
<li> Null Customer IDs, which prevent linkage to individual profiles. </li>
<li> Irrelevant StockCodes, identified through pattern mismatches and business logic.</li>
</ul>
This filtering step improves the quality and interpretability of downstream clustering by removing noise and ensuring all records reflect real customer behavior.

<h3> StockCode Filtering Logic </h3>
StockCodes are usually five-digit numbers (like product IDs), and some valid ones include extra letters at the end. However, there are several codes that don’t represent actual products or customer purchases. These were excluded from the analysis because they don’t reflect real buying behavior and could distort our insights.

<h3> Customer Outliers Detection </h3>

<img width="1489" height="490" alt="image" src="https://github.com/user-attachments/assets/f0a6671b-ee0f-49da-91e0-9e153f556d2a" />
Outliers in Monetary Value and Frequency are visually evident in boxplots, where a small subset of customers exhibit extremely high spend and purchase frequency, compressing the bulk of the data near the lower end. 

These outliers are not discarded, as they represent high-value, highly engaged customers of the client business. Therefore, another separate analysis was conducted to analyze top-tier customers behaviors without distorting the clustering of the broader population.

<h3> Customer Segmentation Analysis </h3>

<h4> Non-outlier Customers (Core Segments) </h4>

Four distinct customer segments were identified within the non-outlier population using KMeans clustering on RFM metrics  (Recency vs Frequency vs Monetary). By plotting the clusters in a 3D scatterplot, a clear separation between behavioral groups was visualized, each representing a unique stage in the customer lifecycle.

<img width="794" height="812" alt="image" src="https://github.com/user-attachments/assets/4f4cd814-65e7-4b30-aee8-a7f6522fbb39" />

To further understand the distribution and variability within each segment, violin plots were created for each dimension. 
<img width="1189" height="1790" alt="image" src="https://github.com/user-attachments/assets/3f93ce0d-3061-48c9-87c9-b7b90de8f846" />

This revealed:
<ul>
<li> Some customers buy frequently and spend consistently, these are our loyal core. </li>
<li> Others are newer or less engaged, with more scattered behavior, these are our growth opportunities. </li>
</ul>
The visual charts demonstrate patterns that simple averages would miss, like whether a group has steady spenders or just a few big buyers.

This analysis allows us to tailor strategies for each group, as shared below

| Label | Cluster Color | Segment Name               | Rationale                                                                 | Strategy                                                                 |
|-------|------------------|----------------------------|---------------------------------------------------------------------------|--------------------------------------------------------------------------|
| 0     | 🔵 Blue         | Consistent Buyers - Retain | Repeat purchasers with consistent behavior, though not always recent      |Loyalty programs, exclusive offers, and ongoing communication</span> |
| 1     | 🟠 Orange       | Low-Engagement Buyers - Reactivate | Minimal history and low activity, but potential if re-engaged         |Personalized outreach, limited-time offers, and reminder messaging</span> |
| 2     | 🟢 Green        | Early-Stage Buyers - Nurture | Recently engaged, low value and frequency; likely new customers           |Relationship-building, standout service, and thoughtful incentives</span> |
| 3     | 🔴 Red          | High-Value Loyalists - Reward | Frequent, high-value purchases and strong engagement; critical segment    |Premium loyalty programs, exclusive perks, and personalized recognition</span> |

<h4> Outlier Customers (High-Impact Segments) </h4>

Outlier customers were identified as those with exceptionally high spend or purchase frequency, far beyond the typical range. While they represent a small portion of the customer base, their behavior is critical to understand because they contribute disproportionately to revenue and may require specialized engagement.

To explore these customers, the same clustering approach was used as with core segments, but focused only on the outlier group. To visualize their behavior, 3D chart was created (Recency, Frequency, Monetary), which revealed distinct patterns, some were frequent buyers with moderate spend, while others made fewer purchases but spent large amounts.
<img width="793" height="812" alt="image" src="https://github.com/user-attachments/assets/51c9d379-669d-4a20-917f-6f24ee68915c" />

Then, violin plots were used to examine each cluster’s spread:
<img width="1189" height="1790" alt="image" src="https://github.com/user-attachments/assets/e748bd99-6363-4499-909d-ace759e0e615" />

These visualizations help generate more thoughtful strategies for high-impact customers, as shared below:
  
| Label | Cluster Color | Segment Name                  | Rationale                                                                 | Recommended Strategy                                                                 |
|-------|----------------|-------------------------------|---------------------------------------------------------------------------|---------------------------------------------------------------------------------------|
| -1    | 🟣 Purple       | High-Spend Infrequents - Pamper | Significant spenders with low purchase frequency and high recency; valuable but sporadic |Curate exclusive offers, concierge-style service, and personalized outreach. Use predictive modeling to gently re-engage.</span> |
| -2    | 🟡 Yellow       | Frequent Frugals - Upsell       | Highly engaged with frequent purchases but low spend; low recency suggests recent activity |Introduce tiered loyalty programs, product bundles, and cross-sell nudges. Emphasize value to grow basket size.</span> |
| -3    | 💗 Magenta      | Top-tier - Delight         | Top-tier customers with high spend and frequency; low recency indicates strong recent engagement |Launch VIP tiers, early access to launches, and personalized thank-you campaigns. Explore co-creation and feedback loops.</span> |


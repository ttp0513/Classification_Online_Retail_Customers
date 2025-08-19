# Classification_Online_Retail_Customers

<h1> 1. Project Background </h1>

### Overview
- The [dataset](https://archive.ics.uci.edu/dataset/502/online+retail+ii) of this project belongs to a UK-based and registered, non-store online retail company that mainly sells unique all-occasion gift-ware. Many customers of the company are wholesalers. <br>
- The company has significant amounts of data on its customers's sales data that has been previously underutilized. This project applies KMeans clustering to uncover distinct customer segments based on Recency, Frequency, and Monetary Value (RFM). The goal is to support personalized marketing strategies and improve customer retention.

Insights and recommendations are provided on the following key areas:
<ul>
  <li> <strong> Customer Segmentation Analysis: </strong> Identification of distinct customer groups using RFM metrics (Recency, Frequency, Monetary), enabling targeted marketing strategies and personalized engagement. </li>
  <li> <strong> Behavioral Patterns by Cluster: </strong> Evaluation of purchasing behavior across segments, highlighting differences in order frequency, spending habits, and recency of transactions. </li>
  <li> <strong> Outlier Detection: </strong> Isolation of high-value or anomalous customers whose behavior significantly deviates from typical patterns, with recommendations for individualized follow-up or separate analysis. </li> </ul>
</ul>

### Project Structure
<ol>
  <li> <code>online_retail_EDA_Cleaning</code>: main script for loading, preprocessing, EDA </li>
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
<br>
Below is the overview visualization of each cluster performance: 

<br>
<img width="1189" height="989" alt="image" src="https://github.com/user-attachments/assets/04d7462e-9232-4da9-b387-5171b1f6d71f" />

<h1> 4. Insights Deep Dive </h1>
<h3> Customer Segmentation Analysis </h3>

6. Recommendations

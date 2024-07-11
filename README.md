# **Supermarket Customers Analysis**

**Outline:**

1. [**Business Background & Problem**](#Business-Background-&-Problem)
2. [**Data Cleaning and Understanding**](#Data-Cleaning-and-Understanding)
3. [**Data Analysis**](#Data-Analysis)
4. [**Conclusion & Recommendation**](#Conclusion-&-Recommendation)
5. [**Dashboard Visualization**](#Dashboard-Visualization)

**Tools:** Python & Tableau<br>
**Dataset:** Supermarket Customers

---

# **Business Background & Problem**

---

## Business Background

The supermarket is facing several challenges, particularly due to shifts in customer behavior and expectations. To align with customer preferences, supermarkets must undergo a transformation. If handled effectively, these challenges can open new opportunities for supermarkets and customer product companies to sustain profitability and satisfy customer demands.

By analyzing detailed customer data on segmentation, product purchasing history, performance of the marketplace or store, responses to marketing campaigns, and acceptance of complaints, the goals of supermarket is setting strategies `to gain customer loyalty, increase sales, and optimize promotion to boost supermarket profits.`

## Problem

Some of the problems that will be analyzed in this project include:

**Customer Segmentation**
1. What is the total number of customers? 
2. Which group (Age_Group, Education, Marital_Status, Income, and Child_Status) has the highest and lowest total number of customers? 

**Product Sales**
1. How much of customers who are active and passive in making purchases? 
2. Is there a correlation between active/passive customers and filing complaints? 
3. What type of product has the highest and lowest total sales?
4. Is there a correlation between Income and sales of each product type? 
5. Is there a correlation between Age_Group and sales of each product type? 

**Store & Marketplace Performance**
1. Which of the Website, Catalog, and Store has the highest and lowest percentage of total purchases?
2. What is the total purchases based on Age_Group for each marketplace/store?
3. What is total number of website visits in the last month?
4. Is there a correlation between website visit frequency and the number of purchases via the website? 

**Promotion Effectiveness**
1. Which campaign yields the highest and lowest accepted offer customers? 
2. What is the total purchase of each product type obtained from each type of campaign? 
3. Is there a correlation between NumDealsPurchases (purchases with discounts) and number purchases in each place?  

**Complaint Handling**
1. How much the total of customers with complain and without complain?
2. Which customers group (based on Age_Group, Education, Income, and Child_Status) frequently complains? 
3. What is the total purchase from customers who complain for each product type?  
4. What is the total number of purchase from customers who complain for each type of marketplace (Website, Catalog, and Store)?

---

# **Data Cleaning and Understanding**

---

## Import & Understanding Data

Raw data imported for cleaning:

https://github.com/ashalaisyar/Supermarket-Customers-Data-Analysis/blob/main/Supermarket%20Customers.csv

Data about supermarket customers in 2012-2014 with a total of 2240 rows. 

Data Dictionary / Column Description:

**People**:
* ID: Customer's unique identifier
* Year_Birth: Customer's birth year
* Education: Customer's education level
* Marital_Status: Customer's marital status
* Income: Customer's yearly household income
* Kidhome: Number of children in customer's household
* Teenhome: Number of teenagers in customer's household
* Dt_Customer: Date of customer's enrollment with the company
* Recency: Number of days since customer's last purchase
* Complain: 1 if the customer complained in the last 2 years, 0 otherwise

**Products**
* MntWines: Amount spent on wine in last 2 years
* MntFruits: Amount spent on fruits in last 2 years
* MntMeatProducts: Amount spent on meat in last 2 years
* MntFishProducts: Amount spent on fish in last 2 years
* MntSweetProducts: Amount spent on sweets in last 2 years
* MntGoldProds: Amount spent on gold in last 2 years

**Promotion**
* NumDealsPurchases: Number of purchases made with a discount
* AcceptedCmp1: 1 if the customer accepted the offer in the 1st campaign, 0 otherwise
* AcceptedCmp2: 1 if the customer accepted the offer in the 2nd campaign, 0 otherwise
* AcceptedCmp3: 1 if the customer accepted the offer in the 3rd campaign, 0 otherwise
* AcceptedCmp4: 1 if the customer accepted the offer in the 4th campaign, 0 otherwise
* AcceptedCmp5: 1 if the customer accepted the offer in the 5th campaign, 0 otherwise
* Response: 1 if the customer accepted the offer in the last campaign, 0 otherwise

**Place**
* NumWebPurchases: Number of purchases made through the company’s website
* NumCatalogPurchases: Number of purchases made using a catalog
* NumStorePurchases: Number of purchases made directly in stores
* NumWebVisitsMonth: Number of visits to the company’s website in the last month

## Data Cleaning

**Drop Unused Column**
    - Drop columns that are not in the column description (drop 'Z_CostContact' and 'Z_Revenue' columns).

**Handling Missing Value**
    - There are 24 missing values ​​in the 'Income' column, decided to fill ​​with the median based on Age Group (because Income, which is data that is not normally distributed, is most correlated with Age Group compared to the others).

**Handling Outliers**
    - Several features 'Age', 'Recency', 'Income', and all columns regarding products and places will be checked to see the distribution of outliers. After analyzing with a boxplot, it is known that only 'Age' and 'Income' need to be removed as outliers.

**Feature Engineering : Create new columns for analysis assistance**
1. Income_Group
    - 0 - < 1146 as 'Low'
    - 1146 - < 4516 as 'Lower Middle'
    - 4516 - < 14006 as 'Upper Middle'
    - 14006 < 113735 as 'High'
2. Active_Customer
    - Active = the last time they made a purchase was <= 90 days
    - Passive = the last time they made a purchase was > 90 days
3. Child_Status (Kidhome + Teenhome)
4. Age (Date of customer's enrollment with the company - Year Birth)
5. Age_Group
    - 13 <= Age < 20 as 'Teen'
    - 20 <= Age < 40 as 'Adult'
    - 40 <= Age < 60 as 'Middle Age Adult'
    - 60 <= Age < 75 as 'Senior Adult / Elder'
6. Education_Lvl
    - Basic = 1
    - Graduation = 2
    - 2n Cycle or Master = 3
    - PhD = 4
7. AgeGroup_inSymbol
    - Teen = 1
    - Adult = 2
    - Middle Age Adult = 3
    - Elder = 4

**Replace Inconsistent Value of Data**
1. Marital_Status
    - Replace 'Alone', 'Absurd', and 'YOLO' to 'Single'.
    - Replace 'Together' to 'Married'
2. Education
    - Replace '2n Cycle' to 'Master'

**Check Duplicate**
    - There are no duplicate data.

## Check and Save Clean Data

The data has been cleaned, ready for analysis process. Clean data is in the repository: 

https://github.com/ashalaisyar/Supermarket-Customers-Data-Analysis/blob/main/clean_Supermarket%20Customers.csv

---

# **Data Analysis**

---

In this section the clean data is analyzed using several different analysis techniques. The analysis techniques used include:
1. Descriptive statistics: displays results in the form of numbers, tables and plots/graphs
2. Inferential statistics: conducting correlation analysis between features.

---

# **Conclusion & Recommendation**

---

## Conclusion
**Customer Segmentation**

The most suitable customer segments to target are:
1. Middle Age Adult customer (40 - 59 years old)
2. Bachelor’s degree customer
3. Married customer
4. customer with child
5. High Income Customer, with income range of 14006 - 113734

**Product Sales**
1. Most of customers are active customers who have made purchases in the last 90 days, with a total of 2033 customers (91.21% of total customers), the other 8.79% are passive customers.
2. Customers who complain are not related to passive customers.
3. Wine is a product with the highest total sales, while Fruits is a product with the lowest total sales.
4. Higher customer's income affecting to higher sales of all products, especially for wine and meat products. Customers with higher income more like to buy Wine and Meat products.
5. Customers with higher Age Group more like to buy Wine products.

**Store & Marketplace Performance**
1.  Store has the highest sales performance, while catalog has the lowest sales performance based on the number of purchases by customers.
2. Store is the most preferred place by all customers, Web is the most not preferred place by Teens, and Catalog is the most not preferred place by Adult; Middle Age Adult; and Elder.
3. The total web visit by customers is 11890 times, but customers who visit the web do not immediately make purchases.

**Promotion Effectiveness**
1.  The latest campaign is the most effective campaign for all products based on total purchases by customer, while campaign 2 is the most not effective for all products.
2. All campaigns is the most effective campaign for wine products based on the highest total purchases of wine out of all products.
3. Most purchases with discounts occur more often through website purchases rather than purchases in catalogs and stores.

**Complaint Handling**
1. Total customer with complaint is 20 customer (0.9% of total customer), it shows that most of customer didn't complaint to supermarket.
2. Most complains is from adult customers with high income.
3. If complaints are not handled well, the supermarket will lose revenue soon as much as:
- 3534 from wine products
- 2354 from meat products
- 552 from gold products
- 534 from fish products
- 502 from fruit products
- 364 from sweet products
4. Store has the highest total number of purchase from consumers who complaint.

## Recommendation
**Customer Segmentation**
1. Maintain existing customer segmentation target with the following demographic characteristics:
- Middle Age Adult customer (40 - 59 years old)
- Bachelor’s degree customer
- Married customer
- Customer with child
- High Income Customer, with income range of 14006 - 113734

2. Expanding the reach of customer segmentation that has not yet been achieved based on purchases activity, especially for customers with the following demographic characteristics:
- Teen (13 - 20 years old)
- Basic (high school or below) as last education
- Single as marital status
- Living without child
- Lower Middle Income (1146 - 4515)

**Product Sales**
1. Provide more inventory for high-selling products (wine and meat).
2. Ensure stocks of Gold, Fish, Sweet and Fruits products not exceed those of products with high sales to avoid having an abundance of leftover products, especially fruit products with the lowest sales.
3. The high and low of product sales are closely related to the target customer segmentation that is owned. To significantly increase sales of products other than wine and meat, it is necessary to follow up with expanding customer segmentation.
4. Design a bundle package with a cross combination of products with high sales (wine and meat) and products with low sales (Gold, Fish, Sweet and Fruits). For example, a meat and fruit bundle package.

**Store & Marketplace Performance**
1.  Get customer feedback to increase web performance based on customer experience or implement these steps :
- Improve website navigation, such as offering simple navigation to the main pages, giving filter options (by product, price, etc), and give functional menu (wishlists, add to cart, etc).
- Simplify the check out process
- Accept alternative payment (debit and credit card, e-wallet, etc)
- Offer free shipping for early users.

2. Increase catalog performance through implement these steps :
- create comprehensive product descriptions in digital catalog (price, size, best before date of product, etc)
- Connect website to digital catalog to drive more traffic to website, it can improve its ranking in search engine results and can track which sale was driven by catalog.

3. Maintain store performance and use it to increase product sales :
- Adding an offline marketing (such as poster platform) using weather parameters to increase sales of targeted product, such as summer fruits (berry, mango, papaya, watermelon, etc) is better sold on a hot summer day than on rainy days.

**Promotion Effectiveness**
1. Maintaning the latest campaign as the most affective campaign for all products.
2. Stopping campaign 2 because giving the lowest accepted offer of customer.

**Complaint Handling**
1. Indentificating and getting the reason of complaint from customer feedback, especially for purchasing in store from adult customers with high income as the most customer doing complaint.
2. If it is the customer’s fault, apologizing for the frustration and confusion the customer is facing, after that giving some solutions that customer needs, such as information and explanation for the problem of customer.
3. If it is supermarket's fault (such as product or service failure), offer compensation such as discount 5% for the next purchases.
4. Train and empower employees to handle complaints effectively.
5. Get some feedback or reviews to identify weaknesses of products or services and improve it to prevent complaints on subsequent sales.

Based on those recommendations, supermarket can implement fit segmentation, clear plan of product sales, good performance of the marketplace or store, targetted marketing campaigns, and good response and prevention of complaints, so that supermarket can easily `gain customer loyalty, increase sales, and optimize promotion to boost supermarket profit.`

---

# **Dashboard Visualization**

---

Clean data is also visualized with Tableau in the form of a dashboard. The following is the dashboard link for this project:

https://github.com/ashalaisyar/Supermarket-Customers-Data-Analysis/blob/main/Supermarket%20Customer%20Analytics_Dashboard.twbx

![image](https://github.com/ashalaisyar/Supermarket-Customers-Data-Analysis/blob/main/Dashboard.png)




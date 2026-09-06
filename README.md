# Instacart Customer Segmentation & Behavioral Analysis
*A rule-based segmentation and behavioral analysis project using Instacart grocery sales data.*

## Business Problem 
Customer purchasing behavior widely varies, making a one-size-fits-all approach to marketing and merchandising less effective. **So how can Instacart target the right customers with the right products at the right time?**

This project answers that question by identifying:
- **The Right Segments (Who):** Five distinct behavioral segments built using rule‑based logic grounded in spend, order frequency, number of orders, and basket patterns.
- **The Right Time (When):** Temporal shopping patterns, including a 10 PM dessert window and Friday spend surge, highlight opportunities for time‑sensitive targeting.
- **The Right Products (What):** Product‑level lift analysis reveals which products over‑index at specific times and days of the week, providing insights into product relevance and merchandising opportunities.


## Executive Summary
This analysis builds a clear picture of how Instacart customers shop by combining time‑based shopping patterns, spend behavior, and product‑level lift insights to develop a rule‑based customer segmentation framework. This approach translates raw transactional data into practical business strategies designed to help marketing and product teams improve product relevance, optimize promotional timing, encourage repeat purchasing, and deliver more personalized shopping experiences. 

| Behavioral Segment      | Strategic Opportunity                   |
| ----------------------- | ---------------------------------- |
| **Light Shoppers**      | **Encourage** repeat purchasing to build consistent shopping habits.             |
| **Core Shoppers**       | **Strengthen** existing routines.       |
| **High Spenders**       | **Convert** above average behavior into higher activity levels.      |
| **Stock-Up Shoppers** | **Reduce** friction through automation and predictive replenishment. |
| **Consistent Shoppers**         | **Recognize** and **protect** long-term value.          |


## Data Overview 
This project uses five datasets containing customer, product, department, and historical order data.

All datasets were cleaned, merged, and prepared for analysis in Notebook 1 and Notebook 2. (make the 1 and 2 links to the notebooks in the repository i will add later)

### Datasets

| Dataset | Granularity | Key Attributes | Role in Analysis |  
|---|---|---|---|
| **orders.csv** | Order-level |`order_id`, `user_id`, `order_hour_of_day`, `order_dow`, `days_since_prior_order` | Establishes order timing, frequency, and temporal shopping trends.|
| **products.csv** | Product-level | `product_id`, `product_name`, `department_id`, `price` | Supports product-level lift analysis and maps products to department IDs. |
| **departments.csv** | Department-level | `department_id`, `department` | Maps department IDs to department names. |
| **orders_products_prior.csv** | Product-level | `order_id`, `product_id`, `add_to_cart_order`, `reordered` | Identifies which products were purchased in each prior order. |
| **customers.csv** | Customer-level | `user_id`, `age`,` income`, number of dependents, etc.) | Supplemental dataset created for instructional purposes to support customer segmentation. |


### Engineered Features
To build interpretable segment rules, several customer-level behavioral and demographic feature were derived:
- **Spend Behavior:** total spend, average spend per customer, and spend tier
- **Order Frequency:** average days between orders and order frequency tier
- **Engagement:** observed order count and engagement tier
- **Basket Size:** average number of items per order
- **Demographics:** age group, household composition, and income tier

## Tools 
**Used Python as the primary programming language:**
- **pandas:** Data cleaning, merging, feature engineering, and aggregation
- **NumPy:** Numerical operations 
- **Seaborn & Matplotlib:** Exploratory visualizations
- **Jupyter Notebook:** Analysis, visualizations, and supporting documentation
  
## Methodology
*Rather than using unsupervised clustering, customer segments were defined using **interpretable behavioral thresholds** designed for business usability. This approach ensures transparency and directly ties each segment to observed customer behaviors.*

- **Cleaned and merged** five Instacart datasets, including removing personally identifiable information (PII) and performing data consistency checks.
- Established baseline customer behavior through **exploratory analysis** of spend, order frequency, basket size, and shopping patterns to inform segmentation thresholds.
- **Engineered customer‑level behavioral features** (spend, engagement, order frequency, basket size, and demographics).
- Conducted **temporal analysis by hour of day and day of week**.
- Performed **product‑level lift** analysis to identify time‑specific product preferences. 
- Built **rule‑based customer segmentation** using interpretable behavioral thresholds.
- Translated segment insights into strategic recommendations to support marketing and product decisions.

## Results
### Behavioral Insights 

- **Shopping behavior varies meaningfully by time of day and day of week.**
  - Customers place **80% of orders between 6 AM and 5 PM**, while average spend rises on **Fridays, when basket size is 7.3% higher than on Monday–Thursday** as shoppers prepare for the weekend. 

- **Higher‑value orders occur outside peak shopping hours.** 
  - Despite lower order volume in the evening and overnight hours, **average order value increases between 9–11 PM** peaking at **10 PM**, and again around **4 AM**. Average spend varies more by **day** than by hour, with **Friday ($92.28)** marking the beginning of a clear rise in weekend spend, while **Tuesday ($80.75) remains the lowest**.

- INSERT LINE CHART SIDE-BY-SIDE -
Average Spend by Hour of Day + Average Spend by Day of Week (side‑by‑side) 
(that visually proves that shopping behavior changes dramatically throughout the day)
These distinct temporal patterns highlight opportunities for more contextually timed merchandising and relevant product recommendations.

- **Product demand patterns align with spending peaks.** 
  - Lift analysis shows that **frozen desserts over‑index in the evening (6–11:59 PM)**, coinciding with the 10 PM spend peak, while **grocery staples like produce and milk over‑index overnight (12–5 AM)**, aligning with the 4 AM peak. These **time‑specific product preferences** can help make merchandising more relevant to when customers are most likely to shop based on what they are purchasing.

- **Demographics show limited differentiation in product behavior**
  - Age, household type, and income show minimal variation in department‑level purchasing, supporting a behavior-first segmentation approach as demographic attributes alone do not explain meaningful differences in shopping patterns or spend.
 

### Customer Segmentation Results
Rule‑based segmentation identifies **five distinct customer groups** based on differences in number of orders, spend, basket size, and order frequency patterns.

- INSERT VISUAL CHART SIDE-BY-SIDE -
[segment distribution + estimated spend share visual]

Although **Light Shoppers (7.0%)**, **High Spenders (7.1%)**, and **Consistent Shoppers (6.8%)** make up similar shares of the customer base, yet contribute substantially different shares of revenue.

For example, **Consistent Shoppers represent less than 7%** of customers yet generate **21.0% of estimated spend**, compared with **9.0%** from **High Spenders** and just **0.5%** from **Light Shoppers.** 

This contrast shows that **customer share alone does not directly translate into business value**. **Behavioral segmentation makes these gaps visible** helping teams prioritize where to focus time and resources to deliver more relevant experiences and grow customer value.


## Strategic Recommendations
These insights reveal opportunities to improve customer engagement and value by aligning the Instacart experience more closely with how customers actually shop. <br>
*A full list of segment‑level recommendations can be found at the end of Notebook 3 (add link), including additional strategies that address micro‑behaviors beyond the core segments.* 

**Optimize Time‑Based Merchandising & Personalization** <br>
Align recommendations, merchandising, and app layout with demonstrated **time‑of‑day and day‑of‑week** shopping patterns.

- **Evening (6–11:59 PM):** Surface frozen desserts such as ice cream, frozen yogurt, and gelato along with occasion‑based bundles like “Movie Night” or “Self-Care Days”, to shift merchandising from individual products toward occasion-based shopping. This can encourage larger baskets while capitalizing on higher evening spending.
- **Overnight (12–5 AM):** Proactively promote frequently purchased staples such as lactose-free milk, spinach, and egg whites alongside recently purchased items. Streamline checkout with saved payment methods and preferred delivery windows to reduce friction for task‑oriented early‑morning shoppers. 
- **Friday Transition:** Beginning Thursday evening, shift the app homepage into “Weekend Mode” by highlighting grilling collections, meal‑prep inspiration, and personalized Friday checklists. This can support larger Friday baskets and aligns the experience with customers’ weekend preparation behavior.

**Tailor Shopping Experiences by Customer Segment**<br>
Prioritize strategies based on each segment’s shopping behavior and needs. 

- **Core Shoppers:** As the largest segment, these customers may benefit most from **time-saving shortcuts** like pre-populated "Weekly Essentials" lists and personalized nudges aligned with their peak daytime shopping hours. Highlighting frequent or recently purchased items immediately upon login minimizes search effort and reduces **decision fatigue** which can streamline checkouts by helping them complete baskets faster and reinforce their established routines.

- **High Spenders:** The primary goal for this segment should be to convert their already above average behavior into higher levels of activity. Since these customers are already spending more, traditional discounts may be less appealing and strategies should instead **leverage loss aversion, time-framed urgency, and status quo bias**:
  - **Frame Rewards as Losses (Prospect Theory):** Instead of using a prompt like "Earn 100 points if you order this week", reframe it as "You have 100 points expiring in 48 hours". People are more likely to be motivated to avoid losing a benefit then they are to gain one.
  - **Opt-Out Priority Access (Status Quo Bias):** Auto-enroll these customers into a 30-day trial for premium perks, such as reserved weekend delivery slots. To stop receiving these benefits, they’d have to actively opt-out, which they are less likely to do (based on the status quo bias) which can help deepen their use of the platform.
  
- **Stock‑Up Shoppers:** Although a niche segment, these customers exhibit unique behavior. They build the largest baskets (over 30 items), so rather than nudging them to buy more, consider focusing on **reducing their cognitive load** through predictive household lists, adaptive subscription programs, and one-click replenishment tools. This could simplify their shopping journey and reduce friction to encourage more frequent orders between major stock‑up trips.
  
**Overall, the greatest opportunity isn't simply encouraging customers to spend more, but understanding when they shop, who they are, and their shopping mission, which can then inform how to effectively respond to and reinforce those existing behaviors over time to grow their value.**

## Limitations & Caveats 
- The data reflects active Instacart users during the 2017 period, with an analytical focus on behavioral patterns rather than long‑term customer acquisition, churn, or retention trends.
- Cost and margin data are not included, meaning spend‑based insights represent gross value rather than profitability.
- The analysis identifies behavioral correlations but does not establish causality. Experimental validation (A/B testing) would be required before real‑world implementation.

## Next Steps 
Future work could build on this framework by validating segment stability, developing predictive models, and testing how these behavioral insights translate into more personalized customer experiences. 

**Validate & Test**
- Monitor segment stability over time and track movement between behavioral profiles to ensure segments remain meaningful as customer behavior evolves.
- Use customer surveys or interviews to better understand the motivations behind observed purchasing patterns and validate behavioral assumptions. 
- A/B test segment-specific promotions, time‑based merchandising, and personalized experiences to measure their impact on basket behavior and order frequency.

**Predict & Personalize**
- Develop models to predict churn risk, reorder timing, and customer lifetime value to support proactive engagement strategies.
- Identify early behavioral signals that indicate changes in engagement, basket size, or potential movement between segments.
- Use historical purchase intervals to predict replenishment cycles and to support personalized shopping lists and timely restock reminders.

**Implement & Expand**
- Integrate segment labels into personalization systems, recommendation engines, and marketing workflows.
- Incorporate product affinity, geography, seasonality, and promotion responsiveness into customer segments to further refine targeting strategies.
- Continuously monitor and update the segmentation framework as new behavioral data becomes available to maintain relevance and accuracy. 





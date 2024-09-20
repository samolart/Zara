# Zara Sales
![Screenshot 2024-09-21 005944](https://github.com/user-attachments/assets/e498ef9e-abcd-45b2-8954-8fd94d22f478)

## Summary
- Top-Selling Products:
Zara’s best-sellers are all about jackets. Leading the charge is the PLAID OVERSHIRT with an impressive 10,910 units sold, followed by the POCKET OVERSHIRT and a range of bomber and leather jackets. Jackets clearly dominate, making them a key product for Zara’s success.

- Promotions and Sales:
Interestingly, promotions didn’t have as strong an effect as expected. Products without promotions sold more, at 240,312 units, compared to 219,261 units with promotions. While discounts are helpful, Zara’s customers are still buying in large numbers even at full price.

- Best-Selling Categories:
When it comes to product categories, jackets reign supreme. They account for a whopping 58% of all sales, far ahead of categories like T-shirts (12%), sweaters (17%), and shoes (13%). Jackets are the clear favorite among Zara’s customers.

- Seasonal Sales:
Zara’s seasonal collections are a big draw, contributing 50.7% of the total sales volume. Customers seem to love keeping up with the latest seasonal trends, making these collections a major part of Zara’s sales strategy.

- Product Placement and Sales:
Where products are placed in the store also plays a crucial role. Aisles lead with 177,396 units sold, followed by end-cap displays and the front of the store. Zara’s store layout clearly helps boost sales, ensuring products are seen in high-traffic areas.


## Recommendations
- Focus on Jackets: Since jackets are top sellers, Zara should continue to prioritize this category by expanding its range and keeping inventory well-stocked.
- Use Promotions Strategically: While promotions help, Zara’s products sell well without discounts. Focus promotions on less popular items rather than across the board.
- Boost Seasonal Collections: With over 50% of sales coming from seasonal items, Zara should continue releasing trendy collections tied to seasons, as they attract a lot of customers.
- Optimize Store Layouts: Since aisles drive the most sales, place high-demand products in key aisle areas and use end-cap displays to promote new or popular items.

## Table of Contents
- [Objective](#objective)
- [Data source](#data-source)
- [Tools](#tools)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Findings](#findings)
- [Recommendations To Zara](#recommendations-to-zara)

### Objective 
--- 
To analyze Zara's product sales data to uncover insights into sales performance, product category trends, the impact of promotions, and overall inventory management for optimizing Zara's marketing and sales strategies.

### Data source
Zara sales [download here](https://www.kaggle.com/datasets/xontoloyo/data-penjualan-zara)

### Tools
- Excel - Data Cleaning
- Postgresql - Data analysis
- Tableau - Creating Report

### Data Cleaning
1. Chekening for duplicates
2. Text to columns

### Exploratory Data Analysis
1. What are the top-selling products?
2. What is the impact of promotions on sales volume?
3. Which sections contribute the most to total sales?
4. What are the seasonal sales trends?
5. *What is the sales volume distribution across different product positions?
6. Which  clothing category generate has the highest sale volume?
7. *Which clothing categories are benefiting the most from promotions?

```sql
/*What are the top-selling products?
This helps identify which products are driving the most revenue or volume.*/
SELECT 
    name,
    SUM (sales_volume) AS Total_sales
FROM
    zara
GROUP BY
    name      
ORDER BY
    Total_sales DESC     
LIMIT 15;

/*What is the impact of promotions on sales volume?
Analyzing how promotions influence product sales to optimize future promotions.*/
SELECT 
    promotion,
    SUM (sales_volume) AS Total_sales
FROM
    zara
GROUP BY
    promotion
ORDER BY
    Total_sales DESC;

/*Which sections contribute the most to total sales?
Evaluating section performance can help in inventory and space management.*/
SELECT 
    Section, 
    SUM(Sales_Volume) AS total_sales
FROM 
    zara
GROUP BY 
    Section
ORDER BY 
    total_sales DESC;

/*What are the seasonal sales trends?
This helps determine which seasons generate the highest sales for specific categories.*/
SELECT 
    Seasonal, 
    SUM(Sales_Volume) AS total_sales
FROM 
    zara
GROUP BY 
    Seasonal
ORDER BY 
    total_sales DESC;

/*What is the sales volume distribution across different product positions?
Understanding if product placement affects sales performance*/
SELECT 
    Product_Position, 
    SUM(Sales_Volume) AS total_sales
FROM zara
GROUP BY 
    Product_Position
ORDER BY 
    total_sales DESC;

-- Which  clothing category generate has the highest sale volume?
SELECT 
    Terms AS Clothing_Category, 
    SUM(Sales_Volume) AS total_sales
FROM 
    zara
GROUP BY 
    Terms
ORDER BY 
    total_sales DESC;

/*Which clothing categories are benefiting the most from promotions?
To assess how effective promotions are within specific clothing categories*/
SELECT 
    terms AS Clothing_Category, 
    Promotion, 
    SUM(Sales_Volume) AS total_sales
FROM 
    zara
WHERE
    promotion = 'Yes'
GROUP BY 
    Clothing_Category,
     Promotion
ORDER BY 
    total_sales DESC;
```

### Findings
#### Top-Selling Products: Jackets Take the Lead
When we look at Zara’s top-selling products, one thing is clear: jackets are the standout performers. The PLAID OVERSHIRT alone sold 10,910 units, making it the best-selling item. Following closely are the POCKET OVERSHIRT and the FAUX LEATHER BOMBER JACKET, with 7,386 and 7,197 units sold, respectively. Other variations of bomber jackets, including the CONTRASTING PATCHES BOMBER JACKET and the FAUX LEATHER JACKET, also rank high.

These numbers indicate that jackets resonate strongly with Zara’s customer base. Whether it’s due to their style, practicality, or a seasonal trend, the emphasis on jackets positions them as a key part of Zara’s product strategy.

#### Impact of Promotions: Subtle Effect on Sales
Surprisingly, promotions don’t seem to have the overwhelming impact one might expect. Zara sold 240,312 units of products without any promotions, compared to 219,261 units of promoted items.

This suggests that while promotions certainly play a role in driving sales, Zara’s products are compelling enough to attract buyers even at full price. This is an important insight for Zara’s marketing strategy—promotions might not always be necessary to move inventory, especially for high-demand items like jackets.

#### Best-Selling Categories: Jackets Dominate the Market
Diving deeper into product categories, jackets account for a remarkable 58% of total sales. No other category comes close: T-shirts make up only 12%, sweaters around 17%, and shoes just under 13%.

This further solidifies jackets as Zara’s most lucrative category, far surpassing other segments. It’s likely that jackets provide a balance of high style and versatility, appealing to a broad audience. Zara can use this data to continue focusing on innovative jacket designs, knowing this category is a consistent performer.

#### Seasonal Collections: A Major Driver of Sales
Seasonal collections are another key driver of Zara’s overall sales. A little over 50% of total sales comes from seasonal items—those products that are tied to specific fashion seasons or trends. This shows that Zara’s customers are highly responsive to new, trend-driven collections that align with the current season.

By consistently launching fresh seasonal collections, Zara ensures it stays relevant and desirable to its fashion-forward customers. These collections not only boost sales during their release but also reinforce the brand’s image as a leader in fast fashion.

#### Product Placement: Aisles Are King
Lastly, how products are positioned in Zara’s stores has a noticeable effect on sales. Products placed in the aisles accounted for 177,396 units sold, the highest of any location within the store. Meanwhile, end-cap displays (those at the end of aisles) moved 152,930 units, and products at the front of the store sold 129,247 units.

This highlights the importance of aisles and high-traffic areas in generating sales. Zara’s strategic placement of key items in these areas helps drive impulse purchases and ensures that best-selling products are easily accessible to shoppers.

### Recommendations to Zara
#### 1. Focus on Expanding and Promoting Jackets
Since jackets account for 58% of all sales, it’s clear that they are Zara’s most popular product category. To capitalize on this:

Expand the jacket collection: Offer more variations in styles, fabrics, and price ranges. Consider introducing more seasonal jackets (e.g., lightweight options for spring/summer and heavy ones for winter) to meet diverse customer needs.
Promote jackets more prominently: Highlight top-selling jackets in online ads, social media campaigns, and in-store displays. This will keep them top of mind for customers, encouraging repeat purchases.
Ensure stock availability: Since jackets are so popular, Zara should ensure that inventory levels are kept high to avoid stockouts, especially for the best-sellers like the Plaid Overshirt and Leather Bomber Jackets.

#### 2. Be Selective with Promotions
The data shows that products without promotions sold slightly more than those with promotions. This means Zara doesn’t need to rely heavily on discounts to drive sales. Here’s how to use promotions effectively:

Target slow-moving products: Instead of broad, store-wide promotions, offer discounts on categories that need a sales boost, like T-shirts and shoes, which have lower sales volumes compared to jackets.
Time promotions for off-peak seasons: Use promotions to clear out older stock during off-peak seasons or when transitioning between collections (e.g., from winter to spring).
Highlight value rather than discounts: Promote the quality, style, and uniqueness of products more than the price cuts, especially for high-demand categories like jackets and seasonal items.

#### 3. Leverage Seasonal Collections for Continued Success
With 50% of sales coming from seasonal collections, Zara’s fast-fashion strategy of regularly releasing new items tied to seasons or trends is clearly effective. To maintain this momentum:

Continue frequent seasonal drops: Keep refreshing the inventory with new collections each season to drive repeat visits from customers who want the latest trends. Make sure to promote these collections heavily, as they are a major draw for shoppers.
Analyze the timing of seasonal product launches: Track which seasonal launches perform best (e.g., summer vs. winter) and use that data to adjust the timing of new releases. This will help maximize sales during peak times.
Collaborate with influencers and designers: Partnering with fashion influencers or designers for seasonal collections can create hype and attract more attention, especially if they align with trending styles or themes.

#### 4. Optimize Product Placement in Stores
Store layout has a clear impact on sales, with products in aisles selling more than those in end-caps or at the front of the store. To make the most of this insight:

Prioritize best-sellers in high-traffic areas: Place top-selling items like jackets in the most visible and high-traffic areas, such as aisles, where customers are most likely to browse.
Use end-caps for seasonal or promotional items: End-cap displays are ideal for promoting seasonal items or products that are currently on promotion. These locations catch customers’ attention as they walk down the aisles.
Rotate product placement: Regularly change up the positioning of products to keep the store feeling fresh and encourage customers to explore different areas.

#### 5. Enhance Digital and In-Store Marketing
With jackets and seasonal collections performing exceptionally well, Zara can tailor its marketing strategies to reinforce these strengths:

Online marketing for key products: Use targeted ads and social media posts to highlight top-selling jackets and new seasonal collections. This can help drive both in-store and online traffic.
In-store displays for trending items: Feature trending items at the front of the store and in window displays to draw in customers. Seasonal products should also be prominently featured during their peak sales periods.
Use customer data for personalized marketing: Leverage customer purchase history to recommend similar products, such as offering customers who bought jackets recommendations for new outerwear or related accessories.


   

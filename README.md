# jumia-product-performance-dashboard
## Overview
This project analyzes Jumia product data to understand how price, discounts and feedback relate to product engagement. The dashboard explores whether large discounts are associated with more reviews, whether highly rated products attract stronger engagement, which products are performing best or need pricing/marketing attention.
## Dataset
Source: Excel_jumia_dataset.csv  
Fields: Product, Current Price(Ksh), Old Price, Discount(%), Review(count), Rating(count of 5)
### Tools Used
Microsoft Excel(PivotTables, PivotCharts, slicers, Excel formulas, ScatterPlots)  
Power Query(used for data cleaning, price range handling, and duplicate removal)
## Data Cleaning
The raw dataset was preserved without modification in the Raw_Data Worksheet and a separate cleaning process was used to create the Cleaned_Data worksheet.
### Data Quality Issues identified during Data Audit
- Misspelled column header (Ratingd)
- Negative review counts
- Price values in text format
- Duplicate Rows
- Percentage symbols in discount values
- Price range values
- Currency symbols and commas in price values
- Blank ratings/reviews
- “out of 5” in ratings
## Cleaning Decisions
| Issue |	Decision |	Reason |
|---|---|---|
| Ratingd header |	Renamed to Rating |	Standardized naming |
| Negative review counts	| Converted to absolute values	| Reviews count cannot be negative |
| Duplicate Rows	| Removed	| Prevent double counting |
| Percentage symbols 	| Removed %	| Enable numerical analysis |
| Price range values	| Used midpoint	| Enable analysis using a representative numeric value |
| Currency symbols 	| Removed KSh and Commas	| Convert prices to numeric format |
| Blank ratings/reviews	| Retained as blank	| Missing data is not equivalent to 0 |
| “out of 5” in ratings	| Removed “out of 5”	| Convert ratings to decimal |

All cleaning decisions were documented in the Data_Dictionary worksheet.
## Key Formulas
Discount Amount: =[@[Old Price]]-[@[Current Price]]  
Rating Category: Poor <3, Average 3–4.5, Excellent >4.5  
Discount Category: Low <20%, Medium 20–40%, High >40%  
Price category: based on quartiles (Q1 / Q3) of Current Price  
Engagement threshold: 75th percentile of Review count  
Correlations calculated with CORREL()
## Analysis
The analysis included descriptive statistics, product rankings, category comparisons and correlation analysis
### Key Performance Indicators
The following KPIs were calculated;
- Total products
- Average current price
- Average old price
- Average discount
- Average rating
- Total Reviews
- Maximum Price
- Minimum Price
- Most Expensive Product
- Least Expensive Product
### Relationship Analysis
Three relationships were investigated using scatter plots and Pearson’s Correlation
| Relationship	| r	| R² |
|---|---|---|
| Discount vs Reviews	| -0.14	| 0.02 |
| Rating vs Reviews	| 0.06	| 0.00 |
| Price vs Rating	 | 0.11	| 0.01 | 

All 3 correlations are weak indicating price, discount and rating do not strongly predict customer engagement.
### Product Performance analysis
The following ranked analyses were created:
- Top 5 products by rating
- Bottom 5 products by rating
- Top 10 products by discount
- Top 10 products by reviews
- Top 10 products by rating
- Products with high discounts but low ratings
- Products with high discounts but low engagement
- Products with many reviews but average ratings
## Dashboard Features
- KPI cards: total products, average price, average discount, average rating, total reviews
- Top 10 tables: by rating, by reviews, by discount
- Scatter charts: Discount vs. Reviews, Rating vs. Reviews, Price vs. Rating
- Rating mix and Discount mix charts
- Slicers: Rating Category, Discount Category, Price Category
- Flags: High Discount + Low Rating, High Discount + Low Engagement, High Engagement + Average Rating, High Engagement + Excellent Rating
## Key Findings & Recommendations
1.	Discount vs. reviews: No meaningful relationship.  
2.	Rating vs. reviews: No meaningful relationship.  
3.	Price vs. rating: Very weak relationship 
## Recommendations
Based on the analysis, potential recommendations include:
- Test discount strategies rather than assuming larger discounts automatically generate engagement.
- Investigate highly discounted products with low ratings to identify potential product quality issues.
- Review products with high engagement but average ratings for customer experience improvement opportunities.
- Promote products with strong engagement and excellent ratings as they demonstrate positive customer response.
- Improve listing visibility and content for products with weak engagement despite competitive pricing.
## Limitations
- Review count is used as an engagement proxy, not a sales or revenue measure.
- Correlation does not imply causation. Unmeasured factors (listing duration, category, visibility) may explain the weak relationships observed.
- Rating and review fields had missing values, which were excluded rather than imputed.
- Customer reviews may be influenced by factors unrelated to price or discounts.
Therefore, findings should be interpreted as exploratory insights rather than causal conclusions.
## Workbook Structure
The Excel workbook contains the following worksheets:
| Worksheet	| Purpose |
|---|---|
| Raw_Data	| Original untouched dataset | 
| Cleaned_Data	| Cleaned and enriched data |
| Analysis	| KPIs, statistics, and correlations |
| Pivot_Tables	| Supporting PivotTables and PivotCharts |
| Dashboard	| Interactive visual dashboard |
| Data_Dictionary	| Field definitions and cleaning documentation |

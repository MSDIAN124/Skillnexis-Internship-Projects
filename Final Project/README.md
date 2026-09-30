# Financial Sales and Profitability Analysis Using Python

## Project Overview

This project analyzes a financial sales dataset using **Python and Pandas** to identify key revenue drivers, profitable customer segments, country-wise performance, product performance, and the impact of discounting on profitability.

The objective was to transform raw business data into actionable insights that can support pricing, discounting, product, and customer-segment decisions.

## Business Objectives

- Which customer segment generates the highest sales and profit?
- Which country contributes the most sales, profit, and profit margin?
- Which products are the strongest and weakest performers?
- How do discount bands affect sales, profit, and profit margins?
- Which segment-product combinations are highly profitable or loss-making?
- What actions can improve overall profitability?

## Dataset

The dataset contains **700 records** and **12 columns** related to sales and profitability.

| Column | Description |
|---|---|
| `Segment` | Customer segment, such as Government, Enterprise, Small Business, Midmarket, and Channel Partners |
| `Country` | Country where the sale occurred |
| `Product` | Product name |
| `Discount Band` | Discount category, such as No Discount, Low, Medium, or High |
| `Units Sold` | Quantity of units sold |
| `Manufacturing Price` | Manufacturing price per unit |
| `Sale Price` | Selling price per unit |
| `Gross Sales` | Sales value before discounts |
| `Discounts` | Discount amount provided |
| `Sales` | Net sales after discounts |
| `COGS` | Cost of goods sold |
| `Profit` | Profit earned after deducting COGS from net sales |

## Tools and Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook
- CSV and Excel

## Data Preparation

- Loaded the CSV file into a Pandas DataFrame.
- Inspected dataset shape, column names, data types, missing values, and duplicates.
- Standardized column names by removing spaces and converting them to lowercase snake_case.
- Identified blank values in `discount_band`.
- Verified that blank discount-band records had `0` in the numeric `discounts` column.
- Replaced blank discount-band labels with `No Discount`.
- Validated the sales and profit calculations.

### Financial Logic

```text
Net Sales = Gross Sales - Discounts
Profit = Net Sales - COGS
```

## Calculated Metrics

| Metric | Formula |
|---|---|
| Profit Margin % | `(Profit / Sales) x 100` |
| Discount Rate % | `(Discounts / Gross Sales) x 100` |
| Revenue per Unit | `Sales / Units Sold` |
| Total Sales | Sum of net sales |
| Total Profit | Sum of profit |
| Total Discounts | Sum of discount values |
| Total Units Sold | Sum of units sold |

## Analysis Performed

### Segment Analysis

- **Government** generated the highest total profit: approximately **₹11.39M**.
- **Channel Partners** was the most efficient segment, with a profit margin of **73.13%**.
- **Enterprise** was loss-making, with a negative profit margin of **-3.13%** and an overall loss of approximately **₹0.61M**.

### Country Analysis

- The **USA** generated the highest net sales: approximately **₹25.02M**.
- **France** generated the highest total profit: approximately **₹3.70M**.
- **Germany** achieved the highest profit margin: **15.66%**.
- **Mexico** generated the lowest total profit: approximately **₹2.91M**, while remaining profitable.
- The USA had the lowest country-level profit margin: **11.97%**.

### Product Analysis

- **Paseo** generated the highest sales: approximately **₹33M**.
- **Paseo** generated the highest total profit: approximately **₹4.7M**.
- **Amarilla** achieved the highest product-level profit margin: **15.86%**.
- **Carretera** generated the lowest total profit: approximately **₹1.8M**.
- **Velo** had the lowest product-level profit margin: **12.64%**.

### Discount Impact Analysis

- The **Medium** discount band generated the highest total sales: approximately **₹38.78M**.
- The **Low** discount band generated the highest total profit: approximately **₹6.10M**.
- The **No Discount** band achieved the highest profit margin: **21.86%**.
- The **High** discount band recorded the lowest profit margin: **9.07%**.
- Higher discount bands were associated with lower profitability.

### Segment-Product Analysis

- **Government-Paseo** was the top segment-product combination by total profit.
- It generated approximately **₹14.8M** in sales and **₹3.0M** in profit.
- Its profit margin was **20.54%**, the fifth-highest among segment-product combinations.
- **Enterprise-Carretera** was the least profitable combination, recording an overall loss of approximately **₹2.2M**.

### Enterprise-Carretera Deep Dive

- The combination had **15 transactions** across all countries.
- **12 of 15 transactions (80%)** were loss-making.
- Only **3 transactions** were profitable.
- The highest single transaction profit was approximately **₹5,304.38**.
- The largest single transaction loss was approximately **₹38,046.25**.
- The findings indicate that its pricing, discount, and COGS structure did not reliably cover costs.

## Key Business Insights

1. Revenue does not always equal profitability: the USA led sales, but France generated the most profit and Germany had the strongest country-level margin.
2. Government was the largest profit contributor, while Channel Partners was the most efficient segment.
3. Paseo was the primary product driver for sales and profit; Amarilla was the most margin-efficient product.
4. No Discount transactions had the strongest margin, while High discounts had the weakest, indicating that excessive discounting erodes profitability.
5. Enterprise-Carretera is a critical risk area because 80% of its transactions were loss-making.

## Recommendations

- Protect and expand the **Government-Paseo** combination because it is the highest profit-generating pairing.
- Review **Enterprise-Carretera** pricing, COGS, customer contracts, and discounting immediately.
- Avoid broad High discount strategies; use targeted Low-to-Medium discounts where needed.
- Study Channel Partners and Amarilla to identify pricing, product-mix, or cost practices that may improve lower-margin areas.
- Investigate USA product mix, COGS, and discounting because high sales were not converting to the strongest margin.
- Review Mexico's country-level product mix and cost structure to improve its lower profit contribution.

## Visualizations

The notebook includes the following visualizations:

- Total profit by customer segment
- Total net sales by country
- Total profit by country
- Total profit by product
- Profit margin by discount band

## Project Structure

```text
Final Project/
|
|-- Financial_Sample_Data-Sheet1.csv
|-- Financial_Sales_Analysis.ipynb
|-- financial_sales_analysis_output.xlsx
|-- README.md
|-- Summary.md
`-- Charts/
```

## How to Run

1. Clone or download this repository.
2. Place `Financial_Sample_Data-Sheet1.csv` in the project folder.
3. Open `Financial_Sales_Analysis.ipynb` in Jupyter Notebook or VS Code.
4. Install dependencies:

```bash
pip install pandas numpy matplotlib seaborn openpyxl
```

5. Run notebook cells sequentially.
6. Review the analysis tables, visualizations, and exported Excel output.

## Author

**Mukesh Samarit**  
Aspiring Data Analyst | Excel | Power BI | SQL | Python | Pandas

*Github:- www.github.com/MSDIAN124
*Linkedin- www.linkedin.com/in/mukesh-samarit


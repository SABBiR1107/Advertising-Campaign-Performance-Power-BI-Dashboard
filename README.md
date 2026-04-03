# Tech Advertising Campaign Performance Dashboard (Power BI)

## Project Overview
This project analyzes a digital advertising campaign dataset and turns it into an interactive **Power BI dashboard** for business and marketing decision-making.

The dashboard focuses on:
- campaign performance
- platform efficiency
- audience behavior
- creative effectiveness
- profitability and return

Using this dashboard, a business user can quickly identify which campaigns, platforms, audience groups, and ad strategies are generating the best results.

---

## Dataset Summary
The dataset contains **10,000 advertising campaign records** with campaign setup, targeting, engagement, and financial performance data.

### Main fields included
- Campaign details: `campaign_id`, `campaign_objective`, `platform`, `ad_placement`
- Device and technical fields: `device_type`, `operating_system`
- Creative fields: `creative_format`, `creative_size`, `ad_copy_length`, `creative_emotion`, `has_call_to_action`
- Audience fields: `target_audience_age`, `target_audience_gender`, `audience_interest_category`, `income_bracket`, `purchase_intent_score`
- Campaign timing fields: `start_date`, `quarter`, `day_of_week`, `hour_of_day`, `campaign_day`
- Performance fields: `impressions`, `clicks`, `conversions`, `ad_spend`, `revenue`, `profit`
- KPI fields: `CTR`, `CPC`, `conversion_rate`, `CPA`, `ROAS`

---

## Project Objective
The main objective of this project is to build a professional **Power BI dashboard** that answers important business questions such as:

- Which platform performs best?
- Which campaign objective brings the highest profit?
- Which audience segments convert better?
- Which creative type drives stronger engagement?
- Does retargeting improve campaign performance?
- What day and hour perform best?
- Which campaign combinations produce the highest ROAS?

---

## Tools Used
- **Power BI Desktop**
- **Power Query**
- **DAX**
- **CSV Dataset**

---

## Data Preparation
Before building the dashboard, the dataset should be cleaned and prepared in **Power Query**.

### Data preparation steps
1. Import the CSV dataset into Power BI.
2. Check column data types.
3. Convert `start_date` into **Date** format.
4. Ensure boolean columns are correctly recognized:
   - `has_call_to_action`
   - `retargeting_flag`
5. Check numeric columns for correct decimal/whole number formats.
6. Create additional columns for reporting and filtering.

---

## Calculated Columns
The following calculated columns are useful for analysis:

### Month Name
```DAX
Month Name = FORMAT('tech_advertising_campaigns_dataset'[start_date], "MMMM")
```

### Year
```DAX
Year = YEAR('tech_advertising_campaigns_dataset'[start_date])
```

### CTA Label
```DAX
CTA Label = IF('tech_advertising_campaigns_dataset'[has_call_to_action] = TRUE(), "Yes", "No")
```

### Retargeting Label
```DAX
Retargeting Label = IF('tech_advertising_campaigns_dataset'[retargeting_flag] = TRUE(), "Yes", "No")
```

### Profit Status
```DAX
Profit Status = IF('tech_advertising_campaigns_dataset'[profit] > 0, "Profitable", "Loss")
```

---

## DAX Measures

### Basic Measures

#### Total Campaigns
```DAX
Total Campaigns = DISTINCTCOUNT('tech_advertising_campaigns_dataset'[campaign_id])
```

#### Total Impressions
```DAX
Total Impressions = SUM('tech_advertising_campaigns_dataset'[impressions])
```

#### Total Clicks
```DAX
Total Clicks = SUM('tech_advertising_campaigns_dataset'[clicks])
```

#### Total Conversions
```DAX
Total Conversions = SUM('tech_advertising_campaigns_dataset'[conversions])
```

#### Total Ad Spend
```DAX
Total Ad Spend = SUM('tech_advertising_campaigns_dataset'[ad_spend])
```

#### Total Revenue
```DAX
Total Revenue = SUM('tech_advertising_campaigns_dataset'[revenue])
```

#### Total Profit
```DAX
Total Profit = SUM('tech_advertising_campaigns_dataset'[profit])
```

---

### KPI Measures

#### Average CTR
```DAX
Average CTR = AVERAGE('tech_advertising_campaigns_dataset'[CTR])
```

#### Average CPC
```DAX
Average CPC = AVERAGE('tech_advertising_campaigns_dataset'[CPC])
```

#### Average Conversion Rate
```DAX
Average Conversion Rate = AVERAGE('tech_advertising_campaigns_dataset'[conversion_rate])
```

#### Average CPA
```DAX
Average CPA = AVERAGE('tech_advertising_campaigns_dataset'[CPA])
```

#### Average ROAS
```DAX
Average ROAS = AVERAGE('tech_advertising_campaigns_dataset'[ROAS])
```

---

### Better Overall Ratio Measures

#### Overall CTR
```DAX
Overall CTR = DIVIDE([Total Clicks], [Total Impressions], 0)
```

#### Overall Conversion Rate
```DAX
Overall Conversion Rate = DIVIDE([Total Conversions], [Total Clicks], 0)
```

#### Overall CPC
```DAX
Overall CPC = DIVIDE([Total Ad Spend], [Total Clicks], 0)
```

#### Overall CPA
```DAX
Overall CPA = DIVIDE([Total Ad Spend], [Total Conversions], 0)
```

#### Overall ROAS
```DAX
Overall ROAS = DIVIDE([Total Revenue], [Total Ad Spend], 0)
```

---

## Dashboard Pages

## 1. Executive Overview
This page gives a high-level business summary.

### KPI Cards
- Total Campaigns
- Total Impressions
- Total Clicks
- Total Conversions
- Total Ad Spend
- Total Revenue
- Total Profit
- Overall CTR
- Overall Conversion Rate
- Overall ROAS

### Recommended visuals
- Clustered column chart: **Profit by Platform**
- Bar chart: **Revenue by Campaign Objective**
- Donut chart: **Campaign Distribution by Profit Status**
- Line chart: **Monthly Profit Trend**

### Slicers
- Platform
- Campaign Objective
- Industry Vertical
- Budget Tier
- Month Name
- Device Type

---

## 2. Audience Performance
This page focuses on customer and targeting insights.

### Recommended visuals
- Bar chart: **Profit by Target Audience Age**
- Bar chart: **Conversion Rate by Gender**
- Bar chart: **ROAS by Audience Interest Category**
- Stacked bar chart: **Conversions by Income Bracket and Retargeting**

### Slicers
- Platform
- Campaign Objective
- Retargeting Label

---

## 3. Creative & Campaign Optimization
This page helps understand which creative strategy works best.

### Recommended visuals
- Bar chart: **CTR by Creative Format**
- Bar chart: **Conversion Rate by Creative Emotion**
- Bar chart: **Profit by Ad Placement**
- Column chart: **ROAS by CTA Label**
- Scatter chart:
  - X-axis: `quality_score`
  - Y-axis: `CTR`
  - Size: `revenue`
  - Legend: `platform`

---

## 4. Time & Efficiency Analysis
This page shows performance trends over time.

### Recommended visuals
- Line chart: **CTR by Hour of Day**
- Column chart: **Profit by Day of Week**
- Line chart: **Revenue by Month**
- Matrix:
  - Rows: Platform
  - Columns: Campaign Objective
  - Values: Total Profit, Overall ROAS, Overall CTR

---

## Dashboard Design Tips
- Use **KPI cards** at the top for summary
- Use **slicers** for interactivity
- Apply **conditional formatting** in tables and matrices
- Use **tooltips** to show extra metrics
- Keep colors and layout consistent
- Highlight profitability and ROAS clearly for decision-making

---

## Key Business Insights This Dashboard Can Provide
- Best-performing platform by profit and ROAS
- Most effective campaign objective
- Highest-value audience segment
- Best creative format and emotional style
- Impact of retargeting campaigns
- Best-performing days and hours
- Platform-objective combinations with strongest return

---

## Business Value
This dashboard helps:
- optimize ad budget allocation
- improve campaign targeting
- choose stronger creative strategies
- reduce low-performing ad spend
- track profitability in a clear and interactive way

---

## Portfolio Description
**Tech Advertising Campaign Performance Dashboard**  
Built an interactive Power BI dashboard using 10,000 advertising campaign records to analyze campaign performance, audience behavior, creative effectiveness, and profitability. Designed KPI-driven visuals and DAX measures to track impressions, clicks, conversions, spend, revenue, profit, CTR, CPA, and ROAS for better marketing decision-making.

---

## Suggested File Structure
```bash
Tech-Advertising-Campaign-PowerBI/
│
├── data/
│   └── tech_advertising_campaigns_dataset.csv
│
├── dashboard/
│   └── Tech_Advertising_Campaign_Dashboard.pbix
│
└── README.md
```

---

## Conclusion
This Power BI project is a complete business intelligence solution for advertising campaign analysis. It can be used as a portfolio project to demonstrate skills in:
- data cleaning
- data modeling
- DAX
- dashboard design
- business insight generation

It is a strong project for roles related to:
- Data Analyst
- BI Analyst
- Marketing Analyst
- Business Analyst

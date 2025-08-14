# Power BI Basics for Beginners - Higher Ed to Utility Transition

## What is Power BI?
Power BI is Microsoft's business intelligence tool that helps you:
- Connect to data sources (Excel, databases, cloud services)
- Create interactive dashboards and reports
- Share insights with teams and stakeholders
- Make data-driven decisions

**Think of it like:** A more powerful, interactive version of Excel charts that can connect to multiple data sources automatically.

## DAX Explained Simply

### What is DAX?
**DAX = Data Analysis Expressions**
- **D**ata **A**nalysis e**X**pressions
- It's the "formula language" for Power BI (like Excel formulas, but more powerful)
- Used to create calculations, metrics, and custom measures
- Helps you analyze data beyond basic sums and averages
- **Think of it like:** Advanced Excel formulas that work across multiple data tables

### Your Higher Ed Experience Connection:
- **Excel formulas** → DAX formulas
- **Student enrollment reports** → Utility customer analytics  
- **Budget tracking** → Energy usage tracking
- **Compliance metrics** → Regulatory reporting

## Essential DAX Functions for Utilities

### 1. SUM and AVERAGE (Basic Aggregations)
```dax
// Total Energy Generated
Total_Generation = SUM(Generation[MW_Output])

// Average Customer Usage
Avg_Usage = AVERAGE(CustomerUsage[kWh_Monthly])
```

**Real-world use:** "How much total energy did we generate this month?"

### 2. CALCULATE (Filtered Calculations)
```dax
// Energy generated only from renewable sources
Renewable_Generation = 
CALCULATE(
    SUM(Generation[MW_Output]),
    Generation[Source] = "Solar" || Generation[Source] = "Wind"
)
```

**Real-world use:** "How much clean energy did we generate?"

### 3. DIVIDE (Safe Division with Error Handling)
```dax
// Renewable percentage of total generation
Renewable_Percentage = 
DIVIDE(
    [Renewable_Generation],
    [Total_Generation],
    0
) * 100
```

**Real-world use:** "What percentage of our energy comes from renewables?"

### 4. SUMX (Row-by-Row Calculations)
```dax
// Calculate outage impact (customers affected × duration)
Outage_Impact = 
SUMX(
    Outages,
    Outages[Customers_Affected] * Outages[Duration_Hours]
)
```

**Real-world use:** Used for SAIDI calculations (reliability metrics)

## Utility Metrics You'll Calculate

### SAIDI (System Average Interruption Duration Index)
**What it means:** Average time customers are without power per year
**Why it matters:** Regulatory requirement, measures grid reliability
**Your calculation:** Total customer-hours of interruption ÷ Total customers

### CAIFI (Customer Average Interruption Frequency Index)  
**What it means:** Average interruptions per affected customer
**Why it matters:** Shows how often customers experience outages
**Your calculation:** Total customer interruptions ÷ Total affected customers

### Peak Demand Utilization
**What it means:** How much of available capacity is being used
**Why it matters:** Helps plan infrastructure investments
**Your calculation:** Current demand ÷ Available capacity × 100

## 5-Day Interview Prep Plan (Specific Links)

### Day 1: Power BI Fundamentals (2-3 hours)
**Priority:** Understanding what Power BI is and basic navigation
- **DataCamp:** https://learn.datacamp.com/courses/introduction-to-power-bi
- **YouTube:** "Power BI Tutorial for Beginners" - https://youtube.com/watch?v=AGrl-H87pRU (ExcelIsFun)
- **Microsoft Learn:** https://learn.microsoft.com/en-us/training/modules/get-started-with-power-bi/

### Day 2: DAX Basics (2-3 hours)  
**Priority:** Understanding basic calculations
- **YouTube:** "DAX 101 - Introduction to DAX" - https://youtube.com/watch?v=klQAZLr5vxA (SQLBI)
- **DataCamp:** https://learn.datacamp.com/courses/introduction-to-dax-in-power-bi
- **Practice:** Create basic SUM, AVERAGE measures

### Day 3: Utility Industry Context (2 hours)
**Priority:** Learning utility terminology for interview
- **YouTube:** "How the Power Grid Works" - https://youtube.com/watch?v=v1BMWczn7JM
- **Read:** SAIDI/CAIFI definitions - https://en.wikipedia.org/wiki/SAIDI
- **Practice:** Explaining utility metrics in simple terms

### Day 4: Interview Scenarios (2 hours)
**Priority:** Connecting your experience to Power BI
- **YouTube:** "Power BI Dashboard Best Practices" - https://youtube.com/watch?v=8EsYzJyNgFo
- **Practice:** Talking through your dashboard design
- **Review:** Your strategic analysis and talking points

### Day 5: Final Review (1 hour)
**Priority:** Confidence building and key message practice
- **Review:** All learning materials created
- **Practice:** 2-minute Power BI explanation
- **Prepare:** Questions about specific DAX functions

## Quick Reference for Interview

### When asked about Power BI:
"Power BI is Microsoft's business intelligence platform. In my higher education experience, I used similar tools like Tableau for student analytics. Power BI would help TEP create real-time dashboards for grid operations, customer usage patterns, and regulatory compliance reporting."

### When asked about DAX:
"DAX is Power BI's calculation language. While I'm newer to DAX specifically, my experience with Excel formulas and data analysis provides a strong foundation. I've been studying utility-specific calculations like SAIDI and renewable energy percentages that would be essential for TEP's operations."

### When asked about specific metrics:
"SAIDI measures how long customers are without power annually - it's a key regulatory metric. CAIFI shows interruption frequency. These are calculated using DAX formulas that aggregate outage data across TEP's 458,000+ customers."

## Additional Resources with Direct Links

### Power BI Learning
- **Microsoft Power BI YouTube Channel:** https://youtube.com/c/mspowerbi
- **Guy in a Cube (Power BI Experts):** https://youtube.com/c/GuyinaCube
- **Power BI Community:** https://community.powerbi.com/
- **SQLBI (Advanced DAX):** https://sqlbi.com/learn/

### Utility Industry Context
- **EIA Energy Explained:** https://www.eia.gov/energyexplained/
- **Utility Dive:** https://utilitydive.com/
- **Smart Electric Power Alliance:** https://sepapower.org/
- **North American Electric Reliability Corporation:** https://nerc.com/

### Interview-Specific Prep
- **Power BI Interview Questions:** https://powerbi.microsoft.com/en-us/blog/power-bi-interview-questions/
- **DAX Quick Reference:** https://docs.microsoft.com/en-us/dax/dax-function-reference

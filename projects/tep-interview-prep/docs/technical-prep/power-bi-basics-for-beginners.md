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
- It's the "formula language" for Power BI (like Excel formulas, but more powerful)
- Used to create calculations, metrics, and custom measures
- Helps you analyze data beyond basic sums and averages

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

## Learning Path Recommendation

### Week 1: Power BI Basics
1. **DataCamp: Introduction to Power BI** (4 hours)
2. **YouTube: "Power BI in 60 Minutes"** (1 hour)
3. **Practice: Connect to Excel file, create basic chart** (1 hour)

### Week 2: DAX Fundamentals  
1. **DataCamp: Introduction to DAX** (4 hours)
2. **Practice: Create basic SUM, AVERAGE measures** (1 hour)
3. **YouTube: "DAX for Beginners"** (2 hours)

### Week 3: Utility Applications
1. **Create sample utility data in Excel** (2 hours)
2. **Build basic utility dashboard** (3 hours)
3. **Practice explaining metrics** (1 hour)

## Quick Reference for Interview

### When asked about Power BI:
"Power BI is Microsoft's business intelligence platform. In my higher education experience, I used similar tools like Tableau for student analytics. Power BI would help TEP create real-time dashboards for grid operations, customer usage patterns, and regulatory compliance reporting."

### When asked about DAX:
"DAX is Power BI's calculation language. While I'm newer to DAX specifically, my experience with Excel formulas and data analysis provides a strong foundation. I've been studying utility-specific calculations like SAIDI and renewable energy percentages that would be essential for TEP's operations."

### When asked about specific metrics:
"SAIDI measures how long customers are without power annually - it's a key regulatory metric. CAIFI shows interruption frequency. These are calculated using DAX formulas that aggregate outage data across TEP's 458,000+ customers."

## Next Steps for You
1. **Complete DataCamp Power BI Introduction** (priority 1)
2. **Review this document daily** to build vocabulary
3. **Practice explaining concepts** out loud
4. **Connect everything back to your higher ed analytics experience**

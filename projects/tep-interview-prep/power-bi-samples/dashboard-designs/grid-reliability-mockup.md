# Power BI Grid Reliability Dashboard - TEP Operations Center

## Dashboard Overview

**Purpose:** Real-time monitoring of electric grid performance, outage management, and reliability metrics for TEP's operations teams and regulatory reporting.

**Primary Users:** System operators, reliability engineers, operations managers, regulatory compliance teams

**Update Frequency:** Real-time data (30-second refresh) with historical analysis capabilities

## Key Performance Indicators

### Critical Reliability Metrics

#### SAIDI (System Average Interruption Duration Index)
- **Target:** <62 minutes annually (Arizona regulatory standard)
- **Current Status:** Real-time calculation with YTD trending
- **Alert Thresholds:** Yellow >45 minutes, Red >55 minutes

#### CAIFI (Customer Average Interruption Frequency Index)  
- **Target:** <1.2 interruptions annually per affected customer
- **Current Status:** Rolling 12-month calculation
- **Alert Thresholds:** Yellow >1.0, Red >1.15

#### SAIFI (System Average Interruption Frequency Index)
- **Target:** <1.1 interruptions annually per customer
- **Calculation:** Total customer interruptions ÷ Total customers served
- **Trending:** Monthly and quarterly analysis with weather correlation

### Operational Performance Metrics
- **Peak Demand vs. Available Capacity** - Real-time utilization percentage
- **Equipment Health Scores** - Transformer, breaker, and line status
- **Generation Mix** - Coal, natural gas, solar, wind, storage percentages
- **Voltage Stability** - System voltage across transmission and distribution networks

## Dashboard Layout Design

### Header Section

### Main Dashboard Layout

#### Left Panel - Real-Time System Status (30% width)

**Interactive System Map**
- Color-coded substations (Green: Normal, Yellow: Alert, Red: Emergency)
- Active outage locations with customer impact radius
- Field crew positions and ETAs
- Weather overlay with impact zones

**Current Alerts Panel**

**System Health Gauges**
- Frequency stability (59.95-60.05 Hz)
- System voltage (±5% nominal)
- Reserve margin percentage

#### Center Panel - Performance Metrics (40% width)

**Key Reliability Metrics**
- SAIDI gauge with YTD progress vs. annual target
- CAIFI trending chart (monthly rolling average)
- Peak demand utilization percentage
- Equipment availability scores

**Generation Dashboard**
- Current generation mix (real-time)
- Renewable energy output vs. forecast
- Storage system charge/discharge status
- Carbon emissions tracking

#### Right Panel - Operations Support (30% width)

**Active Outages Management**
- Outage list with priority ranking
- Estimated restoration times
- Crew assignments and status
- Customer communication status

**Weather and Forecasting**
- Current weather conditions
- Severe weather alerts
- Load forecast accuracy
- Demand response activation status

## Sample DAX Calculations

### Grid Reliability Metrics
```dax
// SAIDI (System Average Interruption Duration Index)
SAIDI_Current = 
DIVIDE(
    SUMX(
        Outages,
        Outages[Duration_Minutes] * Outages[Customers_Affected]
    ),
    SUM(CustomerBase[Total_Customers_Served])
)

// Peak Demand Utilization
Peak_Utilization = 
DIVIDE(
    MAX(Demand[Current_MW]),
    MAX(Capacity[Available_MW])
) * 100

// Renewable Energy Percentage
Renewable_Mix = 
DIVIDE(
    SUM(Generation[Renewable_MW]),
    SUM(Generation[Total_MW]),
    0
) * 100

// Equipment Health Score
Equipment_Health = 
AVERAGE(
    SWITCH(
        Equipment[Condition_Status],
        "Excellent", 100,
        "Good", 80,
        "Fair", 60,
        "Poor", 40,
        "Critical", 20,
        0
    )
)

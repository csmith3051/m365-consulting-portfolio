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
<pre>
┌─────────────────────────────────────────────────────────────────────────────┐
│  TEP Grid Reliability Dashboard          [Real-time Status: ●NORMAL]        │
│  Last Updated: 2025-08-13 14:35:22      Active Outages: 3 | Customers: 847  │
└─────────────────────────────────────────────────────────────────────────────┘
</pre>

### Main Dashboard Layout

#### Left Panel - Real-Time System Status (30% width)

**Interactive System Map**
- Color-coded substations (Green: Normal, Yellow: Alert, Red: Emergency)
- Active outage locations with customer impact radius
- Field crew positions and ETAs
- Weather overlay with impact zones

**Current Alerts Panel**
<pre>
🔴 CRITICAL ALERTS (2)
- Transformer overload - Substation 47A
- Voltage deviation - Circuit 23B

🟡 WARNING ALERTS (5)  
- Equipment maintenance due - Line 15C
- High load forecast - District 3
</pre>

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

## User Experience Design

### Role-Based Views
- **Operators:** Focus on real-time alerts and immediate response tools
- **Engineers:** Detailed analytics and trend analysis capabilities
- **Management:** Executive summary cards and regulatory compliance metrics
- **Field Crews:** Mobile-optimized views with location-based information

### Interactive Features
- **Drill-down capabilities:** Click any metric to see detailed analysis
- **Time period selection:** Real-time, hourly, daily, monthly views
- **Alert acknowledgment:** Mark alerts as reviewed with timestamp
- **Export functionality:** PDF reports for regulatory submissions

## Mobile Responsiveness
- **Field Operations:** Simplified dashboard for mobile devices
- **Critical Alerts:** Push notifications for emergency situations
- **Offline Capability:** Cached data for areas with poor connectivity
- **Voice Integration:** Hands-free status updates for field crews

## Security and Compliance
- **Role-based access control:** Different permissions for different user types
- **Audit logging:** All user interactions tracked for compliance
- **Data encryption:** All sensitive utility data protected
- **NERC CIP compliance:** Meets critical infrastructure protection standards

## Integration Points
- **SCADA Systems:** Real-time operational data feed
- **Outage Management System:** Customer impact and restoration data
- **Weather Services:** Meteorological data for correlation analysis
- **Customer Information System:** Service territory and account data

---

*This dashboard design demonstrates understanding of utility operations, regulatory requirements, and the critical nature of grid reliability monitoring for TEP's 458,000+ customers across Southern Arizona.*


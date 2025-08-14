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

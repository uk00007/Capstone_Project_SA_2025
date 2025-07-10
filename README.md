# Capstone_Project_SA_2025

I have selected one of the parking lots as the target lot ('BHMBCCMKT01') which has implemented the model-2 pricing framework along with geographical insights based on model-3.
The other parking lots have their pricing model based on the model-1.
The pricing strategy for the target lot is influenced by its competitors, which are decided on the basis of geographical distance.


# Technology Stack
# Core Technologies
Pathway - Advanced stream processing framework enabling real-time data handling and temporal analytics

Pandas - Essential data manipulation and analysis library for preprocessing and data structure management

NumPy - Numerical computing foundation for mathematical operations and array processing

Bokeh - Interactive visualization library creating dynamic, web-based charts and dashboards

Panel - Web application framework for building responsive dashboards and user interfaces

Matplotlib - Additional plotting capabilities for data visualization and analysis

# Data Processing Infrastructure
Datetime Module - Time-based operations, parsing, and temporal data management

CSV Processing - Structured data ingestion from comma-separated value files

Stream Analytics - Real-time data processing using Pathway's temporal windowing capabilities

Haversine Distance Calculation - Geographical distance computation based on location coordinates for location-based pricing effects


# Visualization and User Interface
Bokeh Plotting - Interactive time-series charts with real-time updates

Panel Extensions - Web-based dashboard interface with responsive design

Real-time Visualization - Dynamic chart updates synchronized with data streams

Alert Visualization - Color-coded indicators for congestion and re-routing recommendations


# System Architecture Components
# 1. Data Ingestion Layer
The system begins with a robust data ingestion layer that handles multiple parking lot data sources:

Data Sources: CSV files containing parking lot data with comprehensive metrics

Schema Definition: Structured data format using Pathway's Schema class ensuring data consistency and type safety

Stream Simulation: Controlled data replay at configurable rates (100 records/second) to simulate real-time conditions


# 2. Data Processing Layer
The processing layer transforms raw data into actionable insights:

Data Transformation: Conversion of categorical string values to numerical representations for algorithmic processing

Temporal Processing: Timestamp parsing and time-based window creation for aggregation operations

Location Analytics: Haversine formula implementation for calculating distances between parking facilities

Feature Engineering: Creation of derived metrics including occupancy rates, demand indicators, and traffic conditions

# 3. Pricing Algorithm Layer
The system implements three pricing models:

Model 1: Competitor Lot Pricing

Base price of $10 with dynamic adjustments based on demand fluctuation

Formula: price = 10 + 5 × (occupancy_fluctuation / capacity)

Maximum price cap of $15 to maintain competitive positioning

Model 2: Target Lot Advanced Pricing

Multi-factor demand calculation incorporating occupancy, queue length, traffic conditions, special days, and vehicle types

Demand formula: demand = a₁×(occ/cap) + a₂×queue + a₃×traffic + a₄×special_day + a₅×vehicle_type

Coefficients: a₁=1, a₂=0.1, a₃=1, a₄=-1, a₅=0.2

Price formula: price = 10 × (1 + demand/norm_factor)

Model 3: Competitive Adjustment for price of Target Lot

Distance-based competitive pricing considering nearby lot prices

Effect coefficient calculation: 1/distance_to_competitor

Price adjustment: price = price + 0.6 × (competitor_price - price) × (effect_coeff / total_effect)

Note: The target lot price adjustment is made for each of the competitors, updating price by the above mentioned formula in every iteration.

# 4. Alert and Congestion Management System
The alert system monitors occupancy levels and provides re-routing recommendations:

Congestion Monitoring: Real-time tracking of occupancy rates with 70% threshold alerts

Re-routing Logic: Identification of alternative parking options within 5 competitors with respect to distance

Price Comparison: Continuous monitoring of competitive pricing for optimization opportunities

Automated Alerts: Generation of actionable recommendations for traffic distribution

# 5. Visualization and Dashboard Layer
The system provides comprehensive real-time visualization:

Interactive Dashboard: Multi-panel dashboard with synchronized time-series charts

Comparison Visualization: Side-by-side price comparisons across multiple parking lots

Alert Indicators: Color-coded visual indicators for congestion and re-routing recommendations


# Logistics Performance Dashboard with Power BI

## Project Overview
This project showcases a logistics performance dashboard built using **Power BI**. The dashboard provides actionable insights into various aspects of logistics operations, including shipment performance, operational efficiency, environmental impact, and customer analysis. It leverages a synthetic dataset with 100,000 rows of data to simulate real-world scenarios.

---

## Key Features

### 1. Overview Dashboard
- Summarizes critical KPIs:
  - Total Shipments
  - Total Revenue
  - On-Time Delivery Rate
  - Average Freight Cost
- Visualizations include:
  - Revenue distribution by transportation mode.
  - Delivery performance trends over time.
  - Geographic distribution of shipments.

### 2. Operational Performance
- Tracks operational metrics:
  - Average Delivery Time
  - Total Distance Covered
  - Average Shipment Weight
- Highlights carrier performance and customer profitability.
- Visualizations include clustered bar charts, stacked bar charts, and carrier performance tables.

### 3. Environmental Impact
- Focuses on sustainability metrics:
  - Total CO2 Emissions
  - CO2 Emissions per Shipment
- Visualizations include:
  - Line chart for CO2 emissions trends.
  - Treemap of emissions by transportation mode.
  - Scatter chart comparing Freight Cost vs. CO2 Emissions.

### 4. Customer Analysis
- Provides detailed customer insights:
  - Top Customer by Revenue
  - Top Customer by Shipment Volume
- Visualizations include:
  - Revenue by Customer bar charts.
  - Shipment details in a matrix.
  - Monthly revenue trends by customer.

---

## Dataset Details
The dataset simulates logistics operations with the following fields:

| Column                 | Description                                                |
|------------------------|------------------------------------------------------------|
| Shipment ID            | Unique identifier for each shipment.                      |
| Customer Name          | Name of the customer.                                      |
| Origin                 | Shipment origin location.                                  |
| Destination            | Shipment destination location.                             |
| Shipment Date          | Date of shipment initiation.                               |
| Delivery Date          | Date of shipment delivery.                                 |
| Transportation Mode    | Mode of transport (Air, Sea, Road, Rail).                  |
| Shipment Weight (kg)   | Weight of the shipment.                                    |
| Distance (km)          | Distance covered in kilometers.                           |
| Freight Cost ($)       | Cost of shipment transportation.                           |
| Delivery Status        | Status of delivery (On Time, Delayed, In Transit).         |
| Carrier Name           | Name of the shipping carrier.                              |
| CO2 Emissions (kg)     | CO2 emissions associated with the shipment.                |
| Revenue ($)            | Revenue generated from the shipment.                       |

---

## DAX Measures
The following DAX measures are used to calculate key metrics:

### Total Revenue
```DAX
Total Revenue = SUM('Shipments'[Revenue ($)])
```

### On-Time Delivery Rate
```DAX
On-Time Delivery Rate = 
DIVIDE(
    CALCULATE(COUNTROWS('Shipments'), 'Shipments'[Delivery Status] = "On Time"),
    COUNTROWS('Shipments'),
    0
)
```

### Average Freight Cost
```DAX
Average Freight Cost = AVERAGE('Shipments'[Freight Cost ($)])
```

### Total CO2 Emissions
```DAX
Total CO2 Emissions (kg) = SUM('Shipments'[CO2 Emissions (kg)])
```

### Top Customer by Revenue
```DAX
Top Customer by Revenue = 
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            'Shipments',
            'Shipments'[Customer Name],
            "Total Revenue", SUM('Shipments'[Revenue ($)])
        ),
        [Total Revenue],
        DESC
    ),
    'Shipments'[Customer Name]
)
```

---

## Visualizations
This Power BI dashboard includes:
- **Cards**: Displaying KPIs like total shipments, revenue, and on-time delivery rate.
- **Bar Charts**: For revenue distribution, operational metrics, and customer analysis.
- **Line Charts**: Tracking trends over time, such as delivery performance and CO2 emissions.
- **Scatter Charts**: Comparing Freight Cost vs. CO2 Emissions.
- **Maps**: Visualizing shipment distribution geographically.
- **Matrices**: Detailed shipment data, including customer, origin, destination, and costs.

---

## Purpose
This project demonstrates the application of Power BI for analyzing and visualizing logistics data. It serves as a template for real-world use cases, enabling stakeholders to make data-driven decisions that:
- Optimize operations.
- Enhance sustainability.
- Improve customer relationships.

---

## Contributions
Contributions are welcome! Feel free to open an issue or submit a pull request to improve this project.

---


## Acknowledgments
- This project is inspired by real-world logistics challenges and the need for actionable insights using data visualization tools like Power BI.

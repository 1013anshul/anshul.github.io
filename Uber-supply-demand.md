[⏪ Back](./)

# SOLVED - Uber Supply-Demand Gap

## Uber Supply-Demand Gap Analysis: Identifying Challenges & Proposing Solutions

### Introduction
This data science endeavor focuses on analyzing Uber's supply-demand gap, a critical concern 
impacting its service efficacy. The dataset chosen for this study provides deep insights through its six key columns.

#### Dataset Overview
- **Request.id**: A unique identifier for each request.
- **Pickup.point**: Location where the ride request was generated.
- **Driver.id**: Identifier for the driver assigned to the request.
- **Status**: Indicates the status of the request (e.g., completed, canceled).
- **Request.timestamp**: Time when the request was made.
- **Drop.timestamp**: Time when the request was completed.

### Data Cleaning and Manipulation
Before diving into the analysis, it's crucial to ensure the dataset's quality and integrity. We addressed the following:

#### Data Inconsistencies
- Converted the 'Request timestamp' from an object to a datetime format for ease of analysis.
- Ensured consistency in date separators by converting all "/" and "-" to a single format.

### Trends Analysis
Upon analysis, it was observed that the pattern of requests is quite interesting, with 
high volumes during morning and evening rush hours. A significant number of trips are 
being **canceled in the early morning** hours and a large number of **no cars available** during the evening rush hours.

![2](./Assets/2.png)

### Time Binning
To better understand the flow of requests throughout the day, time was segmented into:
- **Pre_Morning**: 12 AM – 5 AM
- **Morning_Rush**: 5 AM – 10 AM
- **Day_Time**: 10 AM – 5 PM
- **Evening_Rush**: 5 PM – 10 PM


Post-segmentation, a clearer image of the supply-demand challenge emerged. Two bars, one green and one orange, 
were particularly prominent. These bars are indicative of the challenges faced during the Evening and Morning rush hours.

![3](./Assets/3.png)

Looking at the status of the trips by pickup during the **morning rush** tells us the majority of **canceled** trips are from the city to the airport.

![4](./Assets/4.png)

Looking at the status of the trips by pickup during the evening rush tells us the majority of no cars available are from the airport to the city.

![5](./Assets/5.png)

Key trends observed from binning:
- Majority of **canceled** trips during the morning rush are from the city to the airport.
- Majority of **no cars available** during the evening rush are from the airport to the city.

### Key Findings
- High volume of morning requests from the city.
- High volume of evening requests from the airport.

### Problem Identification
- **Morning Rush**: 50% of city trips were canceled.
- **Evening Rush**: Car unavailability affected 70% of airport trips.

### 🎯 Recommendations
#### Morning Rush Solutions
- **Incentivize Drivers**: Bonuses for each completed city-to-airport trip.
- **Gas Mileage Compensation**: Cover drivers' gas mileage for empty returns.
- **Boost Airport Demand**: Marketing efforts and price cuts for airport passengers.

#### Evening Rush Solutions
- **Driver Bonuses**: Incentives for airport trips during evening rush.
- **Compensate Empty Trips**: Pay drivers for passenger-less trips to the airport.
- **Ride Pooling**: Fewer cars serving more passengers, optimizing supply.

[⏪ Back](./)
